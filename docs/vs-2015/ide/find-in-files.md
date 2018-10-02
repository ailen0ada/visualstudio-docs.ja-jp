---
title: '[フォルダーを指定して検索] | Microsoft Docs'
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
- vs.findreplace.findinfiles
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
ms.assetid: 989e0737-46d7-4474-8453-fad52a74669d
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2f6f51f53642f0eb17cbbae5498ce1c4c288a867
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539942"
---
# <a name="find-in-files"></a>[フォルダーを指定して検索]
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ファイル内の検索](https://docs.microsoft.com/visualstudio/ide/find-in-files)します。  
  
* * ファイルの検索では、指定したファイル セットを検索できます。 見つかった一致項目と実行された処理は、**[結果オプション]** で選択した **[検索結果]** ウィンドウに表示されます。  
  
 **[検索と置換]** ウィンドウに **[フォルダーを指定して検索]** を表示する場合は、次の方法のいずれかを使用できます。  
  
### <a name="to-display-find-in-files"></a>[フォルダーを指定して検索] を表示するには  
  
1.  メニュー バーで **[編集]**、**[検索と置換]** の順に選択します。  
  
2.  **[フォルダーを指定して検索]** を選択します。  
  
 検索操作を取り消すには、Ctrl キーを押しながら Break キーを押します。  
  
> [!NOTE]
>  検索と置換ツールでは、`Hidden` 属性または `System` 属性が設定されているディレクトリは検索されません。  
  
## <a name="find-what"></a>[検索する文字列]  
 新しい文字列や式を検索するには、このボックスで指定します。 最近検索した 20 種類の文字列を検索するには、一覧を開き、検索する文字列をクリックします。 検索文字列に 1 つ以上の正規表現を使用する場合は、隣接する **[式ビルダー]** をクリックします。 詳細については、「[Visual Studio での正規表現の使用](../ide/using-regular-expressions-in-visual-studio.md)」を参照してください。  
  
## <a name="look-in"></a>[検索対象]  
 **[検索対象]** ドロップダウン リストから選択したオプションにより、**[フォルダーを指定して検索]** で現在アクティブなファイルのみを検索するか、特定のフォルダー内に格納されているすべてのファイルを検索するかが決まります。 検索スコープを一覧から選択するか、**[参照] ([...])** ボタンをクリックして **[検索フォルダーの選択]** ダイアログ ボックスを表示し、独自のディレクトリ セットを入力します。 **[検索対象]** ボックスにパスを直接入力することもできます。  
  
> [!WARNING]
>  **[ソリューション全体]** または **[現在のプロジェクト]** オプションでは、プロジェクトおよびソリューション ファイルは検索されません。 プロジェクト ファイルを検索対象にするには、検索フォルダーを選択します。  
  
> [!NOTE]
>  選択した **[検索対象]** オプションにより、ソース コード管理からチェックアウトしたファイルを検索する場合は、ローカル マシンにダウンロードされたファイルのバージョンのみが検索されることに注意してください。  
  
## <a name="include-subfolders"></a>サブフォルダーを含める  
 **[検索対象]** フォルダーのサブフォルダーが検索されるように指定します。  
  
## <a name="find-options"></a>検索オプション  
 **[検索オプション]** セクションは、展開または折りたたむことができます。 次のオプションは、オンまたはオフにできます。  
  
 大文字と小文字を区別する  
 オンにすると、**[検索結果]** 検索で大文字と小文字が区別されます。  
  
 [単語単位で探す]  
 オンにすると、単語単位で一致した項目のみが **[検索結果]** ウィンドウに表示されます。  
  
 正規表現の使用  
 このチェック ボックスをオンにすると、**[検索する文字列]** または **[置換後の文字列]** テキスト ボックスで特殊な表記を使用して、検索する文字列のパターンを定義できます。 これらの表記の一覧については、「[Visual Studio での正規表現の使用](../ide/using-regular-expressions-in-visual-studio.md)」を参照してください。  
  
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
 一致した検索結果自体ではなく、検索結果を含むファイルの一覧を表示します。  
  
 結果を追加  
 検索結果を、前の検索結果に追加します。  
  
## <a name="see-also"></a>関連項目  
 [テキストの検索と置換](../ide/finding-and-replacing-text.md)   
 [フォルダーを指定して置換](../ide/replace-in-files.md)   
 [Visual Studio のコマンド](../ide/reference/visual-studio-commands.md)


