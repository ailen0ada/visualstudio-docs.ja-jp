---
title: CreateExpInstance ユーティリティ |Microsoft Docs
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
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9b08ba5ac68a09f6c44937634375add3065e5e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537303"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance ユーティリティ
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CreateExpInstance ユーティリティ](https://docs.microsoft.com/visualstudio/extensibility/internals/createexpinstance-utility)します。  
  
リセットするを作成するには、CreateExpInstance ユーティリティを使用するか、Visual Studio の実験用インスタンスを削除します。 実験用インスタンスを使用して、デバッグおよび基になる製品を変更することがなく Visual Studio 拡張機能をテストすることができます。  
  
## <a name="syntax"></a>構文  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>パラメーター  
 /作成します。  
 実験用インスタンスを作成します。  
  
 /リセットします。  
 実験用のインスタンスを削除し、新しく作成します。  
  
 /Clean  
 実験用インスタンスを削除します。  
  
 /VSInstance  
 コピーする基本の Visual Studio インスタンスが含まれているディレクトリの名前。  
  
 /RootSuffix  
 実験用インスタンス ディレクトリの名前に付加するサフィックス。  
  
## <a name="remarks"></a>Remarks  
 Visual Studio 拡張機能を使用しているときに既定の実験用インスタンスを開き、現在の拡張機能をインストールして F5 キーを押します。 実験用インスタンスが使用できない場合、既定の設定である Visual Studio を作成します。  
  
 実験用インスタンスの既定の場所は、Visual Studio のバージョン番号に依存します。 たとえば、Visual Studio 2015 で、場所は、%localappdata%\Microsoft\VisualStudio\14.0Exp\ ディレクトリの場所のすべてのファイルがそのインスタンスの一部と見なされます。 既定の場所にディレクトリ名が変更されない限り、任意の追加の実験用インスタンスは Visual Studio によって読み込まれません。  
  
 Visual Studio 実験用インスタンスを開くときに、システム レジストリにアクセスしません。 これは、レジストリ ハイブの実験用のバージョンを使用すると、Visual Studio の以前のバージョンによって異なります。  
  
 CreateExpInstance ユーティリティには、VsRegEx ユーティリティが置き換えられます。  
  
 次の例では、Visual Studio の既定の実験用インスタンスをリセットします。  
  
 **CreateExpInstance.exe/Reset/VSInstance = 14.0/RootSuffix Exp を =**  
  
## <a name="see-also"></a>関連項目  
 [製品のリリース](../../misc/releasing-a-visual-studio-integration-product.md)

