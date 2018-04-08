---
title: Visual Studio での分散ロード テスト用のテスト設定の作成 | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- test settings, for distributed load tests
ms.assetid: b63d4b71-3b74-4872-b2d1-f0bd1a9a8544
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 38bcbe49850929105199cef360956f29f22a8d0c
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-create-a-test-setting-for-a-distributed-load-test"></a>方法: 配布されたロード テストのテスト設定を作成する

ロード テストの*テスト設定*を構成し、テスト エージェントとテスト コントローラーを使用して複数のコンピューターにテストを分散できるようにします。 また、*診断データ アダプター*を使用するようにテストの設定を構成することもできます。これは、収集するデータの種類や、Visual Studio からロード テストを実行するときにテスト コンピューターに及ぼす影響を指定します。

たとえば、ASP.NET プロファイラーの診断データ アダプターを使用して、コードのパフォーマンスの分析結果を収集できます。 また、診断データ アダプターを使用して、テスト コンピューター上での潜在的なボトルネックをシミュレートすることも、使用可能なシステム メモリを減らすこともできます。

Visual Studio のテスト設定はファイルに格納されます。 テスト設定では、各ロールについて次の情報が定義されます。

-   テスト対象のアプリケーションに必要なロール セット

-   テストの実行に使用するロール

-   各ロールに使用する診断データ アダプター

テストを実行するときに、特定のテストの実行に必要な内容に応じて、アクティブなテストの設定として使用するテストの設定を選択します。 テストの設定ファイルはソリューションの一部として格納されます。 ファイル名には、*.testsettings* という拡張子が付きます。

Web パフォーマンス テストとロード テストのプロジェクトをソリューションに追加すると、*Default.testsettings* ファイルが作成されます。 このファイルは、**[ソリューション項目]** フォルダーにあるソリューションに自動的に追加されます。 このファイルにより、診断データ アダプターを使用せずにローカルでテストが実行されます。 別の*.testsettings* ファイル追加するか、*.testsettings* を編集して、診断データ アダプターとテスト コントローラーを指定できます。

テスト コントローラーには、テストの設定の各ロールに使用できるエージェントが含まれます。 テスト コントローラーとテスト エージェントの詳細については、「[Visual Studio でのテスト コントローラーおよびテスト エージェントの管理](../test/manage-test-controllers-and-test-agents.md)」を参照してください。

Visual Studio から実行する予定のロード テストについて、ソリューションのテストの設定を作成または削除するには、次の手順を実行します。

## <a name="create-a-test-setting-for-a-distributed-load-test"></a>分散ロード テスト用のテスト設定の作成

### <a name="to-add-a-test-settings-for-a-distributed-load-test"></a>分散ロード テスト用のテストの設定を追加するには

1.  ソリューション エクスプローラーで、**[ソリューション項目]** を右クリックし、**[追加]** をポイントして、**[新しい項目]** を選択します。

     **[新しい項目の追加]** ダイアログ ボックスが表示されます。

2.  **[インストールされたテンプレート]** ペインで、**[テストの設定]** を選択します。

3.  (省略可能) **[ファイル名]** ボックスで、テストの設定ファイルの名前を変更します。

4.  **[追加]** をクリックします。

     ソリューション エクスプローラーで、**[ソリューション項目]** フォルダーの下に、新しいテストの設定ファイルが表示されます。

    > [!NOTE]
    > Visual Studio Enterprise に表示されるテスト設定のリストは、**[ソリューション項目]** フォルダー内にあるテスト設定ファイルのリストから作成されます。 たとえば、[ソリューション項目] フォルダー内のテストの設定ファイルは、**[テスト]** メニューの **[アクティブなテスト設定の選択]** オプションを使用するときに表示されます。 つまり、テスト設定ファイルをソリューション階層構造内の別の場所に移動すると、Visual Studio 統合開発環境ではテストの設定として使用できなくなります。

5.  **[テストの設定]** ダイアログ ボックスが表示されます。 **[全般]** ページが選択されています。

     このページで、テストの設定値を編集および保存できます。

    > [!NOTE]
    > 作成するそれぞれのテストの設定は、**[テスト]** メニューの **[アクティブなテスト設定の選択]** オプションおよび **[テスト設定の編集]** オプションに選択肢として一覧表示されます。

6.  **[名前]** ボックスに、テストの設定の名前を入力します。

7.  (省略可能) 他のチーム メンバーにテストの目的がわかるように、**[説明]** ボックスにテストの設定の説明を入力します。

8.  (省略可能) テストの実行の既定の名前付け方法を選択するには、**[既定の名前付けスキーム]** を選択します。 独自の名前付けスキームを定義するには、**[ユーザー定義されたスキーム]** を選び、**[プレフィックス テキスト]** にテキストを入力します。 テストの実行名に日付と時刻スタンプを追加するには、**[日付タイム スタンプを追加する]** を選択します。

