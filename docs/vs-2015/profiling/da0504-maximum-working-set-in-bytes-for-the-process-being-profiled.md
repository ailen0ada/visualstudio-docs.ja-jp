---
title: 'DA0504: プロセスのワーキング セット最大バイト数がプロファイリングされています | Microsoft Docs'
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
- vs.performance.DA0504
- vs.performance.504
- vs.performance.rules.DA0504
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 554db9edb121b1d0c72eb7c78a10e869b921e0c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539501"
---
# <a name="da0504-maximum-working-set-in-bytes-for-the-process-being-profiled"></a>DA0504: プロセスのワーキング セット最大バイト数がプロファイリングされています
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[da 0504: プロセスのプロファイリング対象のバイトで最大ワーキング セット](https://docs.microsoft.com/visualstudio/profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled)。  
  
規則 Id |DA 0504 |  
|カテゴリ |リソースの管理 |  
|プロファイル方法 |すべて |  
|メッセージ |この情報がについてのみ収集されます。 Process Working Set カウンターは、プロファイリングを行っているプロセスによる物理メモリの使用量を測定します。 報告される値は、全測定期間を通じて観察された最大値 |。  
|規則の種類 |情報 |  
  
 サンプリング、.NET メモリ、またはリソース競合メソッドを使用してプロファイリングを行うときは、この規則を呼び出すためのサンプルを少なくとも 10 個収集する必要があります。  
  
## <a name="rule-description"></a>規則の説明  
 このメッセージにより、プロセスが現在使用している物理メモリの最大容量がバイト単位で報告されます。 プロセスのワーキング セットは、物理メモリに現在常駐しているプロセス アドレス空間のページを表します。 この規則は、プロファイリングがアクティブな状態にあったときの、プロセスのワーキング セットの最大値を報告します。  
  
 報告された値には、プロセスが参照する共有メモリ セグメントの常駐ページが含まれます。 プロセスが参照する共有 DLL は、測定対象の共有メモリ セグメントに含まれます。 プロセスのワーキング セットの値は、プロセスによって割り当てられた仮想メモリ量よりも大きくなる場合があります。これは、共有メモリ セグメントが存在するためです。  
  
 プロセスのワーキング セットのサイズには、プロセスが現在使用している仮想メモリ量が反映されます。 これは、アプリケーションの実行に使用できる物理メモリ (または RAM) の量と、実行中の他のプロセスによる物理メモリの競合の影響も受けます。 プロセスのワーキング セットの詳細については、MSDN の Windows のメモリ管理のドキュメントの「[Working Set](http://go.microsoft.com/fwlink/?LinkId=177830)」 (ワーキング セット) を参照してください。  
  
## <a name="how-to-use-rule-data"></a>規則データの使用方法  
 この規則は、測定データを Windows パフォーマンス モニター機能から収集し、情報提供のみの目的でこのデータを報告します。 これを使用して、特定のプログラムの異なるバージョンやビルドを比較したり、さまざまなテスト シナリオにおけるアプリケーションのパフォーマンスを確認したりします。  
  
 [エラー一覧] ウィンドウに表示されたメッセージをダブルクリックして、プロファイル データの[ [マーク] ビュー](../profiling/marks-view.md)に移動します。 **Process\Working Set** カウンター列と **Memory\Pages/sec** カウンター列を探します。 次に、**Process\Working Set** の最大値を探して **Memory\Pages/sec** の値と比較します。 多くの場合 (特に、コンピューターがメモリの制約を受けている場合)、ワーキング セットの最大値は、ページング入出力アクティビティ数が減少する間隔に影響されます。



