---
title: 'Ca 1012: 抽象型はコンス トラクターがありません |Microsoft Docs'
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
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 692dfc0ad69cf4d71d82953e2cc9965733915dc6
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589665"
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012: 抽象型にはコンストラクターを含めません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 1012: 抽象型には、コンス トラクターはありません。](https://docs.microsoft.com/visualstudio/code-quality/ca1012-abstract-types-should-not-have-constructors)します。

|||
|-|-|
|TypeName|AbstractTypesShouldNotHaveConstructors|
|CheckId|CA1012|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 パブリック型は abstract であり、パブリック コンス トラクターがあります。

## <a name="rule-description"></a>規則の説明
 抽象型上のコンストラクターは、派生型からのみ呼び出すことができます。 パブリック コンストラクターで型のインスタンスが作成され、抽象型のインスタンスは自分で作成できないため、パブリック コンストラクターが含まれる抽象型のデザインは不適切になります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するのには、コンス トラクターを保護するか、または抽象型を宣言しないでください。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 抽象型では、パブリック コンス トラクターがあります。

## <a name="example"></a>例
 次の例には、この規則に違反する抽象型が含まれています。

 [!code-csharp[FxCop.Design.AbstractTypeBad#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeBad/cs/FxCop.Design.AbstractTypeBad.cs#1)]
 [!code-vb[FxCop.Design.AbstractTypeBad#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeBad/vb/FxCop.Design.AbstractTypeBad.vb#1)]

## <a name="example"></a>例
 次の例では、前の違反を修正からコンス トラクターのアクセシビリティを変更することで`public`に`protected`します。

 [!code-csharp[FxCop.Design.AbstractTypeGood#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeGood/cs/FxCop.Design.AbstractTypeGood.cs#1)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeGood/vb/FxCop.Design.AbstractTypeGood.vb#1)]



