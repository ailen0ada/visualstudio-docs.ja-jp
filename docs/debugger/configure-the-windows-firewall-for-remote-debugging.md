---
title: リモート デバッグ用の Windows ファイアウォールの構成 |Microsoft Docs
ms.custom: ''
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9688948ebe2fa5e045578ee808e068d59450d748
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433392"
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>Windows ファイアウォールをリモート デバッグ用に構成する
このトピックでは、次のオペレーティング システムが稼働するコンピューターでリモート デバッグを有効にするようにファイアウォールを構成する方法を説明します。  
  
-   Windows 10  
  
-   Windows 8/8.1  
  
-   Windows 7   
  
-   Windows Server 2012 R2  

-   Windows Server 2012
  
-   Windows Server 2008 R2 
  
 デバッグを実行するネットワークがファイアウォールで保護されていない場合は、この構成は不要です。 それ以外の場合は、Visual Studio をホストするコンピューターと、デバッグするリモート コンピューターの両方で、ファイアウォール構成を変更する必要があります。  
  
 **IPSec** ネットワークで IPSec を使用して通信を行う必要がある場合は、Visual Studio ホスト コンピューターとリモート コンピューターの両方で追加のポートを開く必要があります。  
  
 **Web サーバー** リモート Web サーバーをデバッグする場合は、リモート コンピューターで追加のポートを開く必要があります。 (Iis でポート 80 開く必要があります。)  
  
 両方のコンピューターで同じオペレーティング システムを実行する必要がないことにご注意ください。 たとえば Visual Studio コンピューターで Windows 10 を実行し、リモート コンピューターで Windows Server 2012 R2 を実行することができます。      
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>リモート デバッグを有効にするリモート コンピューター上のポート  
  
|**ポート**|**着信/発信**|**プロトコル**|**説明**|   
|-|-|-|-|  
|4022|着信|TCP|For VS 2017。 Visual Studio のバージョンごとにポート番号が 2 ずつインクリメントします。 詳細については、次を参照してください。 [Visual Studio Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)します。|  
|4023|着信|TCP|For VS 2017。 Visual Studio のバージョンごとにポート番号が 2 ずつインクリメントします。 (のみに使用されるリモート デバッグ リモート デバッガーの 64 ビット版から 32 ビット プロセスです。)詳細については、次を参照してください。 [Visual Studio Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)します。| 
|3702|発信|UDP|(省略可能)リモート デバッガー探索に必要です。|    
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>Windows ファイアウォールでのポートの構成方法  

