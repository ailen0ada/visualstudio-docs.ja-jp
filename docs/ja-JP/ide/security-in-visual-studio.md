---
title: Visual Studio におけるセキュリティ
ms.date: 02/17/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74e557fd0e92742f33c25d68862ae15254104963
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="security-in-visual-studio"></a>Visual Studio におけるセキュリティ

セキュリティについては、設計から配置まで、アプリケーション開発のあらゆる段階で考慮する必要があります。 まず、Visual Studio をできるだけ安全に実行します。 [ユーザー アクセス許可](../ide/user-permissions-and-visual-studio.md)に関するページを参照してください。

 安全なアプリケーションを効果的に開発するためには、セキュリティの概念と、開発対象となるプラットフォームのセキュリティ機能について、基本事項を理解しておく必要があります。 さらに、安全なコーディング技法を身に付ける必要もあります。

## <a name="understand-security"></a>セキュリティについて
 [セキュリティ](/dotnet/standard/security/index) .NET Framework のコード アクセス セキュリティ、ロール ベース セキュリティ、セキュリティ ポリシー、およびセキュリティ ツールについて説明します。

 [コードを守るためにすべての開発者が知る必要のある、セキュリティに関するヒント上位 10 項目](http://go.microsoft.com/fwlink/?LinkId=72877) データまたはシステムに対する攻撃を防ぐために注意しなければならない問題について説明します。

## <a name="code-for-security"></a>セキュリティに配慮したコード
 セキュリティ脆弱性の原因となるコーディング エラーのほとんどは、ユーザー入力に対する根拠のない仮定や、開発対象のプラットフォームに対する不十分な知識に起因しています。

 [安全なコーディングのガイドライン](/dotnet/standard/security/secure-coding-guidelines) セキュリティ問題に対処するためのコンポーネント分類ガイドラインを示します。

 [セキュリティ推奨事項](/cpp/top/security-best-practices-for-cpp) バッファー オーバーランと、Microsoft Visual C++ のセキュリティ チェック機能の詳細について説明します。この機能は、コンパイル時に /GS フラグを指定することによって利用できます。

## <a name="build-for-security"></a>セキュリティに配慮したビルド
 セキュリティはビルド プロセスでも重要な考慮事項です。  いくつかの追加手順で、展開するアプリのセキュリティを改善し、不正なリバース エンジニアリング、なりすましなどの攻撃を防ぐことができます。

 [Dotfuscator Community Edition (CE)](dotfuscator/index.md) 無料の PreEmptive Protection - Dotfuscator Community Edition を設定し、使用を開始して .NET アセンブリをリバース エンジニアリングと不正使用 (不正なデバッグなど) から保護する方法について説明します。

 [アセンブリおよびマニフェストへの署名の管理](managing-assembly-and-manifest-signing.md) 厳密な名前の署名について説明します。厳密な名前の署名を使用すると、ソフトウェア コンポーネントを一意に識別し、名前のなりすましを防ぐことができます。