---
title: IDebugModuleLoadEvent2::GetModule |Microsoft Docs
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
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dcf01689b6ab133ee52870ff65293ab31e98855e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533241"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugModuleLoadEvent2::GetModule](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmoduleloadevent2-getmodule)します。  
  
取得されているモジュール読み込みまたはアンロードします。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```csharp  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pModule`  
 [out]返します、 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)読み込みまたはアンロードされているモジュールを表すオブジェクト。  
  
 `pbstrDebugMessage`  
 [入力、出力]このイベントを説明する省略可能なメッセージが返されます。 このパラメーターが null 値の場合は、メッセージは要求されません。  
  
 `pbLoad`  
 [入力、出力]0 以外の場合 (`TRUE`) モジュールが読み込みと 0 の場合 (`FALSE`) 場合は、モジュールをアンロードしています。 このパラメーターが null 値の場合は、状態は要求されません。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)

