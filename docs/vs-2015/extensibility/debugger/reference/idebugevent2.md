---
title: IDebugEvent2 |Microsoft Docs
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
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7fc387733e1472afe5f21f5e0638374ebda9f677
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548992"
---
# <a name="idebugevent2"></a>IDebugEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugevent2)します。  
  
このインターフェイスは、ブレークポイントで停止するなどの重要なデバッグ情報とデバッグ メッセージなどの致命的でない情報の両方の通信に使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) とカスタム ポート サプライヤーは、他のすべてのイベント インターフェイスと同じオブジェクトでこのインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 インターフェイスに指定された ID (IID) 引数を使用して[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)または[イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)、セッション デバッグ マネージャー (SDM) を呼び出す[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)上、`IDebugEvent2`インターフェイスを取得するには適切なイベントのインターフェイスです。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugEvent2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|このデバッグ イベントの属性を取得します。|  
  
## <a name="remarks"></a>Remarks  
 特定のイベント インターフェイスなど[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)IDebugEvent2 インターフェイスから派生していないと同じオブジェクトに個別のインターフェイスとして実装が代わりに、`IDebugEvent2`します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

