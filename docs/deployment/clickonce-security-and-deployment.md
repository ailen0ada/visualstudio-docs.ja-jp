﻿---
title: ClickOnce のセキュリティと展開 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70c90d70af60b6bd1f2399847447c1d49785ebb0
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078427"
---
# <a name="clickonce-security-and-deployment"></a>ClickOnce のセキュリティと配置
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 展開テクノロジをインストールして最小限のユーザーとのやり取りを実行できる自己更新型の Windows ベースのアプリケーションを作成することができます。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 発行および Visual Basic および Visual c# でプロジェクトを開発する場合は、ClickOnce テクノロジで配置されたアプリケーションを更新するためには、完全にサポートを提供します。 Visual C アプリケーションを展開する方法の詳細については、次を参照してください。 [Visual c アプリケーションの ClickOnce 配置](/cpp/ide/clickonce-deployment-for-visual-cpp-applications)します。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 展開は、展開における 3 つの主な問題を克服します。  
  
-   **アプリケーションの更新中における問題。** Microsoft Windows インストーラーの展開でアプリケーションが更新されるたびにユーザーが msp ファイルでは、更新プログラムをインストールしてインストールされた製品に適用します。[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開、更新プログラムを自動的に提供することができます。 アプリケーションの変更された部分のみがダウンロードされ、更新されたアプリケーションの全体はサイド バイ サイドの新しいフォルダーから再インストールされます。  

-   **ユーザーのコンピューターに及ぼす影響。** Windows インストーラーの展開、多くの場合、アプリケーションはバージョン管理の競合が発生する可能性を伴うの共有コンポーネントに依存しています。[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開、各アプリケーションは自己完結型、およびその他のアプリケーションに干渉することはできません。  
  
-   **セキュリティ アクセス許可。** Windows インストーラーの展開は、管理者権限を必要とし、限られたユーザーにのみインストールが制限されます。[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開は管理者権限をもたないユーザーにもインストールを可能とさせ、アプリケーションに必要なコード アクセス セキュリティのアクセス許可のみを付与します。  
  
 以前は、これらの問題が原因で、開発者のインストールの容易にするための豊富なユーザー インターフェイスを犠牲にして、Windows ベースのアプリケーションでの代わりに Web アプリケーションを作成することもありました。 使用してデプロイされたアプリケーションを使用して[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]、両方のテクノロジの長所があることができます。  
  
## <a name="what-is-a-clickonce-application"></a>ClickOnce アプリケーションとは何ですか。  
 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションは、Windows Presentation Foundation (*.xbap*)、Windows フォーム (*.exe*)、コンソール アプリケーション (*.exe*)、または Office ソリューション (*.dll*) を使用してパブリッシュ[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]テクノロジ。 発行することができます、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 3 つの異なる方法でアプリケーション: Web ページから、ネットワーク ファイル共有の場合、または CD-ROM などのメディアから。 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションをエンドユーザーのコンピューターにインストールされているし、コンピューターがオフライン、またはエンドユーザーのコンピューターにインストールせず、オンライン専用モードで実行できる場合でもローカルで実行できます。 詳細については、次を参照してください。 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)します。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは、自己更新できます。使用可能になるし、自動的に更新済みのファイルを置き換える新しいバージョンが確認できます。 開発者は、更新プログラムの動作を指定できます。ネットワーク管理者が制御できますも更新方法、たとえば、更新を必須としてマークします。 また、エンドユーザーまたは管理者によって更新プログラムを以前のバージョンにロールバックすることもします。 詳細については、次を参照してください。 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)します。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションは、分離性、インストールや実行、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションは、既存のアプリケーションを中断できません。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは自己完結型です。各[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションにインストールされ、セキュリティで保護されたユーザー、アプリケーションごとのキャッシュから実行します。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは、インターネットまたはイントラネット セキュリティ ゾーンで実行されます。 必要に応じて、アプリケーションは、管理者特権でのセキュリティのアクセス許可を要求できます。 詳細については、次を参照してください。 [ClickOnce のセキュリティで保護されたアプリケーション](../deployment/securing-clickonce-applications.md)します。  
  
## <a name="how-clickonce-security-works"></a>ClickOnce のセキュリティのしくみ  
 コア[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]セキュリティ証明書、コード アクセス セキュリティ ポリシー、および ClickOnce 信頼プロンプトに基づきます。  
  
### <a name="certificates"></a>証明書  
 Authenticode 証明書を使用して、アプリケーションの発行元の信頼性を確認します。 Authenticode を使用すると、アプリケーションの展開、ClickOnce、確立された信頼できるソースからの正規のプログラムとして団体自体から有害なプログラムを防止に役立ちます。 必要に応じて、証明書が、アプリケーションに署名することもでき、配置のマニフェスト ファイルが改ざんされていないことを証明するためにします。 詳細については、次を参照してください。 [ClickOnce と Authenticode](../deployment/clickonce-and-authenticode.md)します。 証明書は、信頼された発行元のリストを取得してクライアント コンピューターの構成にも使用できます。 信頼された発行元からアプリケーションの場合は、ユーザーが介入せずインストールできます。 詳細については、次を参照してください。[信頼されたアプリケーション展開の概要](../deployment/trusted-application-deployment-overview.md)します。  
  
### <a name="code-access-security"></a>コード アクセス セキュリティ  
 コード アクセス secrity では、コードの保護されたリソースにアクセス権を制限できるようにします。 ほとんどの場合は、アクセス許可を制限するインターネットまたはローカル イントラネット ゾーンを選択できます。 使用して、**セキュリティ**ページで、 **ProjectDesigner**アプリケーションの適切なゾーンを要求します。 エンド ユーザー エクスペリエンスをエミュレートするために、制限されたアクセス許可を持つアプリケーションをデバッグすることもできます。 詳細については、「[ClickOnce アプリケーションのコード アクセス セキュリティ](../deployment/code-access-security-for-clickonce-applications.md)」を参照してください。  
  
### <a name="clickonce-trust-prompt"></a>ClickOnce 信頼プロンプト  
 アプリケーションでは、ゾーン以上のアクセス許可を要求している場合、エンドユーザーが信頼の決定を行うメッセージが表示できます。 Windows フォーム アプリケーション、Windows Presentation Foundation アプリケーション、コンソール アプリケーション、XAML ブラウザー アプリケーション、および Office ソリューションなどの ClickOnce アプリケーションが信頼して実行できるかどうか、エンドユーザーを決定できます。 詳細については、次を参照してください。[方法: ClickOnce 信頼プロンプトの動作を構成する](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)します。  
  
## <a name="how-clickonce-deployment-works"></a>ClickOnce 配置の動作  
 コア[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開アーキテクチャは 2 つの XML マニフェスト ファイルに基づいて: アプリケーション マニフェストと配置マニフェスト。 ファイルは、記述から ClickOnce アプリケーションがインストールされている、更新方法、および更新されたときに使用されます。  
  
### <a name="publish-clickonce-applications"></a>ClickOnce アプリケーションを発行します。  
 アプリケーション マニフェストには、アプリケーション自体がについて説明します。 これには、アセンブリ、依存関係と、アプリケーション、必要なアクセス許可、および更新プログラムを利用できる場所を構成するファイルが含まれます。 アプリケーション開発者は Visual Studio またはマニフェストの生成および編集ツールで発行ウィザードを使用してアプリケーション マニフェストを作成 (*Mage.exe*) で、[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]します。 詳細については、次を参照してください。[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)します。  
  
 配置マニフェストでは、アプリケーションを展開する方法について説明します。 これには、アプリケーション マニフェストの場所とクライアントで実行するアプリケーションのバージョンが含まれます。  
  
### <a name="deploy-clickonce-applications"></a>ClickOnce アプリケーションを展開します。  
 作成した後、配置マニフェストは、配置場所にコピーされます。 Web サーバー、ネットワーク ファイル共有、または CD などのメディアを使用できます。 アプリケーション マニフェストとアプリケーションのすべてのファイルも、配置マニフェストで指定されている配置場所にコピーします。 これは、配置場所として同じであることができますか、別の場所であることができます。 使用する場合、**発行ウィザード**Visual Studio で、コピー操作は自動的に実行します。  
  
### <a name="install-clickonce-applications"></a>ClickOnce アプリケーションをインストールします。  
 配置場所にデプロイすると、後に、エンドユーザーはダウンロードして、Web ページまたはフォルダーに配置マニフェスト ファイルを表すアイコンをクリックして、アプリケーションをインストールできます。 ほとんどの場合、どのインストールが進行し、その他の介入なしにアプリケーションを起動した後、インストールを確認するユーザーに確認する簡単なダイアログ ボックスで、エンドユーザーが表示されます。 高度な権限、またはアプリケーションが信頼された証明書によって署名されていないかどうか、アプリケーションが必要な場合、ダイアログ ボックスは、インストールを続行する前に、アクセス許可を付与するユーザーも確認します。 ClickOnce のインストールには、ユーザー数は、管理者特権が必要な前提条件がある場合は、アクセス許可の昇格が必要あります。 管理者特権でのアクセス許可の詳細については、次を参照してください。 [ClickOnce のセキュリティで保護するアプリケーション](../deployment/securing-clickonce-applications.md)します。  
  
 証明書信頼できる、マシンまたはエンタープライズ レベルで信頼された証明書で署名された ClickOnce アプリケーションをサイレント モードでインストールできるようにします。 信頼された証明書の詳細については、次を参照してください。[信頼されたアプリケーション展開の概要](../deployment/trusted-application-deployment-overview.md)します。  
  
 ユーザーのアプリケーションを追加することができます**開始**メニューおよび、**プログラム追加と削除**グループにおいて、**コントロール パネルの**です。 その他の展開テクノロジとは異なりは何も追加する、 **Program Files**フォルダーや、レジストリの管理者権限がありませんは、インストールに必要な  
  
> [!NOTE]
>  アプリケーションに追加されるを防止することも、**開始**メニューと**プログラム追加と削除**グループ、Web アプリケーションのように動作可能になります。 詳細については、次を参照してください。 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)します。  
  
### <a name="update-clickonce-applications"></a>ClickOnce アプリケーションを更新します。  
 新しいアプリケーション マニフェストを生成し、配置場所にファイルをコピー アプリケーション開発者は、アプリケーションの更新バージョンを作成するときに、通常は、元のアプリケーションの展開フォルダーの兄弟フォルダー。 管理者は、アプリケーションの新しいバージョンの場所を指す配置マニフェストを更新します。  
  
> [!NOTE]
>  **発行ウィザード**Visual Studio では、次の手順を使用できます。  
  
 配置マニフェストには、配置場所だけでなく、アプリケーションが更新されたバージョンをチェックする更新場所 (Web ページまたはネットワーク ファイル共有) も含まれます。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] **発行**プロパティを使用して、アプリケーションの更新プログラムを確認するタイミングと頻度を指定します。 配置マニフェストで更新プログラムの動作を指定するかをして、アプリケーションのユーザー インターフェイスにユーザーの選択肢として提示する、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Api。 さらに、**発行**または以前のバージョンにロールバックする更新プログラムを必須にするのには、プロパティを採用されていることができます。 詳細については、次を参照してください。 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)します。  
  
