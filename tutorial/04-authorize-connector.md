---
ms.openlocfilehash: bf83723de025f3e1f6bde5b4226fc8966dff6b9a
ms.sourcegitcommit: 64947f11d367ffbebbafb700fdfdc20617275f35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "48829735"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="1bf3a-101">コネクタが使用できる状態になっていることを確認するための最後の構成手順は、キャッシュされた接続を作成するためにカスタムコネクタを承認およびテストすることです。</span><span class="sxs-lookup"><span data-stu-id="1bf3a-101">The final configuration step to ensure the connector is ready for use is to authorize and test the custom connector to create a cached connection.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1bf3a-102">次の手順では、管理者特権でログインしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1bf3a-102">The following steps requires that you are logged in with administrator privileges.</span></span>

<span data-ttu-id="1bf3a-103">[Microsoft Power オートメーション](https://flow.microsoft.com)で、左側の [ **データ** ] メニュー項目に移動し、[ **接続** ] ページを選択します。</span><span class="sxs-lookup"><span data-stu-id="1bf3a-103">In [Microsoft Power Automate](https://flow.microsoft.com), go to the **Data** menu item on the left and choose the **Connections** page.</span></span> <span data-ttu-id="1bf3a-104">[ **新しい接続** ] リンクを選択します。</span><span class="sxs-lookup"><span data-stu-id="1bf3a-104">Choose the **New Connection** link.</span></span>

![[新しい接続] ボタンのスクリーンショット](./images/new-connection.png)

<span data-ttu-id="1bf3a-106">カスタムコネクタを見つけ、プラスボタンをクリックして接続を完了します。</span><span class="sxs-lookup"><span data-stu-id="1bf3a-106">Find your custom connector and complete the connection by clicking the plus button.</span></span> <span data-ttu-id="1bf3a-107">Office 365 テナント管理者の Azure Active Directory アカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="1bf3a-107">Sign in with your Office 365 tenant administrator's Azure Active Directory account.</span></span>

![接続リストのスクリーンショット](./images/connection-sign-in.png)

<span data-ttu-id="1bf3a-109">要求されたアクセス許可の入力を求められたら、 **組織に代わって同意** を確認し、[ **同意** する] を選択してアクセス許可を承認します。</span><span class="sxs-lookup"><span data-stu-id="1bf3a-109">When prompted for the requested permissions, check **Consent on behalf of your organization** and then choose **Accept** to authorize permissions.</span></span>

![同意プロンプトのスクリーンショット](./images/consent-prompt.png)

<span data-ttu-id="1bf3a-111">アクセス許可を承認した後、Power 自動実行で接続が作成されます。</span><span class="sxs-lookup"><span data-stu-id="1bf3a-111">After you authorize the permissions, a connection is created in Power Automate.</span></span>

<span data-ttu-id="1bf3a-112">これで、カスタムコネクタが構成され、有効になりました。</span><span class="sxs-lookup"><span data-stu-id="1bf3a-112">The custom connector is now configured and enabled.</span></span> <span data-ttu-id="1bf3a-113">アクセス許可が適用されて使用可能になるまでに遅延が発生することがありますが、コネクタは現在構成されています。</span><span class="sxs-lookup"><span data-stu-id="1bf3a-113">There may be a delay in permissions being applied and available, but the connector is now configured.</span></span>
