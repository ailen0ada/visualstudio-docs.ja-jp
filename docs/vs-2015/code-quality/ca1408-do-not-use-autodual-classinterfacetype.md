---
title: 'Ca 1408: AutoDual ClassInterfaceType を使用 |Microsoft Docs'
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
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 45b9e3b9e562b9b3303d170226845a97af2a0d5a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589268"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: AutoDual ClassInterfaceType を使用しないでください
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 1408: AutoDual ClassInterfaceType を使用](https://docs.microsoft.com/visualstudio/code-quality/ca1408-do-not-use-autodual-classinterfacetype)します。

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 コンポーネント オブジェクト モデル (COM) 参照できる型が付いて、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>属性に設定、 `AutoDual` @property<xref:System.Runtime.InteropServices.ClassInterfaceType>します。

## <a name="rule-description"></a>規則の説明
 デュアル インターフェイスを使用する型を使用することで、クライアントを特定のインターフェイス レイアウトに対応付けることができます。 将来のバージョンで、この型またはその基本型のレイアウトに変更が加えられると、インターフェイスに対応付けられた COM クライアントが切り離されます。 既定では場合、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>属性が指定されていない、ディスパッチ専用インターフェイスが使用されます。

 それ以外の場合にマークされている場合は、すべてのパブリックの非ジェネリック型の COM; から参照できるものすべての非パブリックとジェネリック型が COM に表示されません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を解決するには、値を変更、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>属性を`None`の値<xref:System.Runtime.InteropServices.ClassInterfaceType>し、明示的にインターフェイスを定義します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 特定の種類とその基本型のレイアウトが、今後のバージョンで変更されないことがない限り、この規則による警告を抑制しないでください。

## <a name="example"></a>例
 次の例では、規則に違反すると、明示的なインターフェイスを使用して、クラスの再宣言するクラスを示します。

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/cs/FxCop.Interoperability.AutoDual.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/vb/FxCop.Interoperability.AutoDual.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1403: Auto 配置の型を COM 参照可能にすることはできません](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412: ComSource インターフェイスを IDispatch として設定します](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>関連項目
 [クラス インターフェイスの概要](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)[相互運用のための .NET 型を修飾](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)[アンマネージ コードと相互運用](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