Visual Studio またはリモート デバッガーをインストールするときに、ソフトウェアは正しいポートを開くお試しください。 ただし、(サード パーティ製のファイアウォールを使用して) などの一部のシナリオは、手動でポートを開く必要があります。 ポートが開いていることを確認する必要がある場合は、次を参照してください。[トラブルシューティング](#troubleshooting)します。 ポートを開くための手順は、以前のバージョンの Windows で異なる場合があります。

ポートを開く。
  
1. 開く、**開始**メニューで、検索**セキュリティが強化された Windows ファイアウォール**します。

2. クリックして**受信の規則 > 新しい規則 > ポート**、順にクリックします**次**。 (発信ルールでは、選択**送信の規則**代わりにします)。

3. いずれかを選択**TCP**または**UDP**、ポート番号によって異なります。

4. **特定のローカル ポート**をポート番号を入力し、をクリックして**次**します。

5. クリックして**接続を許可する**順にクリックします**次**します。

6. ポートを有効にし、をクリックする 1 つまたは複数のネットワークの種類を選択します。**次**します。

    選ぶ種類には、リモート コンピューターが接続しているネットワークが含まれている必要があります。
7. 名を追加 (たとえば、 **msvsmon**、 **IIS**、または**Web Deploy**) ルールをクリックします**完了**します。

    受信の規則または送信の規則の一覧に新しい規則を表示する必要があります。

## <a name="troubleshooting"></a>トラブルシューティング

リモート デバッガーを使用して、アプリに接続できない場合は、正しいポートが開いていることを確認する必要があります。

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-visual-studio-computer"></a>ポートが、Visual Studio コンピューター上の Windows ファイアウォールで開いていることを確認します。  
 オペレーティング システムによって、Windows ファイアウォールの構成手順は多少異なります。 Windows 8 または 8.1、Windows 10、および Windows Server 2012、単語の**アプリ**が使用されます。 Windows 7 または Windows Server 2008、単語の**プログラム**が使用されます。 次の手順では、word を使用**アプリ**します。  
  
1.  [Windows ファイアウォール] ページを開きます。 ( **[スタート]** メニューの検索ボックスに「 **Windows ファイアウォール**」と入力します)。  
  
2.  **[Windows ファイアウォールを介したアプリまたは機能を許可]** をクリックします。  
  
3.  **[許可されたアプリおよび機能]** の一覧で **[Visual Studio リモート デバッガー探索]** を見つけます。 一覧にこの項目が表示されている場合は、この項目が選択されていることと、1 つ以上のネットワークの種類も選択されていることを確認します。  
  
4.  **[Visual Studio リモート デバッガー探索]** が一覧に表示されていない場合は **[別のアプリの許可]** をクリックします。 まだ表示されない場合で、**アプリの追加**ウィンドウで、をクリックして**参照**に移動します **\<Visual Studio インストール ディレクトリ > \Common7\IDE\Remote Debugger**. アプリケーションの該当するフォルダー (x86、x64、Appx) を見つけ、 **msvsmon.exe**を選びます。 次に、 **[追加]** をクリックします。  
  
5.  **許可されたアプリおよび機能**一覧で、 **Visual Studio リモート デバッガー**します。 リモート デバッグ モニターの通信に使用する 1 つ以上のネットワークの種類 (**[ドメイン]、[ホーム/社内 (プライベート)]、[パブリック]**) をオンにします。 選択する種類には、Visual Studio コンピューターが接続しているネットワークが含まれている必要があります。 

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-remote-computer"></a>ポートがリモート コンピューター上の Windows ファイアウォールで開いていることを確認します。  
 リモート デバッグ コンポーネントをリモート コンピューターにインストールするか、または共有ディレクトリから実行することができます。 いずれの場合でも、リモート コンピューターのファイアウォールを構成する必要があります。 リモート デバッグ コンポーネントは次の場所にあります。  
  
 **\<Visual Studio のインストール ディレクトリ > \Common7\IDE\Remote Debugger**  
  
 オペレーティング システムによって、Windows ファイアウォールの構成手順は多少異なります。 Windows 8 または 8.1、Windows 10、および Windows Server 2012、単語の**アプリ**が使用されます。 Windows 7 または Windows Server 2008、単語の**プログラム**が使用されます。 次の手順では、word を使用**アプリ**します。  
  
1.  [Windows ファイアウォール] ページを開きます。 ( **[スタート]** メニューの検索ボックスに「 **Windows ファイアウォール**」と入力します。)  
  
2.  **[Windows ファイアウォールを介したアプリまたは機能を許可]** をクリックします。  
  
3.  **許可されたアプリおよび機能**ボックスの一覧で探します**Visual Studio リモート デバッガー**します。 一覧にこの項目が表示されている場合は、この項目が選択されていることと、1 つ以上のネットワークの種類も選択されていることを確認します。  
  
4.  場合**Visual Studio リモート デバッガー**が一覧にない場合、をクリックして**別のアプリを許可する**します。 まだ表示されない場合で、**アプリ ウィンドウを追加**、 をクリックして**参照**に移動します **\<Visual Studio インストール ディレクトリ > \Common7\IDE\Remote Debugger**. アプリケーションの該当するフォルダー (x86、x64、Appx) を見つけ、 **msvsmon.exe**を選びます。 次に、 **[追加]** をクリックします。  
  
5.  **許可されているアプリ**一覧で、 **Visual Studio リモート デバッガー**します。 リモート デバッグ モニターの通信に使用する 1 つ以上のネットワークの種類 (**[ドメイン]、[ホーム/社内 (プライベート)]、[パブリック]**) をオンにします。 選択する種類には、Visual Studio コンピューターが接続しているネットワークが含まれている必要があります。 

### <a name="managed-or-native-compatibility-mode-open-additional-ports-on-the-remote-computer"></a>(マネージまたはネイティブ互換モード)リモート コンピューターで追加のポートを開く

デバッガーの互換モードを使用している場合 (**ツール > オプション > デバッグ**)、追加のポートが開かれている必要があります。 互換性モードは、レガシ バージョンのデバッガーを使用して、別のポートが必要です。

> [!NOTE]
> レガシ バージョンのデバッガーは、Visual Studio 2010 のデバッガーです。
  
|**ポート**|**着信/発信**|**プロトコル**|**説明**|  
|-|-|-|-|  
|135、139、445|発信|TCP|必須。|  
|137、138|発信|UDP|必須。|  
|500、4500|発信|UDP|ドメイン ポリシーで、ネットワーク通信を IPSec 経由で実行する必要がある場合は、必須。|  
|80|発信|TCP|Web サーバーのデバッグに必要。|
  
## <a name="see-also"></a>関連項目  
 [Remote Debugging](../debugger/remote-debugging.md)