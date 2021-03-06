---
title: デバッグ エンジンの実装方法の選択 |Microsoft Docs
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
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8a9e449fddad18c3ff0e95786ab852745407e6a1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536429"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>デバッグ エンジンの実装方法の選択
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[デバッグ エンジンの実装方法を選択する](https://docs.microsoft.com/visualstudio/extensibility/debugger/choosing-a-debug-engine-implementation-strategy)します。  
  
デバッグ エンジン (DE) の実装戦略を決定するのにには、実行時のアーキテクチャを使用します。 デバッグ エンジンを同じプロセスをデバッグしようとするプログラムを Visual Studio セッション デバッグ マネージャー (SDM) またはそれらの両方に、プロセスの外でプロセスを作成できます。 次のガイドラインはこれら 3 つの戦略の中から選択する際に役立ちます。  
  
## <a name="guidelines"></a>ガイドライン  
 アウト プロセスに DE のことはできますが、SDM との両方に、プログラムをデバッグできる、理由はありません通常これを行う。 プロセスの境界を越えて呼び出しは比較的低速です。  
  
 デバッグ エンジンは Win32 ネイティブ ランタイム環境との共通言語ランタイム環境に既に提供されます。 これらの環境のいずれかのデを置き換える必要があります、SDM をインプロセス DE を作成する必要があります。  
  
 それ以外の場合の SDM をインプロセスまたは同じプロセスをデバッグするプログラムには、DE を作成することができます。 これが、DE の式エバリュエーターが、プログラムのシンボル ストアに頻繁にアクセスを必要があるかどうかと、シンボル ストアを高速アクセスをメモリに読み込むことがかどうかを検討する重要です。 また、次の点を検討してください。  
  
-   式エバリュエーターと、シンボル ストアの間の多数の呼び出しが存在しない場合、またはシンボル ストアは、SDM のメモリ領域に読み取ることができる場合、SDM をインプロセス DE を作成します。 プログラムにアタッチするときに、SDM デバッグ エンジンの CLSID を返す必要があります。 SDM は、この CLSID を使用して、DE のインプロセス インスタンスを作成します。  
  
-   場合は、DE シンボル ストアにアクセスするプログラムを呼び出す必要があります、DE、インプロセスをプログラムで作成します。 この場合、プログラムは、DE のインスタンスを作成します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

