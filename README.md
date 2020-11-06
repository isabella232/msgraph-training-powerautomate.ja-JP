---
ms.openlocfilehash: 24aac7ad8709fd70d87f1a2d0d0ceecf99aed2db
ms.sourcegitcommit: 64947f11d367ffbebbafb700fdfdc20617275f35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "48829732"
---
# <a name="microsoft-graph-training-module---create-a-microsoft-graph-json-batch-custom-connector-for-microsoft-power-automate--azure-logic-apps"></a><span data-ttu-id="e4b5d-101">Microsoft Graph トレーニングモジュール-microsoft Power オートメーション & Azure ロジックアプリ用の Microsoft Graph JSON Batch カスタムコネクタを作成する</span><span class="sxs-lookup"><span data-stu-id="e4b5d-101">Microsoft Graph Training Module - Create a Microsoft Graph JSON Batch Custom Connector for Microsoft Power Automate & Azure Logic Apps</span></span>

<span data-ttu-id="e4b5d-102">このモジュールでは、Microsoft Graph JSON バッチ REST API を使用して Office 365 のデータにアクセスする方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="e4b5d-102">This module will introduce you to working with the Microsoft Graph JSON Batching REST API to access data in Office 365.</span></span> <span data-ttu-id="e4b5d-103">Microsoft Power オートメーション用のカスタムコネクタを作成して構成し、Microsoft Graph JSON バッチ API にアクセスし、カスタムコネクタをフローで使用して Microsoft teams を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e4b5d-103">You will learn how to create and configure a custom connector for Microsoft Power Automate, access the the Microsoft Graph JSON Batch API, and use the custom connector in a flow to create a Microsoft Team.</span></span>

## <a name="lab---create-a-microsoft-graph-json-batch-custom-connector-for-microsoft-power-automate--azure-logic-apps"></a><span data-ttu-id="e4b5d-104">演習-microsoft Graph JSON Batch カスタムコネクタを作成して Microsoft Power オートメーション & Azure ロジックアプリを作成する</span><span class="sxs-lookup"><span data-stu-id="e4b5d-104">Lab - Create a Microsoft Graph JSON Batch Custom Connector for Microsoft Power Automate & Azure Logic Apps</span></span>

<span data-ttu-id="e4b5d-105">このラボでは、Microsoft Graph JSON バッチ REST API を使用して、カスタムコネクタおよびフローアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="e4b5d-105">In this lab you will leverage the Microsoft Graph JSON Batching REST API to create a Custom Connector and flow application.</span></span>

- [<span data-ttu-id="e4b5d-106">Microsoft Graph のパワーオートメーションのチュートリアル</span><span class="sxs-lookup"><span data-stu-id="e4b5d-106">Power Automate Microsoft Graph tutorial</span></span>](https://docs.microsoft.com/graph/tutorials/powerautomate)

## <a name="contributors"></a><span data-ttu-id="e4b5d-107">共同作成者</span><span class="sxs-lookup"><span data-stu-id="e4b5d-107">Contributors</span></span>

| <span data-ttu-id="e4b5d-108">ロール</span><span class="sxs-lookup"><span data-stu-id="e4b5d-108">Roles</span></span>       | <span data-ttu-id="e4b5d-109">作成者 (s)</span><span class="sxs-lookup"><span data-stu-id="e4b5d-109">Author(s)</span></span>                                            |
|-------------|------------------------------------------------------|
| <span data-ttu-id="e4b5d-110">ラボマニュアル</span><span class="sxs-lookup"><span data-stu-id="e4b5d-110">Lab Manuals</span></span> | <span data-ttu-id="e4b5d-111">John Liu (Microsoft MVP, SharePointGurus) @johnnliu</span><span class="sxs-lookup"><span data-stu-id="e4b5d-111">John Liu (Microsoft MVP, SharePointGurus) @johnnliu</span></span>  |
| <span data-ttu-id="e4b5d-112">ラボマニュアル</span><span class="sxs-lookup"><span data-stu-id="e4b5d-112">Lab Manuals</span></span> | <span data-ttu-id="e4b5d-113">Pete Skelly) @pskelly</span><span class="sxs-lookup"><span data-stu-id="e4b5d-113">Pete Skelly (ThreeWill) @pskelly</span></span>                     |
| <span data-ttu-id="e4b5d-114">ラボマニュアル</span><span class="sxs-lookup"><span data-stu-id="e4b5d-114">Lab Manuals</span></span> | <span data-ttu-id="e4b5d-115">Ayca Bas (Microsoft) @aycabas</span><span class="sxs-lookup"><span data-stu-id="e4b5d-115">Ayca Bas (Microsoft) @aycabas</span></span>                        |

