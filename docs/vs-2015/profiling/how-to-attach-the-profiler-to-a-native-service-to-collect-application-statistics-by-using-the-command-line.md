---
title: '方法: コマンド ラインを使用してプロファイラーをネイティブ サービスにアタッチし、アプリケーションの統計情報を収集する | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1ff5fd1093faf58e2f704c1e973c5726118f8fc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539415"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line"></a>方法: コマンド ラインを使用してプロファイラーをネイティブ サービスにアタッチし、アプリケーションの統計情報を収集する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: コマンドラインを使用して、Profiler をアプリケーションの統計の収集をネイティブ サービスにアタッチ](https://docs.microsoft.com/visualstudio/profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line)します。  
  
ここでは、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロファイリング ツールのコマンド ライン ツールを使用して、プロファイラーをネイティブ サービスにアタッチし、サンプリング メソッドによってパフォーマンスに関する統計情報を収集する方法について説明します。  
  
> [!NOTE]
>  Windows 8 および Windows Server 2012 の強化されたセキュリティ機能によって、Visual Studio プロファイラーがこれらのプラットフォームでデータを収集する方法に大幅な変更が必要になりました。 Windows ストア アプリにも新しい収集手法が必要です。 「[Windows 8 および Windows Server 2012 アプリケーションのパフォーマンス ツール](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)」を参照してください。  
  
> [!NOTE]
>  プロファイリング ツールのコマンド ライン ツールは、[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] インストール ディレクトリの \Team Tools\Performance Tools サブディレクトリにあります。 64 ビット コンピューター上では、64 ビット バージョンのツールと 32 ビット バージョンのツールの両方を使用できます。 プロファイラーのコマンド ライン ツールを使用するには、コマンド プロンプト ウィンドウの PATH 環境変数にツールのパスを追加するか、コマンド自体にそれを追加します。 詳細については、「[コマンド ライン ツールへのパスの指定](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)」をご覧ください。  
  
 プロファイラーをサービスにアタッチしている間はデータ コレクションを一時停止し、完了後に再開できます。  
  
 プロファイル セッションを終了するには、プロファイラーをサービスからデタッチし、プロファイラーを明示的に終了する必要があります。  
  
## <a name="starting-the-application-with-the-profiler"></a>プロファイラーによるアプリケーションの起動  
 プロファイラーをネイティブ サービスにアタッチするには、**VSPerfCmd.exe**[/start](../profiling/start.md) オプションおよび [/attach](../profiling/attach.md) オプションを使用して、プロファイラーを初期化し、ターゲット アプリケーションにアタッチします。 **/start** と **/attach**、およびそれぞれのオプションは、1 つのコマンド ラインで指定できます。 [/globaloff](../profiling/globalon-and-globaloff.md) オプションを追加して、対象アプリケーションの起動時にデータ収集を一時停止することもできます。 その後、[/globalon](../profiling/globalon-and-globaloff.md) を使用してデータの収集を開始できます。  
  
#### <a name="to-attach-the-profiler-to-a-native-service"></a>プロファイラーをネイティブ サービスにアタッチするには  
  
1.  起動の必要なサービスがあれば起動します。  
  
2.  コマンド プロンプト ウィンドウを開きます。  
  
3.  プロファイラーを起動します。 型:  
  
     **VSPerfCmd /start:sample**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  
  
    -   **/start:sample** オプションによってプロファイラーが初期化されます。  
  
    -   **/start** を使用するには、**/output:**`OutputFile` オプションを指定する必要があります。 `OutputFile` には、プロファイル データ (.vsp) ファイルの名前と場所を指定します。  
  
     **/start:sample** オプションを使用する場合は、次のうちいずれかのオプションを指定できます。  
  
    > [!NOTE]
    >  **/user** オプションと **/crosssession** オプションは、通常、サービスで必要です。  
  
    |オプション|説明|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|プロファイリングされたプロセスを所有するアカウントのドメインおよびユーザー名を指定します。 このオプションは、ログオンしているユーザーとは別のユーザーがプロセスを実行している場合にのみ指定する必要があります。 プロセスの所有者は、Windows タスク マネージャーの [プロセス] タブの [ユーザー名] 列に表示されます。|  
    |[/crosssession](../profiling/crosssession.md)|他のセッションにおけるプロセスのプロファイリングを有効にします。 このオプションは、アプリケーションが別のセッションで実行されている場合に必要です。 セッション ID は、Windows タスク マネージャーの [プロセス] タブの [セッション ID] 列に表示されます。 **/crosssession** の省略形として、**/CS** を指定することができます。|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|プロファイリング実行中に収集する Windows パフォーマンス カウンターを指定します。|  
    |[/automark](../profiling/automark.md) **:** `Interval`|**/wincounter** との組み合わせでのみ使用します。 Windows パフォーマンス カウンター コレクション イベントの間隔をミリ秒単位で指定します。 既定値は 500 ミリ秒です。|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|プロファイリング実行中に収集する ETW (Event Tracing for Windows) イベントを指定します。 ETW イベントは独立した (.etl) ファイルに収集されます。|  
  
