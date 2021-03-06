---
title: プロセス ビュー - 競合データ | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 411de842beb616cf4ed7c51d0458e8d7bce82690
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538980"
---
# <a name="process-view---contention-data"></a>プロセス ビュー - 競合データ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[プロセス ビュー - 競合データ](https://docs.microsoft.com/visualstudio/profiling/process-view-contention-data)します。  
  
プロセス ビューには、プロファイリング実行中に実行されたプロセスとスレッドの競合データが表示されます。  
  
 シンボルを使用できる場合、プロセスは名前で一覧表示されます。 シンボルを使用できない場合、プロセスはそのメモリ アドレス (16 進数形式) で一覧表示されます。 スレッドは、そのスレッドを作成したプロセスの子として一覧表示されます。  
  
 プロセス ビュー表内の列の値について、次の表で説明します。  
  
|Column|説明|  
|------------|-----------------|  
|**開始時刻**|プロファイリングの開始からプロセスまたはスレッドの開始までの時間 (ミリ秒) またはプロセッサ サイクル数。|  
|**ブロック時間**|プロセスまたはスレッドの関数が実行をブロックされた合計時間。|  
|**ブロック時間 %**|プロセスまたはスレッドの有効期間に対する、プロセスまたはスレッドの関数が実行をブロックされた時間の割合。|  
|**競合**|プロセスまたはスレッドの関数が実行をブロックされた回数。|  
|**競合 %**|プロセスまたはスレッドの競合となったすべての競合がプロファイリング実行に占める割合。|  
|**終了時刻**|プロファイリングの開始からプロセスまたはスレッドの終了までの時間 (ミリ秒) またはプロセッサ サイクル数。|  
|**ID**|システムによって生成される、プロセスまたはスレッドの ID。|  
|**有効期間**|プロセスまたはスレッドの開始から、プロセスまたはスレッドの終了、あるいはプロファイリングの終了までの時間 (ミリ秒) またはプロセッサ サイクル数。|  
|**Type**|行の種類 (プロセスまたはスレッド)。<br /><br /> **VSReport** コマンド ライン レポートでのみ有効です。 詳細については、「[VSPerfReport](../profiling/vsperfreport.md)」を参照してください。|  
|**Name**|プロセスまたはスレッドの名前。|  
|**ID (一意)**|プロファイラーによって生成される、プロセスまたはスレッドに固有の ID。|  
  
## <a name="see-also"></a>関連項目  
 [方法: レポート ビューの列をカスタマイズする](../profiling/how-to-customize-report-view-columns.md)   
 [プロセス ビュー](../profiling/process-view.md)