## <a name="version-history"></a><span data-ttu-id="e4b5d-116">バージョン履歴</span><span class="sxs-lookup"><span data-stu-id="e4b5d-116">Version history</span></span>

| <span data-ttu-id="e4b5d-117">バージョン</span><span class="sxs-lookup"><span data-stu-id="e4b5d-117">Version</span></span> | <span data-ttu-id="e4b5d-118">日付</span><span class="sxs-lookup"><span data-stu-id="e4b5d-118">Date</span></span>              | <span data-ttu-id="e4b5d-119">コメント</span><span class="sxs-lookup"><span data-stu-id="e4b5d-119">Comments</span></span>                                             |
|---------|-------------------|------------------------------------------------------|
| <span data-ttu-id="e4b5d-120">1.3</span><span class="sxs-lookup"><span data-stu-id="e4b5d-120">1.3</span></span>     | <span data-ttu-id="e4b5d-121">2020 年 8 月 24 日</span><span class="sxs-lookup"><span data-stu-id="e4b5d-121">August 24, 2020</span></span>   | <span data-ttu-id="e4b5d-122">電源自動化に更新されました</span><span class="sxs-lookup"><span data-stu-id="e4b5d-122">Updated to Power Automate</span></span>                            |
| <span data-ttu-id="e4b5d-123">1.2</span><span class="sxs-lookup"><span data-stu-id="e4b5d-123">1.2</span></span>     | <span data-ttu-id="e4b5d-124">2018 年 11 月 27 日</span><span class="sxs-lookup"><span data-stu-id="e4b5d-124">November 27, 2018</span></span> | <span data-ttu-id="e4b5d-125">利用 ~ docs.microsoft.com/graph</span><span class="sxs-lookup"><span data-stu-id="e4b5d-125">Onboarded to docs.microsoft.com/graph</span></span>                |
| <span data-ttu-id="e4b5d-126">1.1</span><span class="sxs-lookup"><span data-stu-id="e4b5d-126">1.1</span></span>     | <span data-ttu-id="e4b5d-127">2018年11月7日</span><span class="sxs-lookup"><span data-stu-id="e4b5d-127">November 07, 2018</span></span> | <span data-ttu-id="e4b5d-128">複数の操作を呼び出すための手順6の内容を追加しました</span><span class="sxs-lookup"><span data-stu-id="e4b5d-128">Added step 6 content for calling multiple operations</span></span> |
| <span data-ttu-id="e4b5d-129">1.0</span><span class="sxs-lookup"><span data-stu-id="e4b5d-129">1.0</span></span>     | <span data-ttu-id="e4b5d-130">2018 年 10 月 22 日</span><span class="sxs-lookup"><span data-stu-id="e4b5d-130">October 22, 2018</span></span>  | <span data-ttu-id="e4b5d-131">Microsoft Graph 関連製品 breakouts を追加します。</span><span class="sxs-lookup"><span data-stu-id="e4b5d-131">Add Microsoft Graph related product breakouts.</span></span>       |

## <a name="disclaimer"></a><span data-ttu-id="e4b5d-132">免責事項</span><span class="sxs-lookup"><span data-stu-id="e4b5d-132">Disclaimer</span></span>

<span data-ttu-id="e4b5d-133">**このコードは、特定の目的、市販性、または非侵害に対する暗黙の保証を含め、明示的または黙示的ないかなる種類の保証なし *に提供されます* 。**</span><span class="sxs-lookup"><span data-stu-id="e4b5d-133">**THIS CODE IS PROVIDED *AS IS* WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING ANY IMPLIED WARRANTIES OF FITNESS FOR A PARTICULAR PURPOSE, MERCHANTABILITY, OR NON-INFRINGEMENT.**</span></span>
