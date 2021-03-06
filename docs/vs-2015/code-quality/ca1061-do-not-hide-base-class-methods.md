---
title: 'Ca 1061: 基本クラスのメソッドを隠ぺいしない |Microsoft Docs'
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
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f018abbb864533e5c9d7b598638a4006a69ab2f3
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589136"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: 基本クラス メソッドを非表示にしません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 1061: 基本クラスのメソッドを隠ぺいしない](https://docs.microsoft.com/visualstudio/code-quality/ca1061-do-not-hide-base-class-methods)します。

|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 派生型は、基本メソッドのいずれかと同じ数のパラメーターと同じ名前のメソッドを宣言します。1 つまたは複数のパラメーターはベース メソッドの対応するパラメーターの基本型です。残りのパラメーターは、基本メソッドの対応するパラメーターと同じ型であります。

## <a name="rule-description"></a>規則の説明
 派生メソッドのパラメーター シグネチャより弱い派生基底メソッドのパラメーター シグネチャ内の対応する型よりも型のみが異なる場合に、派生型で同じ名前のメソッドで基本データ型のメソッドは表示されません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則の違反を修正するには、削除、メソッドの名前を変更またはメソッドは基本メソッドを隠ぺいしないように、パラメーターのシグネチャを変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、規則に違反するメソッドを示します。

 [!code-csharp[FxCop.Design.HideBaseMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.HideBaseMethod/cs/FxCop.Design.HideBaseMethod.cs#1)]