9. **[ロール]** を選択します。

     **[ロール]** ページが表示されます。

     ![テスト設定のロール](../test/media/load_testtestrole.png "Load_TestTestRole")

10. テストをリモートで実行する、またはテストをリモートで実行してデータをリモートで収集するには、**[テストの実行メソッド]** ドロップダウン リストで **[リモート実行]** を選択します。

11. **[コントローラー]** ドロップダウン リストを使用して、テスト エージェントのテスト コントローラーを **[コントローラー]** から選択します。このコントローラーはテストの実行またはデータの収集に使用されます。

    > [!NOTE]
    > 初めてコントローラーを追加する場合、このボックスの一覧にコントローラーは表示されません。 このリストは、他のテスト設定でそれまでに指定したコントローラーによって設定されます。 コントローラーの名前 (たとえば **TestControllerMachine1**) をボックスに入力する必要があります。

12. テストの実行とデータの収集に使用するロールを追加するには、**[ロール]** で **[追加]** を選択します。

13. **[名前]** 列にロールの名前を入力します。 たとえば、「Web サーバー」というロール名を入力します。

14. 手順 12. と 13. を繰り返し、必要なロールをすべて追加します。

     各ロールでは、テスト コントローラーによって管理されるテスト エージェントが使用されます。

15. テストを実行するロールを選択し、**[テストを実行するロールとして設定]** を選択します。

    > [!IMPORTANT]
    > 作成および定義するその他のロールはテストを実行しませんが、**[データと診断]** ページのロールに指定するデータと診断アダプターに応じて、データ収集のためのみに使用されます。

16. ロールに使用できるエージェントを制限するには、ロールを選択し、**[選択されたロールのエージェント属性]** にあるツール バーの **[追加]** を選択します。

     **[エージェント選択規則]** ダイアログ ボックスが表示されます。

     **[属性名]** に名前を、**[属性値]** に値をそれぞれ入力し、**[OK]** を選択します。 必要な数だけ属性を追加します。

     たとえば、メモリが 16 GB を上回るテスト エージェント コンピューターをフィルターで選択するには、"True" または "False" の値を持つ "RAM > 16 GB" という名前の属性を追加できます。 同じ属性を複数のテスト エージェントに適用するには、[テスト コントローラーの管理] ダイアログ ボックスを使用します。 詳細については、「[Visual Studio でのテスト コントローラーおよびテスト エージェントの管理](../test/manage-test-controllers-and-test-agents.md)」を参照してください。

17. **[データと診断]** を選択します。

     **[データと診断]** ページが表示されます。

     ![テスト設定のデータと診断](../test/media/load_testtest.png "Load_TestTest")

