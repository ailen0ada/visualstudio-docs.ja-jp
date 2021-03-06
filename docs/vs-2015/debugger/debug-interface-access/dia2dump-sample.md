---
title: Dia2dump サンプル |Microsoft Docs
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
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 410d4e8cf2a63c7d01058e501391f02543b1eee7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544815"
---
# <a name="dia2dump-sample"></a>Dia2dump サンプル
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Dia2dump サンプル](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/dia2dump-sample)します。  
  
Dia2dump サンプルでは、Visual Studio と共にインストールされ、Dia2dump.cpp ソース ファイルが含まれています。 コンパイル済み実行可能ファイルは、コマンドラインから実行し、プログラム全体のデータベース (.pdb) ファイルの内容を表示します。  
  
### <a name="to-install-the-sample"></a>サンプルをインストールするには  
  
1.  システムが Visual Studio セットアップの開始 ページで説明されているすべてのセットアップ要件を満たしていることを確認します。  
  
2.  Visual Studio をインストールして、サンプルは、のすべてのセットアップとインストールの指示に従います。  
  
#### <a name="to-build-the-sample"></a>サンプルをビルドするには  
  
1.  Visual Studio で Dia2dump.sln ファイルを開きます。 (必要に応じて、Visual Studio 最初する際に役立つ Dia2dump プロジェクトをアップグレードします。)  
  
2.  プロジェクトのプロパティ ページでの**C と C++** &#124; **全般** &#124; **追加のインクルード ディレクトリ**プロパティを指定、`..\DIA SDK\include`ディレクトリ。 これにより、コンパイラが dia2.h ファイルを見つけることができます。  
  
3.  **ビルド** メニューのをクリックして**ソリューションのリビルド**します。  
  
4.  Visual Studio を閉じます。  
  
#### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1.  コマンド プロンプトを開き、次に入力します。  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>関連項目  
 [Dia2dump.cpp ソース ファイル](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [方法: Visual Studio プロジェクトのアップグレードが成功しなかった場合のトラブルシューティング](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)



