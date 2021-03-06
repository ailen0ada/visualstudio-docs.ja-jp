---
title: '方法 : プロジェクトを構成して対象プラットフォームを設定する | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a79b32583b130b62dc9946acd71776ac67159817
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533609"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>方法 : プロジェクトを構成して対象プラットフォームを設定する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: 構成 Projects to Target Platforms](https://docs.microsoft.com/visualstudio/ide/how-to-configure-projects-to-target-platforms)します。  
  
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] では、64 ビット プラットフォームを含む、さまざまなプラットフォーム向けにアプリケーションを設定できます。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] での 64 ビット プラットフォームのサポートについて詳しくは、「[64 ビット アプリケーション](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)」を参照してください。  
  
## <a name="targeting-platforms-with-the-configuration-manager"></a>構成マネージャーを使用した対象プラットフォームの指定  
 **構成マネージャー**を使うと、プロジェクトの対象となる新しいプラットフォームをすばやく追加できます。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] に用意されているプラットフォームのいずれかを選択すると、プロジェクトのプロパティは、選択したプラットフォーム向けにプロジェクトをビルドするように変更されます。  
  
#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>64 ビット プラットフォームを対象とするようにプロジェクトを構成するには  
  
1.  メニュー バーで **[ビルド]**、 **[構成マネージャー]** の順に選択します。  
  
2.  **[アクティブ ソリューション プラットフォーム]** ボックスの一覧で、ソリューションの対象となる 64 ビット プラットフォームを選び、**[閉じる]** を選びます。  
  
    1.  必要なプラットフォームが表示されない場合は、**[アクティブ ソリューション プラットフォーム]** ボックスの一覧の **[新規作成]** を選びます。  
  
         **[新しいソリューション プラットフォーム]** ダイアログ ボックスが表示されます。  
  
    2.  **[新しいプラットフォームを入力または選択してください]** ボックスの一覧で、**[x64]** を選びます。  
  
        > [!NOTE]
        >  構成に新しい名前を指定する場合は、**[プロジェクト デザイナー]** で適切なプラットフォームを対象にするよう設定の変更が必要になることがあります。  
  
    3.  現在のプラットフォーム構成から設定をコピーする場合は、構成を選んでから **[OK]** を選びます。  
  
 64 ビット プラットフォームを対象とするすべてのプロジェクトのプロパティが更新され、プロジェクトの次のビルドは 64 ビット プラットフォーム用に最適化されます。  
  
## <a name="targeting-platforms-in-the-project-designer"></a>プロジェクト デザイナーを使用した対象プラットフォームの指定  
 プロジェクト デザイナーにも、さまざまなプラットフォームをプロジェクトの対象にする方法が用意されています。 **[新しいソリューション プラットフォーム]** ダイアログ ボックスの一覧にあるプラットフォームのいずれかを選んでも、ソリューションで機能しない場合は、カスタム構成名を作成し、**プロジェクト デザイナー**で設定を変更して、適切なプラットフォームを対象にすることができます。  
  
 このタスクの実行方法は、使用するプログラミング言語によって異なります。 詳細については、次のリンクを参照してください。  
  
-   [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] プロジェクトについては、「[/platform (Visual Basic)](http://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1)」をご覧ください。  
  
-   [!INCLUDE[csprcs](../includes/csprcs-md.md)] プロジェクトについては、「[[ビルド] ウィンドウ (プロジェクト デザイナー) (C#)](../ide/reference/build-page-project-designer-csharp.md)」をご覧ください。  
  
-   [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] プロジェクトについては、「[/clr (共通言語ランタイムのコンパイル)](http://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [ビルド プラットフォームについて](../ide/understanding-build-platforms.md)   
 [/platform (C# コンパイラ オプション)](http://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04)   
 [64 ビット アプリケーション](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Visual Studio IDE の 64 ビット サポート](../ide/visual-studio-ide-64-bit-support.md)



