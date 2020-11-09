---
ms.openlocfilehash: 2d9b6e29a5ddc71b8f7b78b1e2fe035a8fdbddac
ms.sourcegitcommit: 64947f11d367ffbebbafb700fdfdc20617275f35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "48829791"
---
<!-- markdownlint-disable MD002 MD041 -->

前の手順で作成したフローでは、API を使用して、 `$batch` Microsoft Graph に対する2つの個別の要求を行います。 この方法を使用してエンドポイントを呼び出す `$batch` と、いくつかの利点と柔軟性が得られますが、 `$batch` 1 回の呼び出しで Microsoft Graph に複数の要求を実行するときに、エンドポイントの本当の威力を発揮し `$batch` ます。 この演習では、統合グループの作成例を拡張し、1つの要求でチームに複数の既定のチャネルを作成するようにチームを関連付け `$batch` ます。

ブラウザーで [Microsoft Power オートメーション](https://flow.microsoft.com) を開き、Office 365 テナント管理者アカウントでサインインします。 前の手順で作成したフローを選択し、[ **編集** ] を選択します。

[ **新しい手順** ] を選択し `Batch` 、検索ボックスに入力します。 [ **MS Graph バッチコネクタ** ] アクションを追加します。 省略記号を選択して、このアクションの名前をに変更 `Batch POST-channels` します。

アクションの **本文** テキストボックスに次のコードを追加します。

```json
{
  "requests": [
    {
      "id": 1,
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "Marketing Collateral",
        "description": "Marketing collateral and documentation."
      }
    },
    {
      "id": 2,
      "dependsOn": [
        "1"
      ],
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "Vendor Contracts",
        "description": "Vendor documents, contracts, agreements and schedules."
      }
    },
    {
      "id": 3,
      "dependsOn": [
        "2"
      ],
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "General Client Agreements",
        "description": "General Client documents and agreements."
      }
    }
  ]
}
```

上記の3つの要求は、シーケンスの順序を指定するために [dependsOn](https://docs.microsoft.com/graph/json-batching#sequencing-requests-with-the-dependson-property) プロパティを使用していて、それぞれが新しいチームで新しいチャネルを作成するために POST 要求を実行することに注意してください。

プレースホルダーの各インスタンスを選択し、 `REPLACE` [動的コンテンツ] ウィンドウで [ **式** ] を選択します。 次の数式を **式** に追加します。

```js
body('Batch_PUT-team').responses[0].body.id
```

![[動的コンテンツ] ウィンドウ内の式のスクリーンショット](./images/dynamic-expression.png)

[ **保存** ] を選択し、[ **テスト** ] を選択してフローを実行します。 [トリガーアクションを **実行** する] ラジオボタンを選択し、[ **Save & Test** ] を選択します。 [ **名前** ] フィールドにスペースを入れずに一意のグループ名を入力し、[ **実行フロー** ] を選択してフローを実行します。

フローが開始されたら、[ **完了** ] ボタンをクリックしてアクティビティログを表示します。 フローが完了すると、アクションの最終出力には、 `Batch POST-channels` 作成された各チャネルに対して 201 HTTP 状態応答があります。

![成功したフローアクティビティログのスクリーンショット](./images/batch-success.png)

[Microsoft Teams](https://teams.microsoft.com)を参照して、Office 365 テナント管理者アカウントでサインインします。 作成したチームが表示されることと、要求によって作成された3つのチャネルが含まれていることを確認し `$batch` ます。

![新しいチームとチャネルが表示されている Teams アプリのスクリーンショット](./images/team-channels.png)

`Batch POST-channels`このチュートリアルでは、この操作は個別のアクションとして実装されていましたが、チャネルを作成する呼び出しは、アクションに追加の呼び出しとして追加されている可能性があり `Batch PUT-team` ます。 これにより、1回のバッチ呼び出しでチームとすべてのチャネルが作成されます。 自分で試してみてください。

最後に、 [JSON のバッチ](https://docs.microsoft.com/graph/json-batching) 呼び出しは、要求ごとに HTTP 状態コードを返すことに注意してください。 運用プロセスでは、結果の事後処理をアクションと組み合わせ [`Apply to each`](https://docs.microsoft.com/power-automate/apply-to-each) て、個々の応答に201状態コードがあることを検証したり、受信した他の状態コードを補正したりできます。
