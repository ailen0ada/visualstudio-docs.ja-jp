---
title: IDebugProgram3::ExecuteOnThread |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8aff643014da16ed9644573a77cb8444836d713d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31117063"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
デバッガーのプログラムを実行します。 どのスレッドで、ユーザーが表示プログラムを実行するときにデバッガーの情報を提供し、スレッドが返されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```csharp  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pThread`  
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 これには、デバッガーが停止後に実行を再開できます 3 つの異なる方法があります。  
  
-   実行します。 は、前の手順をキャンセルしに、次のブレークポイントまで実行します。  
  
-   手順: は、いずれかの古い手順をキャンセルし、新しい手順が完了するまで実行します。  
  
-   続行: を再度実行し、いずれかの古い手順のアクティブなままにします。  
  
 渡されるスレッド`ExecuteOnThread`をキャンセルする手順を決定する場合に便利です。 実行している実行スレッドがわからない場合は、すべてのステップをキャンセルします。 スレッドの知識さえあれば、のみ、アクティブなスレッドでの手順をキャンセルする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [実行します。](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)