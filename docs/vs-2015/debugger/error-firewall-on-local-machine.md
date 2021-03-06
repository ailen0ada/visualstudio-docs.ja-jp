---
title: 'エラー: ローカル コンピューターでファイアウォールの設定 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.firewall.localmachine
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f4cee2d391038c9157666078c6fd83027bc35e6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548660"
---
# <a name="error-firewall-on-local-machine"></a>エラー : ローカル コンピューターのファイアウォール
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[エラー: ローカル コンピューターのファイアウォール](https://docs.microsoft.com/visualstudio/debugger/error-firewall-on-local-machine)します。  
  
Visual Studio を実行するローカル コンピューターのインターネット接続ファイアウォールは、リモート デバッグを許可するように設定されていません。 既定のトランスポートを使用したマネージド リモート デバッグまたはネイティブ リモート デバッグでは、DCOM トラフィック用に TCP 135 ポートを開く必要があります。 ファイルおよびプリンターの共有を有効にし、devenv.exe を例外リストに追加することも必要です。 また、IPSEC ポートを開く必要がある場合もあります。  
  
 詳細については、次を参照してください。[設定 Up the Remote Tools のデバイスで](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)します。



