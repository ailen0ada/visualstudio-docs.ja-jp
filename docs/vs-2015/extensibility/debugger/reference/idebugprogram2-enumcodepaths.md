---
title: IDebugProgram2::EnumCodePaths |Microsoft Docs
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
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c2f18a95fb63b0db7ea5e4a3a34a663ac1a5ad6c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534645"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugProgram2::EnumCodePaths](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-enumcodepaths)します。  
  
ソース ファイル内の指定位置のコード パスの一覧を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```csharp  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszHint`  
 [in]内のカーソルの下の単語、**ソース**または**逆アセンブル**IDE で表示します。  
  
 `pStart`  
 [in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)コードの現在のコンテキストを表すオブジェクト。  
  
 `pFrame`  
 [in][IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)現在のブレークポイントに関連付けられているスタック フレームを表すオブジェクトします。  
  
 `fSource`  
 [in]0 以外の場合 (`TRUE`) の場合、**ソース**ビュー、または 0 (`FALSE`) の場合、**逆アセンブル**ビュー。  
  
 `ppEnum`  
 [out]返します、 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)コード パスの一覧を含むオブジェクト。  
  
 `ppSafety`  
 [out]返します、 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)がスキップされる場合は、選択したコード パスのブレークポイントとして設定する、追加のコード コンテキストを表すオブジェクトします。 これにショート サーキットのブール式の場合などです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 コード パスでは、メソッドまたはプログラムの実行の現在のポイントに呼び出された関数の名前について説明します。 コード パスの一覧は、コール スタックを表します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)

