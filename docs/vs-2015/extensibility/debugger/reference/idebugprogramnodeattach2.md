---
title: IDebugProgramNodeAttach2 |Microsoft Docs
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
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ef3bedd5b5d501e6c0a60ef6958a8a3745b86865
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537682"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugProgramNodeAttach2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramnodeattach2)します。  
  
プログラム ノードが関連付けられているプログラムにアタッチしようとすると、通知を許可します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは実装するクラスと同じクラスの実装、 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)アタッチ操作の通知を受信するために、アタッチ操作をキャンセルする機会を提供するインターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスを呼び出すことによって取得、`QueryInterface`メソッドで、 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)オブジェクト。 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)メソッドは、前に呼び出す必要があります、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)メソッドは、[プログラム] ノードをアタッチ プロセスを停止できるようにします。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|関連付けられているプログラムにアタッチするか、アタッチ プロセスの遅延、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)メソッド。|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスは非推奨に代わる[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)メソッド。 すべてのデバッグ エンジンが読み込まれて常に、`CoCreateInstance`関数をデバッグ中のプログラムのアドレス空間の外部オブジェクトのインスタンスは、します。  
  
 以前の実装の場合、`IDebugProgramNode2::Attach_V7`メソッドは単に設定された、`GUID`のデバッグ中のプログラムをのみ、 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)メソッドを実装する必要があります。  
  
 以前の実装の場合、`IDebugProgramNode2::Attach_V7`メソッドは、指定されたコールバック インターフェイスを使用し、その機能は、の実装に移動する必要があります、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)メソッドと`IDebugProgramNodeAttach2`インターフェイスでは不要実装する必要があります。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)