### <a name="third-party-installers"></a>サード パーティ製のインストーラー  
 アプリケーションとサード パーティ製のコンポーネントをインストールする、ClickOnce インストーラーをカスタマイズできます。 再頒布可能パッケージ (.exe または .msi ファイル) があるし、言語に依存しない製品マニフェスト、言語固有のパッケージ マニフェストとパッケージを記述する必要があります。 詳細については、次を参照してください。[ブートス トラップ パッケージを作成する](../deployment/creating-bootstrapper-packages.md)します。  
  
## <a name="clickonce-tools"></a>ClickOnce ツール  
 次の表では、生成、編集、署名、およびアプリケーションと配置マニフェストに再署名に使用できるツールを示します。  
  
|ツール|説明|  
|----------|-----------------|  
|[[セキュリティ] ページ (プロジェクト デザイナー)](../ide/reference/security-page-project-designer.md)|アプリケーションと配置マニフェストを登録します。|  
|[[発行] ページ (プロジェクト デザイナー)](../ide/reference/publish-page-project-designer.md)|生成し、Visual Basic および Visual c# アプリケーションのアプリケーションと配置マニフェストを編集します。|  
|[*Mage.exe* (マニフェスト生成および編集ツール)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|Visual Basic、Visual c#、および Visual C アプリケーションのアプリケーションと配置マニフェストを生成します。<br /><br /> 署名し、アプリケーション マニフェストと配置マニフェストに再署名します。<br /><br /> バッチ スクリプトとコマンド プロンプトから実行できます。|  
|[*MageUI.exe* (マニフェストの生成および編集ツールのグラフィカル クライアント)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|生成し、アプリケーション マニフェストと配置マニフェストを編集します。<br /><br /> 署名し、アプリケーション マニフェストと配置マニフェストに再署名します。|  
|[GenerateApplicationManifest タスク](../msbuild/generateapplicationmanifest-task.md)|アプリケーション マニフェストを生成します。<br /><br /> MSBuild から実行できます。 詳細については、次を参照してください。 [MSBuild リファレンス](../msbuild/msbuild-reference.md)します。|  
|[GenerateDeploymentManifest タスク](../msbuild/generatedeploymentmanifest-task.md)|配置マニフェストを生成します。<br /><br /> MSBuild から実行できます。 詳細については、次を参照してください。 [MSBuild リファレンス](../msbuild/msbuild-reference.md)します。|  
|[SignFile タスク](../msbuild/signfile-task.md)|アプリケーションと配置マニフェストを登録します。<br /><br /> MSBuild から実行できます。 詳細については、次を参照してください。 [MSBuild リファレンス](../msbuild/msbuild-reference.md)します。|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|アプリケーションと配置マニフェストを生成するアプリケーションを開発します。|  
  
 次の表では、これらのブラウザーで ClickOnce アプリケーションをサポートするために必要な .NET Framework バージョンを示します。  
  
|ブラウザー|.NET Framework のバージョン|  
|-------------|----------------------------|  
|Internet Explorer|2.0、3.0、3.5、4、3.5 SP1|  
|Firefox|2.0 SP1 では、3.5 SP1 では、4|  
  
## <a name="see-also"></a>関連項目  
 [Windows Vista の ClickOnce 配置](../deployment/clickonce-deployment-on-windows-vista.md)   
 [ClickOnce アプリケーションを発行します。](../deployment/publishing-clickonce-applications.md)   
 [セキュリティで保護された ClickOnce アプリケーション](../deployment/securing-clickonce-applications.md)   
 [ClickOnce での COM コンポーネントをデプロイします。](../deployment/deploying-com-components-with-clickonce.md)   
 [コマンドラインから ClickOnce アプリケーションを構築します。](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [System.Deployment.Application を使用する ClickOnce アプリケーションをデバッグします。](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)
