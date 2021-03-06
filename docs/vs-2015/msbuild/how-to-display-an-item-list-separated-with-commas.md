---
title: '方法: 項目リストをコンマ区切りで表示する | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62fbbfd7df89eee06f476a496b5a7c020c0ff211
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533652"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>方法: 項目リストをコンマ区切りで表示する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: 表示する項目で区切られたリストをコンマで](https://docs.microsoft.com/visualstudio/msbuild/how-to-display-an-item-list-separated-with-commas)します。  
  
  
[!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]) で項目一覧を使用するとき、項目一覧の内容を読みやすいように表示すると便利な場合があります。 あるいは、項目の一覧を特殊な区切り文字列で区切るタスクが与えられることがあります。 いずれの場合でも、項目一覧には区切り文字列を指定できます。  
  
## <a name="separating-items-in-a-list-with-commas"></a>一覧内の項目をコンマで区切る  
 既定では、[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] はセミコロンを利用して一覧内の項目を区切ります。 たとえば、次の値を持つ `Message` 要素があります。  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 `@(TXTFile)` 項目一覧に項目 App1.txt、App2.txt、App3.txt が含まれるとき、メッセージは次のようになります。  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 既定の動作を変更する場合、独自の区切りを指定できます。 項目一覧区切りを指定するための構文は次のようになります。  
  
 `@(ItemListName, '<separator>')`  
  
 区切りは単一の文字か文字列にすることができます。一重引用符で囲む必要があります。  
  
#### <a name="to-insert-a-comma-and-a-space-between-items"></a>項目の間にコンマとスペースを挿入するには  
  
-   次のような項目表記を使用します。  
  
     `@(TXTFile, ', ')`  
  
## <a name="example"></a>例  
 この例では、[Exec](../msbuild/exec-task.md) タスクは findstr ツールを実行し、ファイル Phrases.txt から指定のテキスト文字列を探します。 findstr コマンドでは、リテラル検索文字列が **/c:** スイッチによって示されます。そのため、項目区切り `/c:` が `@(Phrase)` 項目一覧の項目間に挿入されます。  
  
 この例では、次がこれに相当するコマンドライン コマンドです。  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```  
<Project DefaultTargets = "Find"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <Phrase Include="hello"/>  
        <Phrase Include="world"/>  
        <Phrase Include="msbuild"/>  
    </ItemGroup>  
  
    <Target Name = "Find">  
        <!-- Find some strings in a file -->  
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>関連項目  
 [MSBuild リファレンス](../msbuild/msbuild-reference.md)   
 [項目](../msbuild/msbuild-items.md)



