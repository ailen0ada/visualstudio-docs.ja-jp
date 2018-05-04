---
title: Visual Studio でロード テストのために Web サイトの実際の使用状況をエミュレートする
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load model, specifying
- load test load model, specifying
ms.assetid: b7fae849-0538-40d1-ab35-2bb3a0fe4393
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 9ec5777bc1a2bfffc650497314a219d071057beb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="emulate-expected-real-world-usage-of-a-web-site-or-application-in-a-load-test-using-a-test-mix-models"></a>テスト ミックス モデルを使用してロード テストでの Web サイトまたはアプリケーションの実際の使用状況をエミュレートする

さまざまなロード モデリング オプションを使用して、ロード テストの対象となる Web サイトまたはアプリケーションの実際の使用状況をより正確に予測します。 正確なロード モデルに基づかないロード テストでは、誤解を招く結果が生じる可能性があるので、これを行うことが重要です。

## <a name="test-mix-model-enhancements"></a>テスト ミックス モデルの強化

ロード テスト エディターまたはテスト ミックス モデル ウィザードを使用して、ロード テスト シナリオで以下の種類のテスト ミックスを指定できます。 詳細については、「[シナリオのテスト ミックス モデルの変更](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)」を参照してください。

ロード テスト シナリオに、次のいずれかのテスト ミックス モデル オプションを指定できます。

