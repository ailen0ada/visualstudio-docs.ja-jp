---
title: オートメーション [オプション] ページのサポート |Microsoft Docs
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
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9f7a9a9cf13a50cf13817b4c3b12bd1da1e8370b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536448"
---
# <a name="automation-support-for-options-pages"></a>オプション ページのオートメーションのサポート
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[オートメーションのサポート オプション ページ](https://docs.microsoft.com/visualstudio/extensibility/internals/automation-support-for-options-pages)します。  
  
Vspackage は、ユーザー設定を提供できます**オプション** ダイアログ ボックス、**ツール**メニュー ([ツール オプション] ページ) で[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]し、オートメーション モデルを利用できるようにします。  
  
## <a name="tools-options-pages"></a>ツール オプション ページ  
 作成する、**ツール オプション** ページで、VSPackage の VSPackage の実装により、環境に返されるユーザー コントロールの実装を提供する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>メソッド (またはマネージ コードに対する、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>メソッドの場合)。  
  
 これは省略可、ただし、オートメーション モデルからこの新しいページにアクセスできるように強くお勧めします。 これは、次の手順を行うことができます。  
  
1.  拡張、 <xref:EnvDTE._DTE.Properties%2A> IDispatch から派生したオブジェクトの実装を使用してオブジェクト。  
  
2.  実装を返す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>メソッド (またはマネージ コードに対して、<xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A>メソッド) IDispatch から派生したオブジェクトにします。  
  
3.  Automation の消費者を呼び出すときに、<xref:EnvDTE._DTE.Properties%2A>カスタム メソッド**オプション**プロパティ ページで、環境を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>メソッドは、ユーザー設定を取得する**ツール オプション**ページのオートメーション実装です。  
  
4.  各を提供する VSPackage のオートメーション オブジェクトを使用して<xref:EnvDTE.Property>によって返される<xref:EnvDTE._DTE.Properties%2A>します。  
  
 カスタム ツール オプション ページを実装するサンプルについては、次を参照してください。 [VSSDK のサンプル](../../misc/vssdk-samples.md)します。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト オブジェクトの公開](../../extensibility/internals/exposing-project-objects.md)

