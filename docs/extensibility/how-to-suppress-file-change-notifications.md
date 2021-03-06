---
title: '方法: ファイル変更通知を抑制する |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 28f4c2e2929fecb29da6ddeecdd6cede6b8fa4d7
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497964"
---
# <a name="how-to-suppress-file-change-notifications"></a>方法: ファイル変更通知を抑制します。
メッセージ テキスト バッファーを表す物理ファイルが変更されたとき ダイアログ ボックスを表示します**次のものに変更を保存しますか?** これは、ファイル変更通知と呼ばれます。 多くの変更が使用する場合、ファイルに、ただし、このダイアログ ボックスを繰り返し表示することがすぐに面倒な場合。  
  
 プログラムで、次の手順を使用してこのダイアログ ボックスを抑制することができます。 ダイアログ ボックスを抑制することで再読み込みできますファイルをすぐにたびに、変更を保存するユーザーに確認する必要はありません。  
  
## <a name="to-suppress-file-change-notification"></a>ファイル変更通知を抑制するには  
  
1.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>テキスト バッファー オブジェクトは、開いているファイルに関連付けを調べます。  
  
2.  直接、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>オブジェクトが監視しているメモリを無視するファイルの変更を取得して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>からインターフェイス、 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> (ドキュメント データ) オブジェクト、および実装し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A>メソッドを`fIgnore`パラメーター設定`true`します。  
  
3.  メソッドを呼び出して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>インターフェイスでメモリを更新する<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>(ときに、フィールドは、コンポーネントに追加されます) などのファイルの変更を持つオブジェクト。  
  
4.  保留中の編集が進行中のユーザーがあります。 いずれかを考慮せず、変更をディスク上のファイルを更新します。  
  
     これにより、送信すると、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>ファイルの監視を再開するオブジェクトの変更通知、メモリ内のテキスト バッファーには、生成した変更が反映されます。 また、メモリ内のテキスト バッファーには、他のすべての保留中の編集が反映されます。 ディスク上のファイルは、自分で生成された最新のコードを反映し、ユーザーが編集したコードで以前に、ユーザーによる変更を保存いずれかです。  
  
5.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A>に通知するメソッド、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>オブジェクトを設定して、ファイル変更通知の監視を再開する、`fIgnore`パラメーター`false`します。  
  
6.  ソース コード管理 (SCC) の場合と同様、ファイルにいくつかの変更を加える場合は、ファイル変更通知を一時的に中断するグローバル ファイル変更サービスを伝える必要があります。  
  
     たとえば、ファイルを再書き込みするタイムスタンプを変更して場合、書き換えおよびタイムスタンプの操作は、それぞれが別のファイルの変更イベントとしてカウントするため、ファイル変更の通知を中断する必要があります。 グローバル ファイルの変更通知を有効にする必要があります代わりに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A>メソッド。  
  
## <a name="example"></a>例  
 次のコード例では、ファイル変更通知を抑制する方法を示します。  
  
```cpp  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 ケースには、SCC の場合と同様、ファイルに複数の変更が含まれている場合は、アラート、ドキュメント データ ファイルの変更の監視を再開する前にグローバル ファイル変更通知を再開する必要があります。