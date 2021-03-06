---
title: プロジェクトのコマンドの処理を実装する入れ子になった |Microsoft Docs
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
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea27ea6f1b1ef49174b555fb9b1aae0d4c54dd23
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548792"
---
# <a name="implementing-command-handling-for-nested-projects"></a>入れ子になったプロジェクト向けのコマンド処理の実装
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[コマンドは入れ子になったプロジェクトの処理を実装する](https://docs.microsoft.com/visualstudio/extensibility/internals/implementing-command-handling-for-nested-projects)します。  
  
IDE が経由で渡されるコマンドを渡すことができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>と<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスを入れ子になったプロジェクト、または親プロジェクトには、フィルター処理またはコマンドをオーバーライドできます。  
  
> [!NOTE]
>  親プロジェクトによって処理される通常のコマンドのみをフィルター処理できます。 などのコマンド**ビルド**と**デプロイ**によって処理される IDE をフィルター処理することはできません。  
  
 次の手順では、コマンドの処理を実装するプロセスについて説明します。  
  
## <a name="procedures"></a>手順  
  
#### <a name="to-implement-command-handling"></a>コマンドの処理を実装するには  
  
1.  選択すると、ユーザー、入れ子になったプロジェクトまたはノードで入れ子になったプロジェクト。  
  
    1.  IDE の呼び出し、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッド。  
  
     または  
  
    1.  ソリューション エクスプローラで、ショートカット メニュー コマンドなどの階層ウィンドウで、コマンドが作成された場合は、IDE を呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>プロジェクトの親のメソッド。  
  
2.  親プロジェクトに渡されるパラメーターを調べることができます`QueryStatus`など`pguidCmdGroup`と`prgCmds`親プロジェクトで、コマンドをフィルター処理する必要があるかどうかを決定します。 親プロジェクトは、コマンドをフィルター処理を実装する場合は、設定する必要があります。  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     親プロジェクトを返す必要があります`S_OK`します。  
  
     親プロジェクトのコマンドは、フィルター処理しないかどうか、これだけを返します`S_OK`します。 この場合、IDE は、子プロジェクトに対してコマンドを自動的にルーティングします。  
  
     親プロジェクトは、子プロジェクトに対して、コマンドをルーティングする必要はありません。 IDE は、このタスクを実行します.  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [コマンド、メニューのおよびツールバー](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [入れ子になったプロジェクト](../../extensibility/internals/nesting-projects.md)

