---
title: ClickOnce アプリケーションのローカライズ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, ClickOnce applications
- ClickOnce deployment, globalization
- deploying applications [ClickOnce], localizing ClickOnce applications
- localization, ClickOnce deployment
- ClickOnce deployment, download on-demand
- ClickOnce deployment, localization
- Windows Forms, ClickOnce applications
- console applications, ClickOnce applications
ms.assetid: c92b193b-054d-4923-834b-d4226a4c7a1a
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 285c1273114fe7f59b2ee0bb6bc612d18cbaf32e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536792"
---
# <a name="localizing-clickonce-applications"></a>ClickOnce アプリケーションのローカライズ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ClickOnce アプリケーションのローカライズ](https://docs.microsoft.com/visualstudio/deployment/localizing-clickonce-applications)します。  
  
ローカライズは、アプリケーションを特定のカルチャに適したものにするためのプロセスです。 このプロセスには、ユーザー インターフェイス (UI) のテキストを地域固有の言語に翻訳する作業、正しい日付と通貨の書式の適用、フォーム上にあるコントロールのサイズの調整、およびコントロールを右から左へとミラー化する作業 (必要な場合) が含まれます。  
  
 アプリケーションをローカライズすると、1 つ以上のサテライト アセンブリが作成されます。 各アセンブリには、特定のカルチャに固有の UI 文字列、画像、およびその他のリソースが含まれます (アプリケーションのメインの実行可能ファイルには、アプリケーションの既定のカルチャに対応する文字列が含まれています)。  
  
 ここでは、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] アプリケーションを他のカルチャ向けに配置する 3 つの方法について説明します。  
  
-   すべてのサテライト アセンブリを 1 つの配置に含める。  
  
-   カルチャごとに 1 つの配置を生成し、それぞれに 1 つのサテライト アセンブリを含める。  
  
-   必要に応じてサテライト アセンブリをダウンロードする。  
  
## <a name="including-all-satellite-assemblies-in-a-deployment"></a>すべてのサテライト アセンブリを 1 つの配置に含める  
 複数の [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 配置を発行するのではなく、すべてのサテライト アセンブリを含む 1 つの [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 配置を発行します。  
  
 これは、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] での既定の方法です。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] でこの方法を使用する場合、追加の作業を実行する必要はありません。  
  
 MageUI.exe でこのメソッドを使用してに、アプリケーションのカルチャを設定する必要があります**ニュートラル**MageUI.exe でします。 次に、すべてのサテライト アセンブリを手動で配置に含める必要があります。 MageUI.exe でを使用してサテライト アセンブリを追加することができます、 **Populate**のボタンでは、**ファイル**アプリケーション マニフェストのタブ。  
  
 この方法の利点は、単一の配置が作成されるので、配置のローカライズが簡素化されることです。 実行時に、ユーザーが使用する Windows オペレーティング システムの既定のカルチャに応じて、適切なサテライト アセンブリが使用されます。 この方法の欠点は、クライアント コンピューターでアプリケーションをインストールまたは更新するたびに、すべてのサテライト アセンブリがダウンロードされることです。 このため、アプリケーションに大量の文字列が含まれている場合や顧客が使用するネットワーク接続の速度が遅い場合は、このプロセスがアプリケーション更新時のパフォーマンスに影響を与える可能性があります。  
  
> [!NOTE]
>  この方法では、それぞれのカルチャで異なるテキスト文字列のサイズに対応するために、コントロールの高さ、幅、および位置をアプリケーションが自動的に調整することを前提としています。 Windows フォームには、容易にローカライズできるフォームをデザインするためのさまざまなコントロールとテクノロジが用意されています。これには、<xref:System.Windows.Forms.FlowLayoutPanel> コントロールと <xref:System.Windows.Forms.TableLayoutPanel> コントロール、および <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティが含まれます。  参照してください[方法: Windows フォームを使用して AutoSize と TableLayoutPanel コントロールでサポート ローカリゼーション](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))します。  
  
