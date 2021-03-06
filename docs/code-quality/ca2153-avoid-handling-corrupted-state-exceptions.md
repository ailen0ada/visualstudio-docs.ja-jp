---
title: 'CA2153: 破損状態例外の処理を回避する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5043c8cb9cefb8ffdb600083ba2dc4bb49d5e3f5
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547527"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: 破損状態例外の処理を回避する

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

[破損状態例外 (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx)そのメモリ破損がプロセス内に存在します。 プロセスをクラッシュさせるのではなくこれらの例外をキャッチすることは、攻撃者が破損したメモリ領域にセキュリティ上の弱点を見出すことができた場合に、セキュリティ上の脆弱性となる可能性があります。

## <a name="rule-description"></a>規則の説明

CSE は、プロセスが破損状態にあり、システムによってキャッチされていないことを示します。 破損した状態のシナリオでは、適切な `HandleProcessCorruptedStateExceptions` 属性でメソッドをマークした場合に、汎用ハンドラーのみがこの例外をキャッチします。 既定で、[共通言語ランタイム (CLR)](/dotnet/standard/clr) Cse の catch ハンドラーは呼び出されません。

コードをログに記録しても攻撃者はメモリ破損のバグを悪用できるため、このような例外をキャッチせずにプロセスをクラッシュさせるほうが安全な方法です。

catch(exception) や catch(no exception specification) などすべての例外をキャッチする汎用ハンドラーを使用して CSE をキャッチすると、この警告がトリガーされます。

## <a name="how-to-fix-violations"></a>違反の修正方法

この警告を解決するには、次のいずれかの操作を行います。

- 削除、`HandleProcessCorruptedStateExceptions`属性。 これにより、CSE を catch ハンドラーに渡さない既定の実行時の動作に戻ります。

- 特定の例外の種類をキャッチするハンドラーではなく汎用 catch ハンドラーを削除します。 Cse と仮定すると、ハンドラーのコードが安全に処理して (まれな) 場合があります。

- Catch ハンドラーに、これにより、例外が呼び出し元に渡され、実行中のプロセスを終了、CSE を再スローします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告は抑制しないでください。

## <a name="pseudo-code-example"></a>擬似コードの例

### <a name="violation"></a>違反

次の擬似コードでは、このルールにより検出されたパターンを示しています。

```csharp
[HandleProcessCorruptedStateExceptions]
// Method to handle and log CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error.
    }
}
```

### <a name="solution-1"></a>解決方法 1

HandleProcessCorruptedExceptions 属性を削除することにより、例外が処理されないようにします。

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error.
    }
}
```

### <a name="solution-2"></a>解決方法 2

汎用 catch ハンドラーを削除し、特定の例外の種類のみをキャッチします。

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error.
    }
}
```

### <a name="solution-3"></a>解決方法 3

例外を再スローします。

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error.
        throw;
    }
}
```