---
title: 'CA1815: equals および operator equals を値型でオーバーライドします'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7a7f6127789b219ba2378b95d7233b3383ed5c10
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550048"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: equals および operator equals を値型でオーバーライドします
|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 パブリック値型をオーバーライドしない<xref:System.Object.Equals%2A?displayProperty=fullName>、等値演算子 (= =) を実装していませんか。 このルールは、列挙型をチェックしません。

## <a name="rule-description"></a>規則の説明
 値型、継承した実装の<xref:System.Object.Equals%2A>リフレクション ライブラリを使用して、すべてのフィールドの内容を比較します。 Reflection は計算コストが高いため、場合によってはすべてのフィールドで等値性を比較する必要はありません。 ユーザーは比較または並べ替えるのインスタンスまたはハッシュ テーブル キーとして使用する場合、値型を実装する必要があります<xref:System.Object.Equals%2A>します。 お使いのプログラミング言語が演算子のオーバーロードに対応している場合、等値演算子と非等値演算子も実装してください。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、実装を提供<xref:System.Object.Equals%2A>します。 可能な場合は、等値演算子を実装します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 値型のインスタンスを相互に比較しない場合は、この規則による警告を抑制するのには安全です。

## <a name="example-of-a-violation"></a>違反の例

### <a name="description"></a>説明
 次の例では、この規則に違反する構造体 (値型) を示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]

## <a name="example-of-how-to-fix"></a>修正する方法の例

### <a name="description"></a>説明
 次の例では、オーバーライドすることで、前の違反を修正する<xref:System.ValueType.Equals%2A?displayProperty=fullName>と等値演算子の実装 (= =、! =)。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]

## <a name="related-rules"></a>関連するルール
 [CA2224: オーバーロードする演算子 equals で Equals をオーバーライドします](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226: 演算子は対称型オーバーロードを含まなければなりません](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>関連項目
 <xref:System.Object.Equals%2A?displayProperty=fullName>