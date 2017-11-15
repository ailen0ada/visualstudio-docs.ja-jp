---
title: "エディターの動作"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 894bcbe66bd071bff1a6d904759f468b519da0f2
ms.contentlocale: ja-jp
ms.lasthandoff: 08/11/2017

---

# <a name="editor-behavior"></a>エディターの動作

入力時にコードの書式が設定されるようにエディターの動作を設定することができます。 これらのアクションは、**[Visual Studio] > [ユーザー設定] > [テキスト エディター] > [動作]** で設定します。ここでは、よく使用される機能の一部について説明します。

![エディターの [動作] オプション](media/source-editor-image9.png)

*  新しいクラス、メソッド、またはプロパティを作成するときに、対応する右波かっこをコードに自動的に追加することができます。 このオプションをオンにして `{` と入力すると、`}` が自動的に追加されます。
* セミコロンや波かっこなどの文字列を入力すると、実行時のコード書式設定がトリガーされ、設定されている書式設定が列挙されます。
* また、保存時にファイルの書式を選択することもできます。この機能を利用すると、好きなようにコードを作成し、既存のユーザー設定に従って IDE で自動的にコードの書式を設定することができます。
* [インデント] は、[なし]、[自動]、または [スマート] に設定できます。 機能は次のとおりです。
 * なし - カレットを次行の行頭に設定します
 * 自動 - カレットを次行の同じカラムに設定します
 * スマート - コードに基づいて次行にインデントを設定します
* 単語を区切る動作は、OS によって異なります。ナビゲーションのために、テキスト エディターは単語の開始位置と終了位置を認識している必要があります。 書式は Unix または Windows に設定できます。

また、XML、CSS、HTML、および JSON の書式設定規則も設定できます。