---
title: Idiaframedata::get_program |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2c78c6f1c2c6e8368efd86dc3ffa03a021e46da3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459598"
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
レジスタの現在の関数呼び出しの前にセットの計算に使用されるプログラム文字列を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]プログラムの文字列を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 プログラムの文字列は、プロローグを確立するために解釈されるマクロのシーケンスです。 たとえば、一般的なスタック フレームを使用プログラム文字列`"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`です。 形式は、逆ポーランド表記法、演算子はオペランドは、次の場所です。 `T0` スタック上の一時変数を表します。 この例では、次の手順を実行します。  
  
1.  レジスタの内容を移動`ebp`に`T0`です。  
  
2.  追加`4`の値に`T0`アドレスが生成、そのアドレスから値を取得、レジスタに値を格納して`eip`です。  
  
3.  格納されているアドレスから値を取得`T0`レジスタに値を格納および`ebp`です。  
  
4.  追加`8`の値に`T0`レジスタに値を格納および`esp`です。  
  
 プログラムの文字列が、CPU と現在のスタック フレームで表される関数を設定する呼び出し規約に固有である注意してください。  
  
## <a name="see-also"></a>関連項目  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)