---
ms.openlocfilehash: bf83723de025f3e1f6bde5b4226fc8966dff6b9a
ms.sourcegitcommit: 64947f11d367ffbebbafb700fdfdc20617275f35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "48829735"
---
<!-- markdownlint-disable MD002 MD041 -->

コネクタが使用できる状態になっていることを確認するための最後の構成手順は、キャッシュされた接続を作成するためにカスタムコネクタを承認およびテストすることです。

> [!IMPORTANT]
> 次の手順では、管理者特権でログインしている必要があります。

[Microsoft Power オートメーション](https://flow.microsoft.com)で、左側の [ **データ** ] メニュー項目に移動し、[ **接続** ] ページを選択します。 [ **新しい接続** ] リンクを選択します。

![[新しい接続] ボタンのスクリーンショット](./images/new-connection.png)

カスタムコネクタを見つけ、プラスボタンをクリックして接続を完了します。 Office 365 テナント管理者の Azure Active Directory アカウントでサインインします。

![接続リストのスクリーンショット](./images/connection-sign-in.png)

要求されたアクセス許可の入力を求められたら、 **組織に代わって同意** を確認し、[ **同意** する] を選択してアクセス許可を承認します。

![同意プロンプトのスクリーンショット](./images/consent-prompt.png)

アクセス許可を承認した後、Power 自動実行で接続が作成されます。

これで、カスタムコネクタが構成され、有効になりました。 アクセス許可が適用されて使用可能になるまでに遅延が発生することがありますが、コネクタは現在構成されています。
