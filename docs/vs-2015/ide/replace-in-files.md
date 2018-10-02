---
title: '[フォルダーを指定して置換] | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- Find and Replace window, Replace in Files tab
- Replace in Files tab, Find and Replace window
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e693e1166a1612ae8ca82f5d1e8c0e742539da0a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546537"
---
# <a name="replace-in-files"></a>[フォルダーを指定して置換]
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ファイル内の置換](https://docs.microsoft.com/visualstudio/ide/replace-in-files)します。  
  
* * ファイル内の置換文字列や正規表現、ファイルの指定したセットのコードを検索し、見つかった一致の一部またはすべてを変更することができます。 見つかった一致項目と実行された処理は、**[結果オプション]** で選択した **[検索結果]** ウィンドウに表示されます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、[ツール] メニューの [設定のインポートとエクスポート] をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 **[検索と置換]** ウィンドウに **[フォルダーを指定して置換]** を表示するには、次の方法を使用できます。  
  
### <a name="to-display-replace-in-files"></a>[フォルダーを指定して置換] を表示するには  
  
1.  **[編集]** メニューで、**[検索と置換]** を展開します。  
  
2.  **[フォルダーを指定して置換]** を選択します。  
  
     または  
  
     **[検索と置換]** ウィンドウが既に開いている場合、ツール バーで **[フォルダーを指定して置換]** を選択します。  
  
## <a name="find-what"></a>[検索する文字列]  
 新しい文字列や式を検索するには、このボックスで指定します。 最近検索した 20 種類の文字列を検索するには、一覧を開き、検索する文字列をクリックします。 検索文字列に 1 つ以上の正規表現を使用する場合は、隣接する **[式ビルダー]** をクリックします。 詳細については、「[Visual Studio での正規表現の使用](../ide/using-regular-expressions-in-visual-studio.md)」を参照してください。  
  
## <a name="replace-with"></a>[置換後の文字列]  
 **[検索する文字列]** ボックスの文字列インスタンスを別の文字列で置換するには、**[置換後の文字列]** ボックスに置換後の文字列を入力します。 **[検索する文字列]** ボックスの文字列インスタンスを削除するには、このフィールドを空のままにします。 一覧を開くと、最近検索した 20 件の文字列が表示されます。 置換後の文字列に 1 つ以上の正規表現を使用する場合は、隣接する **[式ビルダー]** をクリックします。 詳細については、「[Visual Studio での正規表現の使用](../ide/using-regular-expressions-in-visual-studio.md)」を参照してください。  
  
## <a name="look-in"></a>[検索対象]  
 **[検索対象]** ボックスで選択したオプションにより、**[フォルダーを指定して置換]** 操作で現在アクティブなファイルのみを検索するか、特定のフォルダーに格納されているすべてのファイルを検索するかが決まります。 検索スコープを一覧から選択するか、フォルダー パスを入力し、**[参照] ([...])** ボタンをクリックして **[検索フォルダーの選択]** ダイアログ ボックスを表示し、検索するフォルダー セットを選択します。 **[検索対象]** ボックスにパスを直接入力することもできます。  
  
> [!NOTE]
>  選択した **[検索対象]** オプションにより、ソース コード管理からチェックアウトしたファイルを検索する場合は、ローカル マシンにダウンロードされたファイルのバージョンのみが検索されることに注意してください。  
  
## <a name="find-options"></a>検索オプション  
 **[検索オプション]** セクションは、展開または折りたたむことができます。 次のオプションは、オンまたはオフにできます。  
  
 大文字と小文字を区別する  
 選択すると、**[検索結果]** ウィンドウには、内容で一致し、さらに大文字/小文字の区別で一致する **[検索する文字列]** 文字列インスタンスのみが表示されます。 たとえば、**[大文字と小文字を区別する]** を選択して "MyObject" を検索すると、"MyObject" は返されますが、"myobject" や "MYOBJECT" は返されません。  
  
 [単語単位で探す]  
 選択すると、**[検索結果]** ウィンドウには、単語として一致する **[検索する文字列]** 文字列インスタンスのみが表示されます。 たとえば、"MyObject" を検索すると、"MyObject" は返されますが、"CMyObject" や "MyObjectC" は返されません。  
  
 正規表現の使用  
 このチェック ボックスをオンにすると、**[検索する文字列]** ボックスまたは **[置換後の文字列]** ボックスで特殊な表記を使用し、文字列のパターンを定義できます。 これらの表記の一覧については、「[Visual Studio での正規表現の使用](../ide/using-regular-expressions-in-visual-studio.md)」を参照してください。  
  
 [次のファイルの種類を参照]  
 この一覧は、**[検索対象]** ディレクトリで検索するファイルの種類を示します。 このフィールドが空白の場合は、**[検索対象]** ディレクトリ内のすべてのファイルが検索されます。  
  
 一覧の項目を選択し、特定の種類のファイルを検索する設定済みの検索文字列を入力します。  
  
## <a name="result-options"></a>結果オプション  
 **[結果オプション]** セクションは、展開または折りたたむことができます。 次のオプションは、オンまたはオフにできます。  
  
 [検索結果 1 ウィンドウ]  
 オンにすると、現在の検索結果で **[検索結果 1]** ウィンドウの内容が置換されます。 このウィンドウは自動的に開き、検索結果を表示します。 このウィンドウを手動で開くには、**[表示]** メニューの **[その他のウィンドウ]** を選択し、**[検索結果 1]** を選択します。  
  
 [検索結果 2 ウィンドウ]  
 オンにすると、現在の検索結果で **[検索結果 2]** ウィンドウの内容が置換されます。 このウィンドウは自動的に開き、検索結果を表示します。 このウィンドウを手動で開くには、**[表示]** メニューの **[その他のウィンドウ]** を選択し、**[検索結果 2]** を選択します。  
  
 [ファイル名のみ表示]  
 このチェック ボックスをオンにすると、[検索結果] ウィンドウに、検索文字列が含まれるすべてのファイルの完全名とパスが一覧表示されます。 ただし、結果には、文字列が表示されるコード行が含まれません。 このチェック ボックスは、[フォルダーを指定して検索] のみで利用できます。  
  
 [置換後に、変更したファイルを閉じない]  
 選択した場合、置換が行われたすべてのファイルを開いたままにします。変更を元に戻したり、保存したりできます。 メモリ制約により、置換後に開いた状態を維持できるファイルの数が制限されることがあります。  
  
> [!CAUTION]
>  **[元に戻す]** は、編集のために開いた状態を維持しているファイルにのみ使用できます。 このオプションが選択されていない場合、編集のために開いていなかったファイルは開いていない状態を維持します。そのようなファイルでは、**[元に戻す]** オプションは利用できません。  
  
## <a name="see-also"></a>関連項目  
 [テキストの検索と置換](../ide/finding-and-replacing-text.md)   
 [フォルダーを指定して検索](../ide/find-in-files.md)   
 [Visual Studio のコマンド](../ide/reference/visual-studio-commands.md)


