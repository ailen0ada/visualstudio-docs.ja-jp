---
title: MoreInfoURL 要素 (VSIX 言語パックのスキーマ) |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3f07b67b-95c5-4ae8-8b7e-d643cbbb0348
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fac097d749dd743898882deff5e909e455698b0f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547596"
---
# <a name="moreinfourl-element-vsix-language-pack-schema"></a>MoreInfoURL 要素 (VSIX 言語パックのスキーマ)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[MoreInfoURL 要素 (VSIX 言語パックのスキーマ)](https://docs.microsoft.com/visualstudio/extensibility/moreinfourl-element-vsix-language-pack-schema)します。  
  
任意。 拡張機能のローカライズされた情報へのリンク。  
  
## <a name="syntax"></a>構文  
  
```  
<MoreInfoURL>URL</MoreInfoURL>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|なし||  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|なし||  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[VSIX LanguagePack 要素](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|必須。 VSIX 言語パックのルート要素を提供します。|  
  
## <a name="text-value"></a>テキスト値  
 任意。 Web サイトへのリンク。 リンクは、テキスト文字列です。  
  
## <a name="element-information"></a>要素情報  
  
|||  
|-|-|  
|名前空間|http://schemas.microsoft.com/developer/vsx-schema-lp/2010|  
|スキーマ名|VSIX 言語パックのスキーマ|  
|検証ファイル|VSIXLanguagePackSchema.xsd|  
|空にすることができます。|利用不可|  
  
## <a name="see-also"></a>関連項目  
 [VSX 言語パックのスキーマ リファレンス](../extensibility/vsx-language-pack-schema-reference.md)   
 [VSIX パッケージのローカライズ](../extensibility/localizing-vsix-packages.md)   
 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)

