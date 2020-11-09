---
ms.openlocfilehash: d628ef3ffff3655bbb15115b6f17726e55185b5b
ms.sourcegitcommit: 64947f11d367ffbebbafb700fdfdc20617275f35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "48829738"
---
<!-- markdownlint-disable MD002 MD041 -->

Microsoft Power オートメーションには、230を超えるボックスコネクタがあります。 これらのコネクタの多くは Microsoft Graph を使用して、Microsoft 製品の特定のエンドポイントと通信します。 また、API 全体をカバーするために Microsoft Graph と直接通信するコネクタが存在しないため、サービスの基本的な構成要素を使用して、Microsoft Graph を Power オートメーションから直接呼び出す必要があるシナリオもあります。

Microsoft Graph を直接呼び出すシナリオに対処するだけでなく、Microsoft Graph API のエンドポイントの多くは、委任された [アクセス許可](https://docs.microsoft.com/graph/permissions-reference)のみをサポートしています。 Microsoft Power 自動の HTTP コネクタを使用すると、Microsoft Graph を呼び出すことを含め、非常に柔軟な統合が可能になります。 ただし、HTTP コネクタは、特定の委任されたアクセス許可シナリオを有効にするためにユーザーの資格情報をキャッシュする機能を備えていません。 このような場合は、カスタムコネクタを作成して、Microsoft Graph API のラッパーを提供し、委任されたアクセス許可で API を使用できるようにすることができます。

このラボでは、上記の両方のシナリオについて説明します。 最初に、委任された [アクセス許可](https://docs.microsoft.com/graph/permissions-reference)を必要とする Microsoft Graph との統合を可能にするカスタムコネクタを作成します。 次に、 [$batch 要求エンドポイント](https://docs.microsoft.com/graph/json-batching)を使用して、アプリに "サインイン済み" ユーザーが存在することを必要とする委任されたアクセス許可を使用して、Microsoft Graph のフルパワーにアクセスできるようにします。

> [!NOTE]
> これは、Microsoft Power オートメーションおよび Azure ロジックアプリで使用するカスタムコネクタの作成に関するチュートリアルです。 このチュートリアルでは、 [カスタムコネクタの概要](https://docs.microsoft.com/connectors/custom-connectors/) を読んで、このプロセスを理解していることを前提としています。

## <a name="prerequisites"></a>前提条件

この投稿でこの手順を完了するには、次のものが必要になります。

- Office 365 テナントへの管理者アクセス。 まだお持ちでない場合は、 [Office 365 開発者プログラム](https://developer.microsoft.com/office/dev-program) にアクセスして、無料の開発者テナントにサインアップしてください。
- [Microsoft Power オートメーション](https://flow.microsoft.com/)へのアクセス。

## <a name="feedback"></a>フィードバック

このチュートリアルに関するフィードバックは、 [GitHub リポジトリ](https://github.com/microsoftgraph/msgraph-training-powerautomate)に記入してください。
