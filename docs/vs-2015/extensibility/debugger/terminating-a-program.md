---
title: プログラムの終了 |Microsoft Docs
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
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6092e7f393eb973980cfca123264326aa0b2388b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545121"
---
# <a name="terminating-a-program"></a>プログラムの終了
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[プログラムの終了](https://docs.microsoft.com/visualstudio/extensibility/debugger/terminating-a-program)します。  
  
1 つのスレッドで 1 つのプログラムの終了の説明を次に示します。  
  
## <a name="termination-process"></a>終了プロセス  
  
1.  DE 送信、 [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)有効な[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)します。  
  
2.  DE 送信、 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)有効な[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)します。  
  
 IDE は、デザイン モードに入ります。 デバッグ エンジンまたはランタイム環境は[IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)ポートからプログラムを削除します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのイベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)

