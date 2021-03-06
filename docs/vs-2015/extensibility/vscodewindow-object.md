---
title: VSCodeWindow オブジェクト |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 17dd907bf041f37c4273548f0793b26625a34e3c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540074"
---
# <a name="vscodewindow-object"></a>VSCodeWindow オブジェクト
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[VSCodeWindow オブジェクト](https://docs.microsoft.com/visualstudio/extensibility/vscodewindow-object)します。  
  
コード ウィンドウは通常、1 つまたは複数のテキスト ビューを含めることができる特殊なドキュメント ウィンドウで、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>オブジェクト。  
  
 アーキテクチャ上、コード ウィンドウには、ウィンドウ フレーム内では、ドキュメント ウィンドウです。 機能的には、コード ウィンドウは、機能が追加されたドキュメント ウィンドウだけです。 マルチ ドキュメント インターフェイス (MDI) モードでは、コード ウィンドウは、MDI 子フレームです。 詳細については、次を参照してください。[レガシ API を使用してコードの Windows をカスタマイズする](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)します。  
  
 次の表に、インターフェイス、<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>オブジェクト。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|グローバル一意識別子 (GUID) を識別するサービスを検索する汎用アクセス メカニズムを提供します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|1 つまたは複数のコード ビューを含む複数ドキュメント インターフェイス (MDI) 子を表します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|ウィンドウ フレームを設定します。|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [図の編集](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)

