---
title: データ ヒントでコード エディターでのデータ値の表示 |Microsoft Docs
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
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 41
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1a7e755fd81bb66d822f7232e903fea9c53087c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533896"
---
# <a name="view-data-values-in-data-tips--in-the-code-editor"></a>コード エディターでのデータ ヒントのデータ値の表示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[データ ヒントでコード エディターでのデータ値の表示](https://docs.microsoft.com/visualstudio/debugger/view-data-values-in-data-tips-in-the-code-editor)します。  
  
DataTips は、デバッグ中にプログラムの変数に関する情報を確認するときに便利です。 データヒントは、中断モードのときにのみ機能します。また、実行の現在のスコープ内にある変数に対してだけ使用できます。  
  
 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]、データヒントがソース ファイルで特定の場所にピン留めできますまたはすべてに加えて、変動する[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]windows。  
  
### <a name="to-display-a-datatip-in-break-mode-only"></a>データヒントを表示するには (中断モードのみ)  
  
1.  ソース ウィンドウで、現在のスコープにある任意の変数にマウス ポインターを移動します。  
  
     DataTip が表示されます。  
  
    > [!NOTE]
    >  データヒントは、プログラムの実行が中断され、カーソルがホバーしていないコンテキストで常に評価されます。 現在のコンテキスト内の変数と同じ名前の別の関数内の変数にポインターを合わせると、その別の関数内の変数の値が、現在のコンテキストの変数の値として表示されます。  
  
2.  マウス ポインターを離すとデータヒントが表示されなくなります。 未処理のままにするために、データヒントをピン留めする をクリックして、**ソースにピン留めする**アイコン、または  
  
    -   変数を右クリックし、をクリックして**ソースにピン留めする**します。  
  
     固定したデータヒントは、デバッグ セッションを終了すると閉じます。  
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>データヒントの固定を解除してフローティングするには  
  
-   固定されたデータヒント をクリックして、**ソースをピン解除**アイコン。  
  
     ピン アイコンの表示が固定が解除された状態に変わり、 開いているすべてのウィンドウの上でデータヒントをフローティングできるようになります。 フローティング状態のデータヒントは、デバッグ セッションを終了すると閉じます。  
  
### <a name="to-repin-a-floating-datatip"></a>フローティング状態のデータヒントを再度固定するには  
  
-   データヒントで、ピン アイコンをクリックします。  
  
     ピン アイコンの表示が固定された状態に変わります。 データヒントがソース ウィンドウ外にある場合は、ピン アイコンが無効になり、データヒントを固定することはできません。  
  
### <a name="to-close-a-datatip"></a>データヒントを閉じるには  
  
-   データヒントに合わせ、マウス ポインターを置きをクリックして、**閉じる**アイコン。  
  
### <a name="to-close-all-datatips"></a>すべてのデータヒントを閉じるには  
  
-   **デバッグ** メニューのをクリックして**すべてのデータヒントをクリア**します。  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>特定のファイルのすべてのデータヒントを閉じるには  
  
-   **デバッグ** メニューのをクリックして**クリアすべてデータヒントにピン留め***ファイル*します。  
  
## <a name="expanding-and-editing-information"></a>情報の展開と編集  
 データヒントを使用すると、配列、構造体、またはオブジェクトを展開して、メンバーを表示できます。 DataTip の変数値を編集することもできます。  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>変数を展開して要素を表示するには  
  
-   データヒントで、マウス ポインターを置く経由で、 **+** 変数名の前にサインオンします。  
  
     変数が展開され、ツリー形式で要素が表示されます。  
  
     変数を展開すると、キーボードの方向キーを使用して、上下に移動できます。 また、マウスも使用できます。  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>データヒントを使用して変数値を編集するには  
  
1.  データヒントで、値をクリックします。 読み取り専用の値では無効です。  
  
2.  新しい値を入力し、Enter キーを押します。  
  
## <a name="making-a-datatip-transparent"></a>DataTip を透過的にする  
 データヒントの背後にあるコードを確認する場合は、一時的にデータヒントを透過的に設定できます。 固定されているか、またはフローティング状態になっているデータヒントには適用されません。  
  
#### <a name="to-make-a-datatip-transparent"></a>DataTip を透過的にするには  
  
-   データヒントで、Ctrl キーを押します。  
  
     Ctrl キーを押している間、データヒントは透過的になります。  
  
## <a name="visualizing-complex-data-types"></a>複合データ型の表示  
 データヒント、1 つまたは複数の変数名の横にある虫眼鏡のアイコンが表示された場合[カスタム ビジュアライザーの作成](../debugger/create-custom-visualizers-of-data.md)はデータ型の変数を使用できます。 ビジュアライザーを使用すると、よりわかりやすい形式 (通常はグラフィック形式) で情報が表示されます。  
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>ビジュアライザーを使用して変数の内容を表示するには  
  
-   虫眼鏡アイコンをクリックし、データ型の既定のビジュアライザーを選択します。  
  
     - または -  
  
     ビジュアライザーの横にあるポップアップ矢印をクリックし、データ型の適切なビジュアライザーを一覧から選択します。  
  
     ビジュアライザーに情報が表示されます。  
  
## <a name="adding-information-to-a-watch-window"></a>ウォッチ ウィンドウへの情報の追加  
 変数のウォッチを継続する場合、変数の追加することができます、**ウォッチ**データヒントからウィンドウ。  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>ウォッチ ウィンドウに変数を追加するには  
  
-   データヒントを右クリックし、をクリックし、**ウォッチ式の追加**します。  
  
     変数を追加、**ウォッチ**ウィンドウ。 複数をサポートするエディションを使用している場合**ウォッチ**windows で、変数に追加されて**ウォッチ 1。**  
  
## <a name="importing-and-exporting-datatips"></a>データヒントのインポートとエクスポート  
 データヒントは XML ファイルにエクスポートして、他のユーザーと共有したり、テキスト エディターで編集したりすることができます。  
  
#### <a name="to-export-datatips"></a>データヒントをエクスポートするには  
  
1.  デバッグ メニューで、次のようにクリックします。**データヒントのエクスポート**します。  
  
     **データヒントのエクスポート**  ダイアログ ボックスが表示されます。  
  
2.  ファイルの名前を入力、XML ファイルを保存場所に移動するファイルの標準的な手法を使用して、**ファイル名**ボックスをクリックして**OK**します。  
  
#### <a name="to-import-datatips"></a>データヒントをインポートするには  
  
1.  デバッグ メニューで、次のようにクリックします。**データヒントのインポート**します。  
  
     **データヒントのインポート**  ダイアログ ボックスが表示されます。  
  
2.  開き、をクリックする XML ファイルを検索 ダイアログ ボックスを使用して**OK**します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーでのデータの表示](../debugger/viewing-data-in-the-debugger.md)   
 [方法: [クイック ウォッチ] ダイアログ ボックスを使用します。](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [カスタム ビジュアライザーを作成します。](../debugger/create-custom-visualizers-of-data.md)   
 [方法: Windows のデバッガーの数値書式の変更](http://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)