18. **[データと診断]** ページで、ロールがデータ収集に使用する*診断データ アダプター*を選択してロールの実行内容を定義します。 その結果、1 つ以上のデータおよび診断アダプターがロールに対して有効になっていると、テスト コントローラーは使用可能なテスト エージェント コンピューターを選択し、ロールに定義された属性に基づいて、指定されたデータおよび診断アダプターのデータを収集します。 各ロールで収集するデータおよび診断データ アダプターを選択するには、ロールを選択します。 各ロールについて、テストのニーズに応じて診断データ アダプターを選択します。 各ロールに対して選択した診断データ アダプターを構成するには、**[構成]** を選択します。

     **ロールと診断データ アダプターの例:**

     たとえば、"Uses SQL" 属性を "True" に設定した "Desktop Client" という名前のクライアント ロールや、特定の属性を "RAM > 16 GB" に設定した "SQL Server" という名前のサーバー ロールを作成できます。 **[ロール]** ページの **[テストを実行するロールとして設定]** を選び、"Desktop Client" によってテストが実行されるように指定すると、"Uses SQL" 属性が "True" に設定されているテスト エージェントがあるコンピューターがテスト コントローラーによりテスト実行用として選択されます。 また、ロールに含まれているデータおよび診断アダプターによって定義されるデータを収集するためだけに、属性 "RAM > 16 GB" が含まれているテスト エージェントのある SQL Server コンピューターも選択されます。 このロールについてデータおよび診断アダプターも選択すると、"Desktop Client" テスト エージェントは、実行されるコンピューターのデータも収集できます。

     各診断データ アダプターの詳細および構成方法については、次の表に示す関連トピックを参照してください。

     診断データ アダプターの詳細については、「[Collect Diagnostic Information Using Test Settings](../test/collect-diagnostic-information-using-test-settings.md)」 (テスト設定を使用して診断情報を収集する) を参照してください。

     **ロード テストの診断データ アダプター**

    |診断データ アダプター|ロード テストでの使用|関連するトピック|
    |-----------------------------|-------------------------|----------------------|
    |**IntelliTrace およびテスト インパクト用の ASP.NET クライアント プロキシ**: このプロキシを使用すると、IntelliTrace 診断データ アダプターとテスト インパクト診断データ アダプターでクライアントから Web サーバーへの http 呼び出しに関する情報を収集できます。|![情報アイコン](../test/media/vc364f4.gif)<br /><br /> テスト エージェント コンピューターのシステム情報を収集する必要がある場合を除き、このアダプターを含めないでください。 **注意:** ロード テストでの IntelliTrace アダプターの使用はお勧めしません。大量のデータが収集されることで問題が発生する可能性があるためです。 <br /><br /> ロード テストを使用しても、テスト影響データは収集されません。||
    |**IntelliTrace:** ログ ファイルに格納する具体的な診断トレース情報を構成できます。 ログ ファイルの拡張子は .tdlog です。 テストを実行し、テスト ステップが失敗した場合は、バグを作成できます。 診断トレースが格納されたログ ファイルは、このバグに自動的にアタッチされます。 ログ ファイルに収集されたデータによって、コードのエラーを再現して診断するために必要な時間が短縮され、この結果、デバッグの生産性が向上します。 このログ ファイルから、別のコンピューターでローカル セッションを再作成できます。 これにより、バグを再現できない危険性が減少します。<br /><br /> 詳細については、[IntelliTrace データの収集](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)に関するページを参照してください。|![[重要] アイコン](../test/media/vc364f3.gif)<br /><br /> 大量のデータが収集および記録されることで問題が発生する可能性があるため、ロード テストでの IntelliTrace アダプターの使用はお勧めしません。 IntelliTrace アダプターは、実行時間が短く、それほど多くのテスト エージェントを使用しないロード テストでのみ使用してください。|[方法: 困難な問題をデバッグするのに役立つ IntelliTrace データを収集する](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|
    |**ASP.NET プロファイラー:** ASP.NET Web アプリケーションのパフォーマンス データを収集する ASP.NET プロファイリングを含むテストの設定を作成できます。|ASP.NET プロファイラー診断データ アダプターは、Internet Information Services (IIS) プロセスをプロファイルするため、開発用 Web サーバーに対しては機能しません。 ロード テスト内で Web サイトをプロファイルするには、IIS が実行されているコンピューターにテスト エージェントをインストールする必要があります。 テスト エージェントはロードを生成しませんが、コレクションのみのエージェントとなります。 詳細については、「[テスト エージェントをインストールして構成する](../test/lab-management/install-configure-test-agents.md)」を参照してください。|[方法: テストの設定を使用して、ロード テスト用の ASP.NET プロファイラーを構成する](../test/how-to-configure-aspnet-profiler-for-load-tests-using-test-settings.md)|
    |**イベント ログ:** イベント ログ収集を指定し、これをテスト結果に含めるようにテストの設定を構成できます。||[方法: テスト設定を使用してイベント ログ収集を構成する](http://msdn.microsoft.com/en-us/48d67891-6018-4549-83e3-213d5d824a02)|
    |**ネットワーク エミュレーション:** テストの設定を使用して、テストに対して人為的なネットワーク負荷をかけることを指定できます。 ネットワーク エミュレーションでは、ダイヤルアップなどの特定のネットワーク接続の速度をエミュレートすることにより、マシンに対する通信に影響を与えます。 **注:** ネットワーク接続の速度を向上するためにネットワーク エミュレーションを使用することはできません。|ネットワーク エミュレーション アダプターは、ロード テストでは無視されます。 ロード テストでは、ロード テスト シナリオのネットワーク ミックスで指定された設定が使用されます。<br /><br /> 詳細については、[仮想ネットワークの種類の指定](../test/specify-virtual-network-types-in-a-load-test-scenario.md)に関するページを参照してください。||
    |**システム情報:** システム情報診断とデータ コレクターを実行するコンピューターのシステム情報を含めるようにテストの設定を構成できます。 システム情報は、テストの設定を使用して、テスト結果で指定します。|![情報アイコン](../test/media/vc364f4.gif)<br /><br /> ロード エージェントとテスト対象のシステムの両方からシステム情報を収集できます。|この情報を収集するために構成は必要ありません。|
    |**テスト インパクト:** テスト ケースの実行時にアプリケーション コードのどのメソッドが使用されたかについての情報を収集できます。 これを、開発者によるアプリケーション コードに対する変更と合わせて使用することにより、このような開発上の変更によって影響を受けたテストを判別できます。|ロード テストを使用しても、テスト影響データは収集されません。||
    |**ビデオ レコーダー:** 自動テストの実行時にデスクトップ セッションのビデオ記録を作成できます。 これは、コード化された UI テストでのユーザー アクションを確認するために使用できます。 ビデオは、再現するのが困難なアプリケーション上の懸案事項をチーム メンバーが特定するのに役立ちます。 **注:** テストをリモートで実行する際、そのエージェントが対話プロセス モードで実行していない限りビデオ レコーダーは作動しません。|![重要アイコン](../test/media/vc364f3.gif) **警告:** ロード テストにビデオ レコーダー アダプターを使用することはお勧めしません。|[方法: テスト設定を使用してテスト中に画面と音声の記録を含める](../test/how-to-include-recordings-of-the-screen-and-voice-during-tests.md)|

19. **[配置]** を選択します。

     **[配置]** ページが表示されます。

20. テストを実行するたびに配置用の個別のディレクトリを作成するには、**[配置を有効にする]** を選択します。

    > [!NOTE]
    > このオプションを選択した場合は、テストの実行時にアプリケーションの作成を続行できます。

21. テストの実行に使用するディレクトリにファイルを追加するには、**[ファイルの追加]** を選び、追加するファイルを選択します。

    > [!NOTE]
    > ロード テストを実行すると、プラグイン アセンブリ、データ ファイル、およびアップロードされたファイルが自動的に配置されます。

22. テストの実行に使用するディレクトリにディレクトリを追加するには、**[ディレクトリの追加]** を選び、追加するディレクトリを選択します。

23. テストの前後にスクリプトを実行するには、**[セットアップおよび後処理用のスクリプト]** を選びます。

     **[セットアップおよび後処理用のスクリプト]** ページが表示されます。

    1.  **[セットアップ スクリプト]** にスクリプト ファイルの場所を入力するか、省略記号 **[…]** を選び、セットアップ スクリプトを指定します。

    2.  **[後処理用スクリプト]** にスクリプト ファイルの場所を入力するか、省略記号 **[…]** を選び、後処理用スクリプトを指定します。

24. 別のホストを使用してテストを実行する場合は、**[ホスト]** を選びます。

    1.  **[ホストの種類]** で、**[既定]** が選択されていることを確認します。

        > [!NOTE]
        > **[ホストの種類]** の **[ASP.NET]** は、ロード テストではサポートされていません。

    2.  [32 ビット プロセスまたは 64 ビット プロセスでテストを実行] ドロップダウン リストを使用して、ロード テストの Web パフォーマンス テストおよび単体テストを 32 ビット プロセスと 64 ビット プロセスのどちらで実行するか指定します。

        > [!NOTE]
        > 柔軟性を最大限に高めるには、**"Any CPU"** 構成を使用して Web パフォーマンスとロード テスト プロジェクトをコンパイルします。 これにより、32 ビット エージェントと 64 ビット エージェントの両方で実行できます。 **"64 ビット"** 構成で Web パフォーマンスとロード テストのプロジェクトをコンパイルしても、特に利点はありません。

25. (省略可能) 各テストの実行および個別のテストの実行時間を制限する場合は、**[テストのタイムアウト]** を選択します。

    1.  時間制限を超えた場合にテストの実行を中止するには、**[テストの実行時間が次の値を超えた場合、テストの実行を中止する]** を選択し、この制限に使用する値を入力します。

    2.  時間制限を超えた場合に個々のテストを失敗とするには、**[テストの実行時間が次の値を超えた場合、個々のテストを失敗とする]** を選択し、この制限に使用する値を入力します。

26. **[単体テスト]** をスキップします。 ロード テストではこれらの設定を使用しません。

27. **[Web テスト]** をスキップします。 ロード テストではこれらの設定を使用しません。

28. **[名前を付けて保存]** を選び、テストの設定を保存します。 **[オブジェクト名]** に、必要なファイルの名前を入力します。

    > [!NOTE]
    > テストの設定を変更する必要がある場合は、**[テスト]** を選び、**[テスト設定の編集]** を選び、作成したテスト設定をポイントします。

### <a name="to-remove-a-test-settings-from-your-solution"></a>ソリューションからテストの設定を削除するには

ソリューション エクスプローラーの [ソリューション項目] フォルダーで、削除するテスト設定を右クリックし、**[削除]** を選択します。

テストの設定ファイルがソリューションから削除されます。 この変更は、**[テスト]** メニューの **[アクティブなテスト設定の選択]** オプションおよび **[テスト設定の編集]** オプションの選択肢の一覧に反映されます。

## <a name="see-also"></a>関連項目

- [テスト コントローラーとテスト エージェント](configure-test-agents-and-controllers-for-load-tests.md)
- [テスト設定を使用して診断情報を収集する](../test/collect-diagnostic-information-using-test-settings.md)