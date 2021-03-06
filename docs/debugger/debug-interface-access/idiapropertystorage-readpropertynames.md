---
title: IDiaPropertyStorage::ReadPropertyNames |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a13ac0e3a1af8dc20fe63f832e7a19d7bf40c271
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465578"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
対応する文字列名を取得では、プロパティの識別子を指定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cpropid`  
 [in]プロパティ id の数`rgpropid`です。  
  
 `rgpropid`  
 [in]名前を取得する対象のプロパティ id の配列 (`PROPID`として WTypes.h で定義された、 `ULONG`)。  
  
 `rglpwstrName`  
 [入力、出力].指定したプロパティの id のプロパティ名の配列。 配列のプロパティ名の要求の数を保持するために事前に割り当てる必要があり、少なくともを保持できる必要があります`cpropid``BSTR`文字列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 返されるプロパティの名前を解放する必要があります (を呼び出して、`SysFreeString`関数) が不要になったときにします。  
  
## <a name="see-also"></a>関連項目  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)