4.  プロファイラーをサービスにアタッチします。 型:  
  
     **VSPerfCmd /attach:** `PID` [`Sample Event`]  
  
     `PID` には、対象アプリケーションのプロセス ID を指定します。 Windows タスク マネージャーで、実行中のすべてのプロセスのプロセス ID を参照できます。  
  
     既定では、パフォーマンス データはプロセッサのクロック サイクル数 10,000,000 (停止なし) ごとにサンプリングされます。 このため、1 GHz のプロセッサでは 10 秒ごとに約 1 回です。 次のオプションのいずれかを指定すると、クロック サイクルの間隔の変更や、別のサンプリング イベントの指定ができます。  
  
    |サンプリング イベント|説明|  
    |------------------|-----------------|  
    |[/timer](../profiling/timer.md) **:** `Interval`|サンプリングの間隔を、`Interval` で指定された停止なしのクロック サイクル数に変更します。|  
    |[/pf](../profiling/pf.md)[**:**`Interval`]|サンプリング イベントをページ フォールトに変更します。 `Interval` を指定した場合は、サンプル間のページ フォールト数が設定されます。 既定値は 10 です。|  
    |[/sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|サンプリング イベントを、プロセスからオペレーティング システムのカーネルへのシステム コール (syscall) に変更します。 `Interval` を指定した場合は、サンプル間の呼び出し回数が設定されます。 既定値は 10 です。|  
    |[/counter](../profiling/counter.md) **:** `Config`|サンプリング イベントと間隔を、プロセッサのパフォーマンス カウンターと、`Config` で指定した間隔に、それぞれ変更します。|  
  
## <a name="controlling-data-collection"></a>データ コレクションの制御  
 対象アプリケーションの実行中に、**VSPerfCmd.exe** のオプションを使用して、プロファイラー データ ファイルへのデータの書き込みを開始および停止できます。 データ コレクションを制御することにより、アプリケーションの起動や終了など、プログラム実行の特定の部分についてのデータ コレクションを行うことができます。  
  
#### <a name="to-start-and-stop-data-collection"></a>データ コレクションを開始および停止するには  
  
-   次に示す **VSPerfCmd** のオプションの組み合わせにより、データ収集を開始および停止します。 個別のコマンド ラインで各オプションを指定します。 データ収集のオンとオフは複数回切り替えることができます。  
  
    |オプション|説明|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|すべてのプロセスのデータ収集を開始 (**/globalon**) または停止 (**/globaloff**) します。|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|プロセス ID (`PID`) で指定されたプロセスのデータ収集を開始 (**/processon**) または停止 (**/processoff**) します。|  
    |**/attach:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/attach** は、プロセス ID またはプロセス名で指定したプロセスのデータ収集を開始します。 **/detach** は、指定されたプロセスのデータ収集を停止します。プロセスが指定されていない場合は、すべてのプロセスのデータ収集を停止します。|  
  
## <a name="ending-the-profiling-session"></a>プロファイル セッションの終了  
 プロファイル セッションを終了するには、プロファイラーをサービスからデタッチし、明示的に終了する必要があります。 サービスを停止するか **VSPerfCmd /detach** オプションを呼び出すことによって、サンプリング メソッドでプロファイリングが実行されているネイティブ サービスをデタッチできます。 次に、**VSPerfCmd** [/shutdown](../profiling/shutdown.md) オプションを呼び出して、プロファイラーをオフにし、プロファイル データ ファイルを閉じます。  
  
#### <a name="to-end-a-profiling-session"></a>プロファイル セッションを終了するには  
  
1.  対象アプリケーションからプロファイラーをデタッチするには、次のいずれかの操作を行います。  
  
    -   サービスを停止します。  
  
         - または -  
  
    -   **VSPerfCmd /detach** と入力します  
  
2.  プロファイラーをシャットダウンします。 型:  
  
     **VSPerfCmd /shutdown**  
  
## <a name="see-also"></a>関連項目  
 [サービスのプロファイリング](../profiling/command-line-profiling-of-services.md)   
 [サンプリング メソッドのデータ ビュー](../profiling/profiler-sampling-method-data-views.md)



