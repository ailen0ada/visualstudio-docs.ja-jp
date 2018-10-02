---
title: SupportsLanguageDropDown 要素 (Visual Studio テンプレート) |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e1b7ef96eae30a35c5c06530a787968cfca01e1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544493"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>SupportsLanguageDropDown 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[SupportsLanguageDropDown 要素 (Visual Studio テンプレート)](https://docs.microsoft.com/visualstudio/extensibility/supportslanguagedropdown-element-visual-studio-templates)します。  
  
Web 項目テンプレートが複数の言語と同じかどうかと、かどうかを指定します、**言語**のオプションが有効になっている、**新しい項目の追加** ダイアログ ボックス。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<SupportsLanguageDropDown >  
  
## <a name="syntax"></a>構文  
  
```  
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必須の要素です。<br /><br /> テンプレートをカテゴリに分類し、 **[新しいプロジェクト]** ダイアログ ボックス、または **[新しい項目の追加]** ダイアログ ボックスでどのように表示させるかを定義します。|  
  
## <a name="text-value"></a>テキスト値  
 テキスト値が必要です。  
  
 テキストがいずれかにする必要があります`true`または`false`ことを示すかどうか、**言語**オプションはから利用可能な**新しい項目の追加** ダイアログ ボックス。  
  
## <a name="remarks"></a>Remarks  
 `SupportsLanguageDropDown` は、省略可能な要素です。 既定値は `false` です。  
  
 `SupportsLanguageDropDown`要素は、Web 項目テンプレートの使用のみ。  
  
 この要素の値が設定されている場合`true`、項目テンプレートはすべてのプログラミング言語と同じ、**言語**でオプションが有効になっている、**新しい項目の追加** ダイアログ ボックス。 このオプションでは、テンプレートから作成する新しい項目のプログラミング言語を選択することができます。  
  
## <a name="example"></a>例  
 次の例を表示するように指定します、**言語**オプションをドロップダウンします。  
  
```  
<VSTemplate Version="3.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)
