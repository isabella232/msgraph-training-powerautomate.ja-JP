---
ms.openlocfilehash: 22c9c7ddd8513d857d96ade608e4b2e4e809dc41
ms.sourcegitcommit: 64947f11d367ffbebbafb700fdfdc20617275f35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "48829767"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="81a87-101">この演習では、カスタムコネクタに対して委任されたアクセス許可を提供するために使用される新しい Azure Active Directory アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="81a87-101">In this exercise, you will create a new Azure Active Directory Application which will be used to provide the delegated permissions for the custom connector.</span></span>

<span data-ttu-id="81a87-102">ブラウザーを開き、 [Azure Active Directory 管理センター](https://aad.portal.azure.com)に移動します。</span><span class="sxs-lookup"><span data-stu-id="81a87-102">Open a browser and navigate to [Azure Active Directory admin center](https://aad.portal.azure.com).</span></span> <span data-ttu-id="81a87-103">左側のナビゲーションメニューで [ **Azure Active directory** ] リンクを選択し、 **azure active directory** ブレードの [ **管理** ] セクションで [ **アプリの登録** ] エントリを選択します。</span><span class="sxs-lookup"><span data-stu-id="81a87-103">Choose the **Azure Active Directory** link in the left navigation menu, then choose the **App registrations** entry in the **Manage** section of the **Azure Active Directory** blade.</span></span>

![Azure Active Directory 管理センターの Azure Active Directory ブレードのスクリーンショット](./images/app-registrations.png)

<span data-ttu-id="81a87-105">**アプリ登録** ブレードの上部にある [ **新しい登録** ] メニュー項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="81a87-105">Choose the **New registration** menu item at the top of the **App Registrations** blade.</span></span>

![Azure Active Directory 管理センターのアプリ登録ブレードのスクリーンショット](./images/new-registration.png)

<span data-ttu-id="81a87-107">`MS Graph Batch App`[ **名前** ] フィールドにを入力します。</span><span class="sxs-lookup"><span data-stu-id="81a87-107">Enter `MS Graph Batch App` in the **Name** field.</span></span> <span data-ttu-id="81a87-108">[ **サポートされているアカウントの種類** ] セクションで、 **任意の組織ディレクトリの [アカウント** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="81a87-108">In the **Supported account types** section, select **Accounts in any organizational directory**.</span></span> <span data-ttu-id="81a87-109">[ **リダイレクト URI** ] セクションを空白のままにして、[ **登録** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="81a87-109">Leave the **Redirect URI** section blank and choose **Register**.</span></span>

![Azure Active Directory 管理センターでアプリケーションブレードを登録するスクリーンショット](./images/register-an-app.png)

<span data-ttu-id="81a87-111">**MS Graph バッチアプリ** ブレードで、 **アプリケーション (クライアント) ID** をコピーします。</span><span class="sxs-lookup"><span data-stu-id="81a87-111">On the **MS Graph Batch App** blade, copy the **Application (client) ID**.</span></span> <span data-ttu-id="81a87-112">次の手順でこれを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="81a87-112">You'll need this in the next exercise.</span></span>

![登録済みアプリケーションページのスクリーンショット](./images/app-id.png)

<span data-ttu-id="81a87-114">**MS Graph バッチアプリ** ブレードの [ **管理** ] セクションで、 **API アクセス許可** エントリを選択します。</span><span class="sxs-lookup"><span data-stu-id="81a87-114">Choose the **API permissions** entry in the **Manage** section of the **MS Graph Batch App** blade.</span></span> <span data-ttu-id="81a87-115">[ **API アクセス許可** ] の下で [ **アクセス許可の追加** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="81a87-115">Choose **Add a permission** under **API permissions**.</span></span>

![API アクセス許可ブレードのスクリーンショット](./images/api-permissions.png)

<span data-ttu-id="81a87-117">[ **API アクセス許可の要求** ] ブレードで、 **Microsoft Graph** を選択し、[委任された **アクセス許可** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="81a87-117">In the **Request API permissions** blade, choose the **Microsoft Graph** , then choose **Delegated permissions**.</span></span> <span data-ttu-id="81a87-118">[検索 `group` ] を選択し、[ **すべてのグループの読み取りと書き込み** ] アクセス許可を選択します。</span><span class="sxs-lookup"><span data-stu-id="81a87-118">Search for `group`, then select the **Read and write all groups** delegated permission.</span></span> <span data-ttu-id="81a87-119">ブレードの下部にある [ **アクセス許可の追加** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="81a87-119">Choose **Add permissions** at the bottom of the blade.</span></span>

 ![API アクセス許可ブレードの要求のスクリーンショット](./images/select-permissions.png)

<span data-ttu-id="81a87-121">**MS Graph バッチアプリ** ブレードの [ **管理** ] セクションで、[ **証明書と秘密** ] エントリを選択し、[ **新しいクライアントシークレット** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="81a87-121">Choose the **Certificates and secrets** entry in the **Manage** section of the **MS Graph Batch App** blade, then choose **New client secret**.</span></span> <span data-ttu-id="81a87-122">`forever`**説明** にを入力し、[ **期限切れ** ] の下で [ **なし** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="81a87-122">Enter `forever` in the **Description** and select **Never** under **Expires**.</span></span> <span data-ttu-id="81a87-123">**[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="81a87-123">Choose **Add**.</span></span>

![証明書とシークレットブレードのスクリーンショット](./images/create-client-secret.png)

<span data-ttu-id="81a87-125">新しいシークレットの値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="81a87-125">Copy the value for the new secret.</span></span> <span data-ttu-id="81a87-126">次の手順でこれを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="81a87-126">You'll need this in the next exercise.</span></span>

![新しいクライアントシークレットのスクリーンショット](./images/copy-client-secret.png)

> [!IMPORTANT]
> <span data-ttu-id="81a87-128">この手順は、このブレードを閉じたときにシークレットにアクセスできないため、重要です。</span><span class="sxs-lookup"><span data-stu-id="81a87-128">This step is critical as the secret will not be accessible once you close this blade.</span></span> <span data-ttu-id="81a87-129">このシークレットをテキストエディターに保存して、今後の演習で使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="81a87-129">Save this secret to a text editor for use in upcoming exercises.</span></span>

<span data-ttu-id="81a87-130">Teams プロパティなど、Microsoft Graph からアクセスできる追加のサービスの管理を有効にするには、特定のサービスの管理を有効にするために、追加の適切なスコープを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81a87-130">To enable management of additional services accessible via the Microsoft Graph, including Teams properties, you would need to select additional, appropriate scopes to enable managing specific services.</span></span> <span data-ttu-id="81a87-131">たとえば、OneNote ノートブックまたはプランナープラン、バケット、タスクの作成を可能にするソリューションを拡張するには、関連する Api に必要なアクセス許可スコープを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81a87-131">For example, to extend our solution to enable creating OneNote Notebooks or Planner plans, buckets and tasks you would need to add the required permission scopes for the relevant APIs.</span></span>
