---
title: 'DA0014: ディスクへのアクティブなメモリのページングが非常に高率で発生しています。 | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DAMemoryBound
- vs.performance.DA0014
- vs.performance.14
- vs.performance.rules.DA0014
ms.assetid: a7fa3749-9191-437a-9331-9d917181e62f
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 158ccc60d356fd83a808ca1a6d74268e53adb4b1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548503"
---
# <a name="da0014-extremely-high-rates-of-paging-active-memory-to-disk"></a>DA0014: ディスクへのアクティブなメモリのページングが非常に高率で発生しています
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[DA0014: ディスクへのアクティブなメモリのページングが非常に高率](https://docs.microsoft.com/visualstudio/profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk)します。  
  
規則 Id |DA0014 |  
|カテゴリ |メモリとページング |  
|プロファイル方法 |すべて |  
|メッセージ |ディスクへのアクティブなメモリのページングが非常に高率が発生しています。 アプリケーションのメモリ バインドされた可能性があります |。  
|規則の種類 |警告 |  
  
 サンプリング、.NET メモリ、またはリソース競合メソッドを使用してプロファイリングを行うときは、この規則を呼び出すためのサンプルを少なくとも 25 個収集する必要があります。  
  
## <a name="cause"></a>原因  
 プロファイリングの実行中に収集されたシステム パフォーマンス データが、ディスクへのアクティブなメモリのページングがプロファイリング実行全体において非常に高率で発生していることを示しています。 通常、このレベルのページング率は、アプリケーションのパフォーマンスと応答速度に影響します。 アルゴリズムを修正してメモリの割り当てを減らすことを検討してください。 また、アプリケーションのメモリ要件も検討した方がよいでしょう。 よりメモリの多いコンピューターでプロファイリングを再度実行してください。  
  
## <a name="rule-description"></a>規則の説明  
 ディスクに対する過剰なページングは、物理メモリの不足が原因で発生する場合があります。 ページング ファイルが存在する物理ディスクの大部分がページング操作によって使用される場合、同じディスクのその他のアプリケーションのディスク操作の処理速度が遅くなる可能性があります。  
  
 通常、ページのディスクへの読み書きは一括で実行されます。 たとえば、1 秒あたりの出力ページ数は 1 秒あたりの書き込みページ数よりも大幅に大きくなることが一般的です。 これは、1 秒あたりの出力ページ数には、システム ファイルのキャッシュで変更されたデータ ページも含まれるためです。 ただし、どのプロセスがどういった理由で高いページング率の直接的な原因になっているのかを特定するのは、必ずしも容易ではありません。  
  
> [!NOTE]
>  この規則は、アクティブなメモリのページングが非常に高率に達した場合に適用されます。 ページングが高いレベルで発生しているが、非常に高くはない場合、代わりに、情報規則「[DA0017: ディスクへのアクティブなメモリのページングが高率で発生しています。](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)」が発生します。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 [エラー一覧] ウィンドウに表示されたメッセージをダブルクリックして、[[マーク](../profiling/marks-view.md)] ビューに移動します。 **Memory\Pages/sec** 列を探します。 ページングの入出力アクティビティのが他のフェーズよりも多い特定のプログラム実行フェーズがあるかどうかを確認します。  
  
 ロード テスト シナリオで ASP.NET アプリケーション用のプロファイル データを収集している場合は、追加の物理メモリ (または RAM) が構成されているコンピューターでもう一度ロード テストを実行してください。  
  
 アルゴリズムを修正し、String.Concat や String.Substring などのメモリ消費量の多い API の使用を控えることにより、メモリの割り当てを減らすことを検討してください。


