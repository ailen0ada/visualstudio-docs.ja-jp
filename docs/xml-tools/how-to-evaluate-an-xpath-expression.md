---
title: '方法 : XPath 式を評価する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02492f2e1760df3ce5cd6751808303bae75577e2
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2018
ms.locfileid: "34549052"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>方法 : XPath 式を評価する

含む XPath 式を評価することができます、 **クイック ウォッチ**  ダイアログ ボックス。 XPath 式は、W3C XPath 1.0 勧告に沿って有効である必要があります。 現在の XSLT コンテキスト-は、`self::node()`内のノード、 **[ローカル]** ウィンドウ: XPath 式の評価コンテキストを提供します。

 XPath 式を評価する際にどの機能がサポートされるかについて次の一覧に示します。

-   組み込みの XPath 関数はサポートされます。

-   組み込みの XSLT 関数はサポートされません。

-   ユーザー定義関数はサポートされません。

> [!NOTE]
> 次の手順を使用して、 *belowAvg.xsl*と*books.xml*ファイルから、[チュートリアル: XSLT スタイル シートのデバッグ](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)トピックです。

## <a name="to-evaluate-an-xpath-expression"></a>XPath 式を評価するには

1.  `xsl:if` 開始タグにブレークポイントを挿入します。

2.  クリックして、 **XSL のデバッグ**XML エディター ツールバーのボタンをクリックします。

     デバッガーが起動され、`xsl:if` タグで実行が中断されます。

3.  右クリックし  **クイック ウォッチ**です。

     **クイック ウォッチ**  ダイアログ ボックスが表示されます。

4.  入力`./price/text()`で、**式**のフィールド、 **クイック ウォッチ**  ダイアログ ボックスをクリック**再評価**です。

     現在の book ノードの価格が表示されます、**値**ボックス。

5.  XPath 式を変更して`./price/text() < $bookAverage` をクリック**再評価**です。

     **値**ボックスに表示する XPath 式の評価結果`true`です。

## <a name="see-also"></a>関連項目

- [XSLT のデバッグ](../xml-tools/debugging-xslt.md)