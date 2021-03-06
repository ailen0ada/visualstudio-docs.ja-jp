---
title: '方法: WPF トレース情報を表示 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07cdebcc636f768c7caf2437af55f20283db7b6c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539914"
---
# <a name="how-to-display-wpf-trace-information"></a>方法: WPF トレース情報を表示する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: WPF トレース情報を表示](https://docs.microsoft.com/visualstudio/debugger/how-to-display-wpf-trace-information)します。  
  
[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] WPF アプリケーションからデバッグ トレース情報を受信できでその情報を表示、**出力**ウィンドウ。 デバッグ トレース情報を表示するには、WPF トレースを有効にする必要があります。  
  
 WPF トレースは、App.Config ファイルで、または <xref:System.Diagnostics.PresentationTraceSources> クラスを使用してプログラムによって有効にすることができます。 使用して簡単に WPF トレースを有効にするは、**オプション**ウィンドウ。 Web アプリケーション用の WPF トレースはサポートされていません。  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>WPF トレース情報を有効にする、またはカスタマイズするには  
  
1.  **[ツール]** メニューの **[オプション]** を選択します。  
  
2.  **オプション**ダイアログ ボックスで、左側にあるボックスで、開く、**デバッグ**ノード。  
  
3.  [**デバッグ**、] をクリックして**出力ウィンドウ**します。  
  
4.  **出力の全般設定**、**すべてのデバッグ出力**します。  
  
5.  右側のボックスで、検索**WPF トレース設定**します。  
  
6.  開く、 **WPF トレース設定**ノード。  
  
7.  **WPF トレース設定**、有効に設定のカテゴリをクリックします (たとえば、**データ バインディングの**)。  
  
     ドロップダウン リスト コントロールは [設定] 列隣に表示されます**データ バインディングの**クリックしたカテゴリまたはします。  
  
8.  ドロップダウン リストをクリックし、表示するトレース情報の種類を選択:**すべて**、**重大**、**エラー**、**警告**、 **情報**、**詳細**、または**ActivityTracing**します。  
  
     **重要な**重大なイベントのみの追跡を有効にします。  
  
     **エラー**重大なエラー イベントの追跡を有効にします。  
  
     **警告**重大、エラーのトレースおよび警告イベントを使用します。  
  
     **情報**重大、エラー、警告、および情報イベントの追跡を有効にします。  
  
     **詳細な**重大、エラー、警告、情報、および Verbose のイベントの追跡を有効にします。  
  
     **ActivityTracing**停止、開始、中断、転送、および Resume イベントの追跡を有効にします。  
  
     これらのトレース情報レベルが持つ意味の詳細については、「<xref:System.Diagnostics.SourceLevels>」を参照してください。  
  
9. **[OK]** をクリックします。  
  
### <a name="to-disable-wpf-trace-information"></a>WPF トレース情報を無効にするには  
  
1.  **[ツール]** メニューの **[オプション]** を選択します。  
  
2.  **オプション**ダイアログ ボックスで、左側にあるボックスで、開く、**デバッグ**ノード。  
  
3.  [**デバッグ**、] をクリックして**出力ウィンドウ**します。  
  
4.  右側のボックスで、検索**WPF トレース設定**します。  
  
5.  開く、 **WPF トレース設定**ノード。  
  
6.  **WPF トレース設定**、有効に設定のカテゴリをクリックします (たとえば、**データ バインディングの**)。  
  
     ドロップダウン リスト コントロールは [設定] 列隣に表示されます**データ バインディングの**クリックしたカテゴリまたはします。  
  
7.  ドロップダウン リストをクリックし、選択**オフ**します。  
  
8.  **[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [WPF のデバッグ](../debugger/debugging-wpf.md)



