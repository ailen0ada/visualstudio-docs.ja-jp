---
title: '方法: エディット コンティニュを使用 (c#) |Microsoft Docs'
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
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4305c39c62dfcc927ea7295ceec786d3da40f56
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538670"
---
# <a name="how-to-use-edit-and-continue-c"></a>方法 : エディット コンティニュを使用する (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: 使用の編集と続行 (c#)](https://docs.microsoft.com/visualstudio/debugger/how-to-use-edit-and-continue-csharp)します。  
  
C# のエディット コンティニュを使用すると、デバッグ中に中断モードでコードに変更を加えることができます。 デバッグ セッションを停止したり再開したりしなくても、変更を適用できます。  
  
 エディット コンティニュは自動的に呼び出されます、中断モードに変更し、デバッガーの実行を選択コマンドなど、**続行**、**手順**、または**次のステートメントの設定**、か、デバッガー ウィンドウで関数を評価します。  
  
> [!NOTE]
>  Compact Framework、最適化されたコード、ネイティブ コードとマネージ コードの混合コード、または SQL Server の共通言語ランタイム (CLR: Common Language Runtime) との統合コードのデバッグ時は、エディット コンティニュはサポートされません。 これらのシナリオのいずれかでコード変更を適用しようとすると、エディット コンティニュがサポートされないことを説明するダイアログ ボックスが表示されます。  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>エディット コンティニュを自動的に呼び出すには  
  
1.  中断モードで、ソース コードを変更します。  
  
2.  **デバッグ** メニューのをクリックして**続行**、**手順**、または**次のステートメントの設定**か、デバッガー ウィンドウで関数を評価します。  
  
     新しいコードがコンパイルされ、その新しいコードでデバッグが続行されます。 エディット コンティニュでサポートされない変更もあります。 詳細については、次を参照してください。[サポートされているコード変更 (c#)](../debugger/supported-code-changes-csharp.md)します。  
  
### <a name="to-enabledisable-edit-and-continue"></a>[エディット コンティニュ] を有効または無効にするには  
  
1.  **[ツール]** メニューの **[オプション]** をクリックします。  
  
2.  **オプション** ダイアログ ボックスで、展開、**デバッグ**ノード、および選択**エディット コンティニュ**します。  
  
3.  **オプション** ダイアログ ボックス**エディット コンティニュ**ページ、オンまたはオフ、**編集を有効にして続行**チェック ボックスをオンします。  
  
     デバッグ セッションを再開すると、この設定が有効になります。  
  
## <a name="see-also"></a>関連項目  
 [エディット コンティニュ (Visual c#)](../debugger/edit-and-continue-visual-csharp.md)   
 [サポートされているコードの変更 (c#)](../debugger/supported-code-changes-csharp.md)   
 [エディット コンティニュのエラーと警告 (C#)](../misc/edit-and-continue-errors-and-warnings-csharp.md)



