---
title: 'Ca 2207: 値型の静的フィールドのインラインの初期化 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0f90e52ed5d80c9b3e97415e920d7d6f4f0972fc
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589585"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: 値型の静的フィールドのインラインを初期化します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 2207: 値型の静的フィールドのインラインを初期化](https://docs.microsoft.com/visualstudio/code-quality/ca2207-initialize-value-type-static-fields-inline)します。

|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 値型では、明示的な静的コンス トラクターを宣言します。

## <a name="rule-description"></a>規則の説明
 値型が宣言されている場合、すべての値型フィールドが 0 に設定され、すべての参照型フィールドに設定は、既定の初期化が行われる`null`(`Nothing` Visual Basic で)。 明示的な静的コンス トラクターを実行して、インスタンス コンス トラクターにのみ保証されます。 または、型の静的メンバーが呼び出されます。 そのため、インスタンス コンス トラクターを呼び出さずに、型が作成される場合、静的コンス トラクターを実行する保証されません。

 C# および Visual Basic のコンパイラが追加するかどうかは、すべての静的データが初期化されたインラインと明示的な静的コンス トラクターが宣言されていない、 `beforefieldinit` MSIL クラスの定義にフラグ。 コンパイラでは、静的な初期化コードを含むプライベート静的コンス トラクターも追加します。 このプライベート静的コンス トラクター、型の静的フィールドにアクセスする前に実行することが保証されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 解決するには、は、この規則違反は、宣言されていて、静的コンス トラクターを削除するときに、すべての静的データを初期化します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="related-rules"></a>関連規則
 [CA1810: 参照型の静的フィールドをインラインで初期化します](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)