-   **テストの合計数に基づく:** 仮想ユーザーがテスト イテレーションを開始するときに実行される Web パフォーマンス テストまたは単体テストを決定します。 ロード テストの終了時に、特定のテストの実行の回数が、割り当てられたテストの配分に近づけられます。 IIS ログまたは本番データのトランザクションの割合に基づくテスト ミックスを使用する場合に、このテスト ミックス モデルを使用します。 詳細については、「[開始されるテストに基づく割合](#BasedOnTestsStarted)」を参照してください。

-   **仮想ユーザー数に基づく:** 特定の Web パフォーマンス テストまたは単体テストを実行する仮想ユーザーの割合を決定します。 ロード テストのどの時点でも、特定のテストを実行中のユーザーの数が、割り当てられた配分に一致します。 テスト ミックスが、特定のテストを実行しているユーザーの割合に基づいている場合、このテスト ミックス モデルを使用します。 詳細については、「[仮想ユーザーに基づく割合](#PercentageBasedonVirtualUsers)」を参照してください。

-   **ユーザーのペースに基づく:** ロード テストの過程で、各 Web パフォーマンス テストまたは単体テストが、ユーザーおよび時間ごとに指定された回数実行されます。 仮想ユーザーがロード テスト全体で一定のペースでテストを実行するようにする場合、このテスト ミックス モデルを使用します。 詳細については、「[テスト ミックスのペース配分](#PacingTestMix)」を参照してください。

    > [!TIP]
    > **テスト ミックスの割合**と**仮想ユーザーに基づく割合**の選択基準は何でしょうか。 この 2 つの選択肢の違いは、テスト ミックス内に他のテストと比較して継続時間が長いテストが含まれている場合に重要です。 このような状況の場合は**仮想ユーザーに基づく割合**を選択してください。 この選択は、多数のユーザーが長時間継続するテストを実行する可能性が高いテストの実行を回避するために有用です。 ただし、すべてのテストの継続時間がほぼ同じ場合は、**テスト ミックスの割合**を選択しても問題はありません。

-   **時系列順に基づく:** 各仮想ユーザーは、テストがシナリオで定義されている順序に従って、Web パフォーマンス テストまたは単体テストを実行します。 仮想ユーザーは、ロード テストが完了するまでこの順序でテストの繰り返しを続行します。 詳細については、「[順次処理](#SequentialOrder)」を参照してください。

###  <a name="BasedOnTestsStarted"></a> 開始されるテストに基づく割合
 ミックス内のテストごとに、次回のテスト実行時にそのテストが選択される頻度を決定する割合を指定できます。 たとえば、3 種類のテストに対して次の割合を割り当てることができます。

-   TestA (50%)

-   TestB (35%)

-   TestC (15%)

 この設定を使用すると、次回のテストは、割り当てられた割合に基づいて開始されます。 ここでは、現在各テストを実行中の仮想ユーザーの数は考慮されません。

###  <a name="PercentageBasedonVirtualUsers"></a> 仮想ユーザーに基づく割合
 このテスト ミックス モデルは、特定のテストを実行する仮想ユーザーの割合を決定します。 このテスト ミックス モデルを使用すると、次回のテストは、割り当てられた割合だけではなく、特定のテストを現在実行中の仮想ユーザーの割合も考慮して開始されます。 ロード テストのどの時点でも、特定のテストを実行中のユーザーの数は、割り当てられた配分に可能な限り近づけられます。

###  <a name="PacingTestMix"></a> テスト ミックスのペース配分
 テスト ミックスのペース配分を指定する場合は、テスト ミックス内のテストごとに各仮想ユーザーが実行するテストの実行のレートを設定します。 このレートは、各テストで、1 人の仮想ユーザーが 1 時間に実行するテストの実行として表されます。 たとえば、次のテスト ミックスのペース配分を各テストに割り当てることができます。

-   TestA: 各ユーザーが 1 時間に 4 回テスト

-   TestB: 各ユーザーが 1 時間に 2 回テスト

-   TestC: 各ユーザーが 1 時間に 0.125 回テスト

 テスト ミックスのペース配分モデルを使用した場合は、ロード テスト ランタイム エンジンが、実際に開始されるテストのレートが指定されたレート以下になることを保証します。 割り当てられた数のテストの実行が完了するまでに時間がかかりすぎる場合は、エラーが返されます。

 テスト ミックスのペース配分を使用する場合、**[テスト イテレーション間の待ち時間]** 設定は適用されません。

#### <a name="applying-distribution-to-pacing-delay"></a>ペース配分遅れへの分布の適用
 ロード テスト シナリオの **"遅延のペースに分布を適用"** プロパティの値を、true または false のどちらかに設定できます。

-   **True**: [テスト ミックスの編集] ダイアログ ボックスの **[1 ユーザーの 1 時間あたりのテスト数]** 列の値で指定された、標準的な統計分布による遅れを適用します。 詳細については、「[テキスト ミックス モデルを編集して仮想ユーザーがテストを実行する確率を指定する](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)」を参照してください。

     たとえば、テストの [テスト ミックスの編集] ダイアログ ボックスの **[1 ユーザーの 1 時間あたりのテスト数]** の値を、1 時間あたり 2 ユーザーに設定したとします。 **"遅延のペースに分布を適用"** プロパティを **True** に設定すると、標準的な統計分布がテスト間の待機時間に適用されます。 1 時間につき 2 つのテストが実行されますが、その間隔は 30 分とは限りません。 最初のテストが 4 分後に実行されたり、2 回目のテストは 45 分後に実行されたりする場合があります。

-   **False**: テストは、[テスト ミックスの編集] ダイアログ ボックスの **[1 ユーザーの 1 時間あたりのテスト数]** 列の値に指定した特定のペースで実行されます。 詳細については、「[テキスト ミックス モデルを編集して仮想ユーザーがテストを実行する確率を指定する](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)」を参照してください。

     たとえば、テストの [テスト ミックスの編集] ダイアログ ボックスの **[1 ユーザーの 1 時間あたりのテスト数]** の値を、1 時間あたり 2 ユーザーに設定したとします。 **"遅延のペースに分布を適用"** プロパティを **False** に設定すると、基本的にテスト実行時の設定を変更する余裕はなくなります。 テストは 30 分ごとに実行されます。 これにより、1 時間あたり 2 回のテストが行われます。

 詳細については、「[方法: 配分を適用してユーザー ペースのテスト ミックス モデルを使用するときの遅延をペース配分する](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)」を参照してください。

###  <a name="SequentialOrder"></a> 順次処理
 順次処理に基づいてオプションを選択すると、仮想ユーザーは、テストが定義されている順序に従って、シナリオでのすべてのテストを実行するようになります。

## <a name="test-iterations-property"></a>[テスト イテレーション] プロパティ
 実行設定プロパティの中で、[テスト イテレーション] プロパティの値を指定できます。 この値は、1 回のロード テストで実行されるテストの反復回数です。 指定された回数のテスト イテレーションが開始されると、負荷プロファイルの設定にかかわらず、他のテスト イテレーションは開始されません。 指定された回数のテスト イテレーションが完了すると、ロード テストが終了します。 詳細については、「[方法: テスト イテレーションの数をテストの実行設定に指定する](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)」を参照してください。

## <a name="initialize-and-terminate-tests"></a>初期化テストと終了テスト
 各仮想ユーザーのロード テスト セッションの始まりと終わりに実行するテストを選択できます。 詳細については、「[テキスト ミックス モデルを編集して仮想ユーザーがテストを実行する確率を指定する](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)」を参照してください。

-   **初期化テスト**。 このテストは、テスト ミックス内のいずれかのテストが実行される前に、各仮想ユーザーによって実行されます。

-   **終了テスト**。 このテストは、特定の仮想ユーザーのすべてのテストが実行された後で実行されます。

 初期化テストと終了テストには次の注意点があります。

-   ロード テストの継続時間を、反復カウントではなく、時間で指定できます。 この場合、ロード テストの実行の継続時間が完了すると、終了テストは実行されません。

-   初期化テストが単体テストまたは Web パフォーマンス テストの場合は、初期化テストの完了後の TestContext オブジェクトまたは WebTestContext オブジェクトの状態が保存されます。 これは、テスト ミックス内のテスト イテレーションのための開始コンテキストとして使用されます。

-   シナリオ プロパティである [新しいユーザーのパーセンテージ] に定義された新しいユーザーは、初期化テスト、テスト ミックス内のテスト (1 回)、および終了テストを常に実行します。

## <a name="see-also"></a>関連項目

- [テキスト ミックス モデルを編集して仮想ユーザーがテストを実行する確率を指定](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
- [ロード パターンを編集して仮想ユーザー アクティビティをモデル化](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [テスト ミックスを編集して、ロード テスト シナリオに含めるテストを指定](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [ロード テストの実行設定の構成](../test/configure-load-test-run-settings.md)
- [ロード テスト シナリオのプロパティ](../test/load-test-scenario-properties.md)
- [シナリオのテスト ミックス モデルの変更](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)