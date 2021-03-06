---
title: '方法: ClickOnce で発行されるファイルの指定 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.File
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, file exclusion
- files, publishing via ClickOnce
ms.assetid: 579c134a-d50f-4e0c-8e05-2a4ff654896a
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: c56d378c8adee1801fb82fc4a2ed84e5b05c0aef
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536098"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>方法: ClickOnce で発行されるファイルを指定する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: 指定するファイル ClickOnce で発行される](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-which-files-are-published-by-clickonce)します。  
  
発行するときに、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]プロジェクト内のアプリケーション、コード以外のすべてのファイルは、アプリケーションと共にデプロイされます。 場合によっては、場合や、特定のファイルを発行する必要がない可能性がありますかを条件に基づく特定のファイルをインストールすることがあります。 Visual Studio には、ファイルを除外する、ファイルをデータ ファイルや必須コンポーネントとしてマークし、条件付きでインストールするファイルのグループを作成する機能が用意されています。  
  
 ファイルを[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]でアプリケーションが管理されている、**アプリケーション ファイル**からアクセスできるダイアログ ボックス、**発行**のページ、**プロジェクト デザイナー**します。  
  
 最初に、という名前の 1 つのファイル グループがある **(必須)** します。 追加のファイル グループを作成し、ファイルを割り当てることができます。 変更することはできません、**ダウンロード グループ**アプリケーションを実行するために必要なファイル。 たとえば、アプリケーションの .exe ファイルやとしてマークするデータ ファイルが属する必要があります、 **(必須)** グループ。  
  
 既定の発行状態で、ファイルの値がタグ付け **(自動)** します。 たとえばの発行状態には、アプリケーションの .exe**含める (自動)** 既定。  
  
 使用するファイル、**ビルド アクション**プロパティに設定**コンテンツ**アプリケーション ファイルとして指定しては既定で含まれているとしてマークされます。 含まれる、除外したりできますデータ ファイルとしてマークします。 例外は次のとおりです。  
  
-   SQL データベース (.mdf ファイルおよび .mdb) ファイルと XML ファイルなどのデータ ファイルは、既定では、データ ファイルとしてマークされます。  
  
-   参照を追加するとき、アセンブリ (.dll ファイル) への参照が次のように指定されます: 場合**ローカル コピー**は**False**、既定では、前提条件となるアセンブリとしてマークされている (**(前提条件自動)**) アプリケーションをインストールする前に、GAC に存在している必要があります。 場合**ローカル コピー**は**True**、アセンブリは既定では、アプリケーション アセンブリとしてマークされます (**含める (自動)**)、インストール時にアプリケーション フォルダーにコピーされます。 COM の参照が表示されます、**アプリケーション ファイル** ダイアログ ボックス (.ocx ファイル) として場合にのみその**Isolated**プロパティに設定されて**True**します。 既定では、含まれることです。  
  
### <a name="to-add-files-to-the-application-files-dialog-box"></a>アプリケーション ファイル ダイアログ ボックスにファイルを追加するには  
  
1.  データ ファイルを選択**ソリューション エクスプ ローラー**します。  
  
2.  [プロパティ] ウィンドウで変更、**ビルド アクション**プロパティを**コンテンツ**値。  
  
### <a name="to-exclude-files-from-clickonce-publishing"></a>ClickOnce の発行からファイルを除外するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  をクリックして、**アプリケーション ファイル**ボタンをクリックする、**アプリケーション ファイル** ダイアログ ボックス。  
  
4.  **アプリケーション ファイル** ダイアログ ボックスで、除外するファイルを選択します。  
  
5.  **発行の状況**フィールドで、**除外**ドロップダウン リストから。  
  
### <a name="to-mark-files-as-data-files"></a>データ ファイルとしてファイルをマークするには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  をクリックして、**アプリケーション ファイル**ボタンをクリックする、**アプリケーション ファイル** ダイアログ ボックス。  
  
4.  **アプリケーション ファイル** ダイアログ ボックスで、データとしてマークするファイルを選択します。  
  
5.  **発行の状況**フィールドで、**データファイル**ドロップダウン リストから。  
  
### <a name="to-mark-files-as-prerequisites"></a>ファイルの前提条件としてマークするには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  をクリックして、**アプリケーション ファイル**ボタンをクリックする、**アプリケーション ファイル** ダイアログ ボックス。  
  
4.  **アプリケーション ファイル** ダイアログ ボックスで、前提条件としてマークする、アプリケーション アセンブリ (.dll ファイル) を選択します。 なお、アプリケーションが一覧に表示するためにアプリケーション アセンブリへの参照を必要する必要があります。  
  
5.  **発行の状況**フィールドで、**前提条件となる**ドロップダウン リストから。  
  
### <a name="to-add-a-new-file-group"></a>新しいファイル グループを追加するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  をクリックして、**アプリケーション ファイル**ボタンをクリックする、**アプリケーション ファイル** ダイアログ ボックス。  
  
4.  **アプリケーション ファイル**ダイアログ ボックスで、**グループ**新しいグループに追加するファイルのフィールド。  
  
    > [!NOTE]
    >  ファイルが必要、**ビルド アクション**プロパティに設定**コンテンツ**にファイル名が表示されるまで、**アプリケーション ファイル** ダイアログ ボックス。  
  
5.  **ダウンロード グループ**フィールドで、 **\<新規作成 >** ドロップダウン リストから。  
  
6.  **新規グループ** ダイアログ ボックスで、グループの名前を入力し、順にクリックします**OK**します。  
  
### <a name="to-add-a-file-to-a-group"></a>グループにファイルを追加するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  をクリックして、**アプリケーション ファイル**ボタンをクリックする、**アプリケーション ファイル** ダイアログ ボックス。  
  
4.  **アプリケーション ファイル**ダイアログ ボックスで、**グループ**新しいグループに追加するファイルのフィールド。  
  
5.  **ダウンロード グループ**フィールドに、ドロップダウン リストからグループを選択します。  
  
    > [!NOTE]
    >  変更することはできません、**ダウンロード グループ**アプリケーションを実行するために必要なファイル。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