## <a name="generate-one-deployment-for-each-culture"></a>カルチャごとに 1 つの配置を生成する  
 この配置ストラテジでは、複数の配置を生成します。 各配置には特定のカルチャに必要なサテライト アセンブリのみを含め、その配置をそのカルチャ固有としてマークします。  
  
 このメソッドを使用する[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、設定、**発行の言語**プロパティを**発行**目的の地域にタブ。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] は、選択した地域に必要なサテライト アセンブリを自動的に組み込み、それ以外のすべてのサテライト アセンブリを配置から除外します。  
  
 この作業は、Microsoft [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] の MageUI.exe ツールを使用して実行することもできます。 使用して、 **Populate**のボタンでは、**ファイル**アプリケーション ディレクトリで、その他のすべてのサテライト アセンブリを除外し、設定、アプリケーション マニフェストのタブ、**カルチャ**フィールドに、**名前**MageUI.exe で配置マニフェスト タブ。 この手順によって、正しいサテライト アセンブリが組み込まれるだけでなく、配置マニフェストに含まれる `assemblyIdentity` 要素の `language` 属性が、対応するカルチャに設定されます。  
  
 アプリケーションを発行した後、アプリケーションがサポートする追加のカルチャごとにこの手順を繰り返す必要があります。 発行するようにして別の Web サーバーのディレクトリまたはファイルの共有ディレクトリに常に、各アプリケーション マニフェストは、さまざまなサテライト アセンブリを参照し、各配置マニフェスト、に別の値になりますので、行う必要があります`language`属性。  
  
## <a name="downloading-satellite-assemblies-on-demand"></a>サテライト アセンブリを必要に応じてダウンロードする  
 すべてのサテライト アセンブリを 1 つの配置に含める場合は、オンデマンド ダウンロードを使用し、サテライト アセンブリをオプションとしてマークすることにより、パフォーマンスを高めることができます。 マークしたアセンブリは、アプリケーションがインストールまたは更新されるときにはダウンロードされません。 これらのアセンブリは、必要になったときに <xref:System.Deployment.Application.ApplicationDeployment> クラスの <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> メソッドを呼び出すことでインストールできます。  
  
 サテライト アセンブリを必要に応じてダウンロードする処理は、その他の種類のアセンブリを必要に応じてダウンロードする処理と若干異なります。 情報とコードの例を使用してこのシナリオを有効にする方法について、[!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)]用ツールの[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]を参照してください[チュートリアル: ClickOnce 配置 API で必要に応じてサテライト アセンブリをダウンロード](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)します。  
  
 このシナリオは、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] で有効にすることもできます。  「 [チュートリアル: デザイナーを使用し、ClickOnce 配置 API で必要に応じてサテライト アセンブリをダウンロードする](http://msdn.microsoft.com/library/ms366788\(v=vs.110\)) 」または「 [チュートリアル: デザイナーを使用し、ClickOnce 配置 API で必要に応じてサテライト アセンブリをダウンロードする](http://msdn.microsoft.com/library/ms366788\(v=vs.120\))」もご覧ください。  
  
## <a name="testing-localized-clickonce-applications-before-deployment"></a>ローカライズされた ClickOnce アプリケーションを配置前にテストする  
 サテライト アセンブリが Windows フォーム アプリケーションに使用されるのは、アプリケーションのメイン スレッドの <xref:System.Threading.Thread.CurrentUICulture%2A> プロパティがそのサテライト アセンブリのカルチャに設定されている場合に限られます。 各地域の顧客は Windows のローカライズ版を既に実行していると考えられるため、カルチャも該当する既定値に設定されているはずです。  
  
 アプリケーションを顧客が使用できるようにする前に、ローカライズされた配置をテストするには、次の 3 つのオプションがあります。  
  
-   [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] アプリケーションを、Windows の該当するローカライズ版で実行する。  
  
-   アプリケーション内で、<xref:System.Threading.Thread.CurrentUICulture%2A> プロパティをプログラムにより設定する (このプロパティは、<xref:System.Windows.Forms.Application.Run%2A> メソッドを呼び出す前に設定する必要があります)。  
  
## <a name="see-also"></a>関連項目  
 [\<assemblyIdentity > 要素](../deployment/assemblyidentity-element-clickonce-deployment.md)   
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [Windows フォームのグローバル化](http://msdn.microsoft.com/library/72f6cd92-83be-45ec-aa37-9cb8e3ebc3c5)



