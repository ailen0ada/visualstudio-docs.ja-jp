---
title: プロファイルと Windows Vista のセキュリティ | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 736e7a04813a6c56d6cab6d1886171e321d583cb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547620"
---
# <a name="profiling-and-windows-vista-security"></a>プロファイルと Windows Vista のセキュリティ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[プロファイルと Windows Vista のセキュリティ](https://docs.microsoft.com/visualstudio/profiling/profiling-and-windows-vista-security)します。  
  
コンピューターの管理者が使用可能にした [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] ユーザー アクセス許可の設定に応じて、個々のユーザーは、コンピューター上でプロセスをプロファイリングするためのセキュリティ アクセス許可を持っている場合があります。 次の例では、考えられるユーザーごとの違いについて説明します。  
  
-   管理者がドライバーとサービスが起動するように設定しているときには、一部のユーザーが高度なプロファイリング機能にアクセスできることがあります。  
  
-   ドメイン ユーザーはサンプルのプロファイリングにのみアクセスできる場合があります。  
  
-   一部のユーザーが他のすべてのユーザーに対してプロファイリングへのアクセスを拒否することがあります。  
  
 詳細については、「[VSPerfCmd](../profiling/vsperfcmd.md)」の ADMIN オプションを参照してください。  
  
## <a name="cross-session-profiling"></a>セッション間プロファイリング  
 *セッション間プロファイリング*は、別のログオン セッションで実行しているプロセスをプロファイリングする機能です。 たとえば、サービスのほとんどはセッション 0 で実行され、ユーザーはセッション 0 で直接実行できません。 パフォーマンス エクスプローラーのツールバーで **[プロセスにアタッチ]** ボタン、または VSPerfCmd コマンド ライン ツールの /attach オプションを使用して、さまざまなログオン セッションでのほとんどのプロセスをプロファイリングすることができます。  
  
 プロセス間のプロファイルの表示オプションを設定すると、使用できるプロセスの一覧が表示できます。 これらのオプションは、**[プロセスにアタッチ]** をクリックすると表示される **[プロセスにアタッチ]** ウィンドウで利用できます。  
  
-   **全ユーザーのプロセスを表示する**  
  
     このオプションを選択していない場合、一覧には、現在のユーザーによって所有されているプロセスのみが表示されます。 **[全ユーザーのプロセスを表示する]** を選択すると、一覧には、すべてのユーザーのプロセスが表示されます。  
  
-   **すべてのセッションのプロセスを表示**  
  
     このオプションを選択していない場合、一覧には、現在のセッションのプロセスが表示されます。 このオプションを選択すると、一覧には、すべてのセッションのプロセスが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [概要](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [方法: 実行中のプロセスにアタッチする](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)



