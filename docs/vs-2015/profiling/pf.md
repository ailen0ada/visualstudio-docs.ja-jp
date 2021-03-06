---
title: PF | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ba9558683311d77742b89a4ae4841ed5b7d8511
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534825"
---
# <a name="pf"></a>PF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[PF](https://docs.microsoft.com/visualstudio/profiling/pf)します。  
  
VSPerfCmd.exe の **PF** オプションは、サンプリングするプロファイル イベントをページ フォールトに設定し、必要に応じて、サンプリング間隔のページ フォールト数を既定の 10 から変更します。  
  
> [!NOTE]
>  PF を 64 ビット システムで使用することはできません。  
  
 **注: PF** は 64 ビット コンピューターではサポートされていません。**PF** は、**Launch** オプションまたは **Attach** オプションも含むコマンド ラインでのみ使用できます。  
  
 既定では、サンプリング イベントはプロセッサのクロック サイクル (停止なし) に設定され、サンプリング間隔は 10,000,000 に設定されます。 **Timer**、**PF**、**Sys**、**Counter** の各オプションを使用すると、サンプリング イベントおよびサンプリング間隔を設定できます。 **GC** オプションは、割り当ておよびガベージ コレクション イベントが発生するたびに、.NET メモリ データを収集します。 コマンド ラインには、上記のオプションのいずれか 1 つだけを指定できます。  
  
 サンプリング イベントおよびサンプリング間隔は、**Launch** または **Attach** オプションを含む最初のコマンド ラインでのみ設定できます。  
  
## <a name="syntax"></a>構文  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### <a name="parameters"></a>パラメーター  
 `Events`  
 サンプリング間隔でのページ フォールト イベント数を指定する整数値。 ‎`Events` が指定されていない場合、間隔は 10 に設定されます。  
  
## <a name="required-options"></a>必須オプション  
 **PF** は、次のオプションのいずれかを含むコマンド ラインでのみ指定できます。  
  
 **Launch:** `AppName`  
 プロファイラーと、AppName で指定されたアプリケーションを起動します。  
  
 **Attach:** `PID`  
 プロファイラーを AppName で指定されたプロセスにアタッチします。  
  
## <a name="invalid-options"></a>無効なオプション  
 以下のオプションは、**PF** と同じコマンド ラインでは指定できません。  
  
 **Timer**[**:**`Cycles`]  
 サンプリング イベントをプロセッサのクロック サイクルに設定し、必要に応じてサンプリング間隔を `Cycles` に設定します。 既定の Timer 間隔は 10,000,000 です。  
  
 **Sys**[**:**`Events`]  
 サンプリング イベントを、プロファイリングされたアプリケーションからオペレーティング システムのカーネル (syscalls) への呼び出しに設定し、必要に応じて、サンプリング間隔を `Events` に設定します。 既定の Sys 間隔は 10 です。  
  
 **Counter:** `Name`[`,Reload`[`,FriendlyName`]]  
 サンプリング イベントを、`Name` で指定された CPU パフォーマンス カウンターに設定し、サプリング間隔を `Reload` に設定します。  
  
 **GC**[**:**{**Allocation**&#124;**Lifetime**}]  
 .NET メモリ データを収集します。 既定 (**Allocation**) では、データはメモリの割り当てイベントごとに収集されます。 **Lifetime** パラメーターが指定されている場合、ガベージ コレクション イベントごとのデータも収集されます。  
  
## <a name="example"></a>例  
 この例では、プロファイリング サンプル イベントをページ フォールトに設定し、サンプリング間隔を 20 のページ フォールトに設定する方法を示します。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## <a name="see-also"></a>関連項目  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング (サービスの)](../profiling/command-line-profiling-of-services.md)



