---
title: "VLSC からサブスクリプションの割り当てメールを再送信する方法 | Microsoft Docs"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 12/29/2017
Ms.topic: Get-Started-Article
Description: Learn how to resend the subscription assignment to a subscriber from within VLSC
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 7162435044a578a94249774305f2c6b8b6438219
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-resend-subscription-assignment-emails-from-vlsc"></a>VLSC からサブスクリプションの割り当てメールを再送信する方法:

サブスクリプションが VLSC でサブスクライバーに割り当てられ、そのサブスクライバーから割り当てメールの再送信が要求された場合、サブスクライバーの電子メール情報を編集してから元のアドレスに戻すことで、これを行うことができます。 これにより割り当てメールの再送信が自動的にトリガーされます。

次の指示に従って、割り当てメールを再送信します。


1. ボリューム ライセンス サービス センター (VLSC) にアクセスしてサインインします。
2. VLSC の管理ページから、**[サブスクリプション]**、**[Visual Studio サブスクリプション]** の順にクリックします。
3. Visual Studio サブスクリプションに関連付けられている**契約番号**をクリックします。
4. **検索**バーで下矢印をクリックします。  
5. [電子メール アドレス] フィールドを使用してサブスクライバーを検索します。
6. 結果リストからサブスクライバーの**姓**をクリックします。
7. **[編集]** をクリックします。
8. サブスクリプションを編集します。 単に変更する必要があるだけなので、変更内容は何でもかまいません。  たとえば、サブスクライバーの電子メール アドレスの .com から "m" を 1 文字削除します。**[保存]** ボタンをクリックします。
9. 情報が保存されたら、**[編集]** ボタンをもう一度クリックして、電子メールから欠落している文字を修正します。 **[保存]**をクリックします。
   
これにより、サブスクリプションに変更があったことを VLSC に認識させ、割り当てメールがポータルにリストされている電子メールに再送信されます。 

> [!NOTE]
> - 新しく割り当てられたサブスクリプションは、割り当てメールを自動的に生成します。 上記は、ユーザーが新しい割り当てメールを要求した場合、または何らかの理由で通知が送信されない場合にのみ必要です。
> - https://manage.visualstudio.com 経由で割り当てられたサブスクリプションに対して割り当てメールを再送信するには、この手順は必要はありません。ポータルでサブスクライバーに割り当てメールを再送信するには、サブスクライバーを選択して、サブスクライバー リストの上部にある **[再送信]** ボタンをクリックするだけです。  