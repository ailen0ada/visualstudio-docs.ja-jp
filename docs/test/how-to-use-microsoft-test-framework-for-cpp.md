---
title: Visual Studio で C++ 用の Microsoft 単体テスト フレームワークを使用する
ms.date: 11/15/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 6087b864ba497d3754adfa01dc0168da5317aa5e
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379554"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Visual Studio で C++ 用の Microsoft 単体テスト フレームワークを使用する

**C++ ワークロードによるデスクトップ開発**には、既定では Microsoft 単体テスト フレームワークが含まれます。

##  <a name="separate_project"></a>単体テストを個別のプロジェクトで作成するには

通常、独自のプロジェクト内のコードもテストするコードと同じソリューションでテストします。 新しいテスト プロジェクトをセットアップして構成するには、[C/C++ 用の単体テストの作成](writing-unit-tests-for-c-cpp.md)に関するページを参照してください。

##  <a name="same_project"></a> 同じプロジェクトで単体テストを作成するには

DLL でエクスポートされない関数をテストするときなど、場合によっては、テストするプログラムと同じプロジェクトでテストを作成することが必要になります。 同じプロジェクトで単体テストを作成するには:

1.  単体テストに必要なヘッダーおよびライブラリ ファイルが含まれるように、プロジェクトのプロパティを変更します。

    1.  **ソリューション エクスプローラー**で、テストするプログラムのプロジェクト ノードを右クリックして、**[プロパティ]** > **[構成プロパティ]** > **[VC++ ディレクトリ]** の順に選択します。

    3.  次の行の下向きの矢印をクリックし、**[<Edit>]** を選択します:

        |ディレクトリ|プロパティ|
        |-|-|
        |**インクルード ディレクトリ**|**$(VCInstallDir)UnitTest\include;$(IncludePath)**|
        |**ライブラリ ディレクトリ**|**$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|

2.  C++ 単体テスト ファイルを追加します。

    -   新しいファイルを追加するには、**ソリューション エクスプローラー**でプロジェクト ノードを右クリックし、**[追加]** > **[新規アイテム]** > **[C++ 単体テスト]** を選択します。

## <a name="write-the-tests"></a>テストを作成

テスト クラスを含む *.cpp* ファイルには、"CppUnitTest.h" に加えて、`using namespace Microsoft::VisualStudio::CppUnitTestFramework` 用の using ステートメントが必要です。 テスト プロジェクトは既に構成されています。 これには、名前空間の定義と、開始するための TEST_METHOD を含んだ TEST_CLASS も記述されています。 名前空間の名前だけでなく、クラスとメソッドのマクロ内のかっこで囲んだ名前も変更することができます。

テスト モジュール、クラス、およびメソッドを初期化するため、およびテストが完了したときにリソースをクリーンアップするために、特殊なマクロが定義されます。 これらのマクロは、クラスまたはメソッドに最初にアクセスする前に実行されるコードと、最後のテストを実行した後に実行されるコードを生成します。 詳細については、[初期化とクリーンアップ](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup)に関するページを参照してください。

[Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) クラスに静的メソッドを使用して、テスト条件を定義します。 [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) クラスを使用して、**[出力ウィンドウ]** にメッセージを書き込みます。 テスト メソッドに属性を追加する

## <a name="run-the-tests"></a>テストを実行

1.  **[テスト]** メニューで、**[Windows]**、**[テスト エクスプローラー]** の順に選択します。
2. ウィンドウに一部のテストしか表示されない場合は、次の方法でテスト プロジェクトをビルドします。**ソリューション エクスプローラー**で、該当するノードを右クリックし、**[ビルド]** または **[リビルド]** を選択します。

2.  **テスト エクスプローラー**で、**[すべて実行]** を選択するか、または実行する特定のテストを選択します。 ブレークポイントを有効にした場合のデバッグ モードでのテストの実行など他のオプションについては、テストを右クリックします。
3. **[出力ウィンドウ]** で、ドロップダウンから **[テスト]** を選択し、`Logger` クラスによって書き出されたメッセージを表示します。

  ![テスト メッセージを示す C++ 出力ウィンドウ](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>グループ化を有効にするための特徴を定義する

**テスト エクスプローラー**でテストを分類してグループ化するための特徴をテスト メソッドに対して定義できます。 特徴を定義するには、 `TEST_METHOD_ATTRIBUTE` マクロを使用します。 たとえば、特徴 `TEST_MY_TRAIT`を定義するには、次のように記述します。

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

 定義された特徴を単体テストで使用するには、次のように記述します。

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
    TEST_OWNER(L"OwnerName")
    TEST_PRIORITY(1)
    TEST_MY_TRAIT(L"thisTraitValue")
END_TEST_METHOD_ATTRIBUTE()

TEST_METHOD(Method1)
{
    Logger::WriteMessage("In Method1");
    Assert::AreEqual(0, 0);
}
```

### <a name="c-trait-attribute-macros"></a>C++ の特徴の属性マクロ

次の定義済みの特徴は、`CppUnitTest.h` にあります。 詳細については、「[C++ API リファレンス用の Microsoft 単体テスト フレームワーク](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)」を参照してください。

|マクロ|説明|
|-----------|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|TEST_METHOD_ATTRIBUTE マクロを使用して、特徴を定義します。|
|`TEST_OWNER(ownerAlias)`|定義済みの所有者の特徴を使用して、テスト メソッドの所有者を指定します。|
|`TEST_PRIORITY(priority)`|定義済みの優先度の特徴を使用して、テスト メソッドに相対的な優先度を割り当てます。|

## <a name="see-also"></a>関連項目

- [クイック スタート: テスト エクスプローラーによるテスト駆動開発](../test/quick-start-test-driven-development-with-test-explorer.md)

