---
title: IPropertyProxyEESide::ResolveAssemblyRef |Microsoft Docs
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
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a3d8b5b41f8503a24d2a6d2643a1cf4c0290624
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539215"
---
# <a name="ipropertyproxyeesideresolveassemblyref"></a>IPropertyProxyEESide::ResolveAssemblyRef
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IPropertyProxyEESide::ResolveAssemblyRef](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref)します。  
  
指定したマネージ アセンブリの参照の場所を決定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT ResolveAssemblyRef(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  assemLocation,  
   ASSEMBLYLOCRESOLUTION* alr  
);  
```  
  
```csharp  
int ResolveAssemblyRef(  
   ref string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     assemLocation,  
   out enum_ASSEMBLYLOCRESOLUTION alr  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `assemName`  
 [in]解決するのには、アセンブリの名前です。  
  
 `assemBytes`  
 [out]返します、 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)参照に関連付けられているアセンブリのバイト数を格納しているオブジェクト。  
  
 `assemPdb`  
 [out]返します、`IEEDataStorage`シンボルを含むオブジェクトがこの参照に関連付けられているデータを格納します。  
  
 `assemLocation`  
 [out]この参照のパスの場所を返します。  
  
 `alr`  
 [out]値を返します、 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)この参照のアセンブリの場所を示す列挙値。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 通常、このメソッドはカスタム式エバリュエーターでは実装されません。  
  
## <a name="see-also"></a>関連項目  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)

