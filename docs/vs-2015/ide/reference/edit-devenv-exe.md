---
title: -Edit (devenv.exe) | Microsoft Docs
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
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b61e79561d8bf2ae6bd456ad4ac91ea684491ed5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548985"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[の編集 (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/edit-devenv-exe)します。  
  
  
指定されたファイルを [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の既存のインスタンスで開きます。  
  
## <a name="syntax"></a>構文  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## <a name="arguments"></a>引数  
 `file1`  
 任意。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の既存のインスタンスで開くファイル。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] のインスタンスが存在していない場合は、簡略化されたウィンドウ レイアウトで新しいインスタンスが作成され、新しいインスタンスで `file1` が開かれます。  
  
 `file2`  
 任意。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の既存インスタンスで開く 1 つ以上の追加ファイル。  
  
## <a name="remarks"></a>Remarks  
 ファイルが指定されておらず、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の既存のインスタンスがある場合は、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の既存のインスタンスがフォーカスを取得します。 ファイルが指定されておらず、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の既存のインスタンスがない場合は、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の新しいインスタンスが簡略化されたウィンドウ レイアウトで作成されます。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の既存のインスタンスがモーダル状態の場合 (たとえば、[[オプション] ダイアログ ボックス](../../ide/reference/options-dialog-box-visual-studio.md)が開かれている場合)、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] がモーダル状態を終了すると、ファイルが既存のインスタンスで開かれます。  
  
## <a name="example"></a>例  
 この例では、ファイル `MyFile.cs` が [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の既存インスタンスで開かれるか、またはインスタンスがまだ存在しない場合は [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の新しいインスタンスでファイルが開かれます。  
  
```  
devenv /edit MyFile.cs  
```  
  
## <a name="see-also"></a>関連項目  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)



