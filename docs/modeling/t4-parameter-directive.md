---
title: T4 パラメーター ディレクティブ
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5425dc16b40495d1a9ab9010ac90fe6b552d02e9
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47858003"
---
# <a name="t4-parameter-directive"></a>T4 パラメーター ディレクティブ

Visual Studio テキスト テンプレートで、`parameter`ディレクティブがテンプレート コードの外部のコンテキストから渡された値から初期化されるプロパティを宣言します。 テキスト変換を呼び出すコードを記述する場合は、これらの値を設定できます。

## <a name="using-the-parameter-directive"></a>パラメーター ディレクティブの使用

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 `parameter`ディレクティブがテンプレート コードの外部のコンテキストから渡された値から初期化されるプロパティを宣言します。 テキスト変換を呼び出すコードを記述する場合は、これらの値を設定できます。 いずれかの値を渡すことができます、`Session`ディクショナリ、または<xref:System.Runtime.Remoting.Messaging.CallContext>します。

 任意のリモート処理可能な型のパラメーターを宣言することができます。 型を宣言する必要があります<xref:System.SerializableAttribute>、またはそれから派生する必要があります、<xref:System.MarshalByRefObject>します。 これにより、テンプレートを処理する AppDomain に渡されるパラメーターの値です。

 たとえば、次の内容をテキスト テンプレートを記述できます。

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>

```

## <a name="passing-parameter-values-to-a-template"></a>テンプレートにパラメーター値を渡す
 メニュー コマンドやイベント ハンドラーなどの Visual Studio 拡張機能を作成する場合は、テキスト テンプレート サービスを使用してテンプレートを処理できます。

```csharp
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example
// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
// Create a Session in which to pass parameters:
host.Session = host.CreateSession();
// Add parameter values to the Session:
session["TimesToRepeat"] = 5;
// Process a text template:
string result = t4.ProcessTemplate("MyTemplateFile.t4",
  System.IO.File.ReadAllText("MyTemplateFile.t4"));

```

## <a name="passing-values-in-the-call-context"></a>呼び出しコンテキストで値を渡す
 または値を渡すことで、論理データ<xref:System.Runtime.Remoting.Messaging.CallContext>します。

 次の例では、両方のメソッドを使用して値を渡します。

```csharp
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
host.Session = host.CreateSession();
// Pass a value in Session:
host.Session["p1"] = 32;
// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");

// Process a small template inline:
string result = t4.ProcessTemplate("",
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"
 + "Test <#=p1#> <#=p2#>");

// Result value is:
//     Test 32 test

```

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>実行時 (前処理された) テキスト テンプレートに値を渡す
 通常、使用する必要はありません、`<#@parameter#>`ディレクティブ実行時 (前処理された) テキスト テンプレートを使用します。 代わりに、追加のコンス トラクターまたはパラメーターの値を渡すときに経由する、生成されたコードの設定可能なプロパティを定義できます。 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)します。

 ただし、使用する場合`<#@parameter>`実行時テンプレートできます値を渡してにセッションのディクショナリを使用しています。 例として、たとえばという名前の前処理済みテンプレートとして、ファイルを作成した`PreTextTemplate1`します。 テンプレートは、次のコードを使用して、プログラムで呼び出すことができます。

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();

```

## <a name="obtaining-arguments-from-texttemplateexe"></a>TextTemplate.exe から引数を取得します。

> [!IMPORTANT]
>  `parameter`ディレクティブに設定された値を取得できません、`-a`のパラメーター、`TextTransform.exe`ユーティリティ。 これらの値を取得するには、次のように設定します。`hostSpecific="true"`で、`template`ディレクティブ、および使用`this.Host.ResolveParameterValue("","","argName")`します。