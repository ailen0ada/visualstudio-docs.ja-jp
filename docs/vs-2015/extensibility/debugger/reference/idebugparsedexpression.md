---
title: IDebugParsedExpression |Microsoft Docs
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
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fac7ae05352317b9e53bced531f13981b02220a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534508"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugParsedExpression](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugparsedexpression)します。  
  
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスは、すぐに評価できる解析された式を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugParsedExpression : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーターでは、評価の準備が整った解析された式を表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出し[解析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)このインターフェイスを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugParsedExpression`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|解析された式を評価します。|  
  
## <a name="remarks"></a>Remarks  
 呼び出す、呼び出し元の式を評価する準備ができたら[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)を返す、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)評価の結果を格納しています。 この 2 つの部分には、評価、評価、により、解析された式を複数回評価し、解析、式を解析の時間のかかるプロセスをバイパスするアプローチが。  
  
## <a name="requirements"></a>要件  
 ヘッダー: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [解析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

