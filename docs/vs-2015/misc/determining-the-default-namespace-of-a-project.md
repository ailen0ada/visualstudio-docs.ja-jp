---
title: プロジェクトの既定の Namespace を決定する |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: douge
ms.openlocfilehash: 27919985c09356764533e736899dc6a7cb5d0090
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535730"
---
# <a name="determining-the-default-namespace-of-a-project"></a>プロジェクトの既定の名前空間の決定
[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]場合、`CustomToolNamespace`プロパティの値の入力ファイルに設定されます`CustomToolNamespace`に渡される既定の名前空間のパラメーターの値になります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>メソッド。 それ以外の場合、`wszDefaultNamespace`に渡されるパラメーター`Generate`は常にルート名前空間を等しくします。 名前空間の詳細については、次を参照してください。 [Namespace キーワード](http://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b)します。  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] フォルダー ベースの名前空間を使用します。 名前空間は、ルート名前空間とカスタムのツールが含まれるフォルダーの名前で構成されます。 各フォルダー名は有効な識別子に変換され、期間は、すべての名前を区切ります。 たとえば、入力ファイルが FolderA\FolderB\FolderC\MyInput.txt、ルート名前空間が CL9 の場合、計算の既定の名前空間になります**CL9 します。FolderA.FolderB.FolderC**します。  
  
 このルールの例外は、階層チェーンには、Web 参照フォルダーが含まれている場合に発生します。 たとえば場合、。  
  
-   FolderC された Web 参照フォルダーで、名前空間になります**CL9 します。FolderC**します。  
  
-   FolderB された Web 参照フォルダーで、名前空間になります**CL9 します。FolderB.FolderC**します。  
  
 つまり、名前空間は、次の形式を使用します。  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>関連項目  
 [単一ファイル ジェネレーターの実装](../extensibility/internals/implementing-single-file-generators.md)   
 [単一ファイル ジェネレーターの登録](../extensibility/internals/registering-single-file-generators.md)   
 [ビジュアル デザイナーへのタイプの公開](../extensibility/internals/exposing-types-to-visual-designers.md)