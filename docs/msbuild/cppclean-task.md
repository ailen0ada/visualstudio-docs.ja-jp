---
title: CPPClean タスク | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.cppclean
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), CPPClean task
- CPPClean task (MSBuild (Visual C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 749d60c764f522d188b45b4ecf7302d69b6cd64b
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2018
ms.locfileid: "39179080"
---
# <a name="cppclean-task"></a>CPPClean タスク
Visual C++ プロジェクトのビルド時に MSBuild によって作成される一時ファイルを削除します。 ビルド ファイルを削除するプロセスは、*クリーニング* と呼ばれます。  
  
## <a name="parameters"></a>パラメーター  
 **CPPClean** タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|**DeletedFiles**|省略可能な `ITaskItem[]` 型の出力パラメーターです。<br /><br /> タスクで使用および生成できる MSBuild 出力ファイル項目の配列を定義します。|  
|**DoDelete**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合は、一時ビルド ファイルを消去します。|  
|**FilePatternsToDeleteOnClean**|必須の `String` 型のパラメーターです。<br /><br /> 消去するファイルのファイル拡張子をセミコロンで区切ったリストを指定します。|  
|**FilesExcludedFromClean**|省略可能な `String` 型のパラメーターです。<br /><br /> 消去しないファイルをセミコロンで区切ったリストを指定します。|  
|**FoldersToClean**|必須の `String` 型のパラメーターです。<br /><br /> 消去するディレクトリをセミコロンで区切ったリストを指定します。 完全パスまたは相対パスを指定することができ、パスにはワイルドカード記号 (*) を含めることができます。|  
  
## <a name="see-also"></a>関連項目  
 [タスク リファレンス](../msbuild/msbuild-task-reference.md)