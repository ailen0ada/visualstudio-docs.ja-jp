---
title: 提供されるサービス (ソース管理 VSPackage) |Microsoft Docs
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
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aff288f68f32d3850cfa92d5999febd1c65572e1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544297"
---
# <a name="services-provided-source-control-vspackage"></a>提供されるサービス (ソース管理 VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[サービスの提供 (ソース管理 VSPackage)](https://docs.microsoft.com/visualstudio/extensibility/internals/services-provided-source-control-vspackage)します。  
  
サービスは、Vspackage 間および Visual Studio 統合開発環境 (IDE) と、インストールされている Vspackage 間に共有する機能により、主要なメカニズムです。 サービスと、Visual Studio IDE で、重要度の詳細については、次を参照してください。[を使用すると、サービスを提供する](../../extensibility/using-and-providing-services.md)します。  
  
## <a name="the-source-control-service"></a>ソース管理サービス  
 Visual Studio では、サービス、IDE レベルのサービスおよびパッケージ レベルのサービスの 2 つのレイヤーを提供します。 Visual Studio IDE は、ネイティブ IDE レベルのサービスを提供します。 ソース管理パッケージは、これらのサービスの一部を消費します。 VSPackage としてソース管理パッケージでは、独自の秘密のソース管理サービスを提供することで、ソース管理機能を共有します。 ソース管理パッケージは、Visual Studio IDE で使用できるコントラクトの形式でによって実装されるソース コントロールに関連するインターフェイスのセットをカプセル化します。  
  
## <a name="see-also"></a>関連項目  
 [デザイン要素](../../extensibility/internals/source-control-vspackage-design-elements.md)

