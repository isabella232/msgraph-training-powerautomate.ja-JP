---
ms.openlocfilehash: 1674fb94e1749ad15f8f33f0865ce468f889232a
ms.sourcegitcommit: 64947f11d367ffbebbafb700fdfdc20617275f35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "48829836"
---
<!-- markdownlint-disable MD002 MD041 -->

この演習では、前の手順で作成したカスタムコネクタを使用して Microsoft teams を作成して構成するフローを作成します。 このフローでは、カスタムコネクタを使用して、Office 365 統合グループを作成するために POST 要求を送信します。グループの作成が完了するまで待機し、その後、PUT 要求を送信して、グループを Microsoft チームに関連付けます。

最終的に、フローは次のようになります。

![完了したフローのスクリーンショット](./images/completed-flow.png)

ブラウザーで [Microsoft Power オートメーション](https://flow.microsoft.com) を開き、Office 365 テナント管理者アカウントでサインインします。 左側のナビゲーションで [ **マイフロー** ] を選択します。 [ **新規** ] を選択し、[ **インスタント** ] を選択します。 [ `Create Team` **フロー名** ] に入力してから、[ **このフローをトリガーする方法を選択** してください] で [ **フローを手動でトリガー** する] を選択します。 **[作成]** を選択します。

[フロー項目を **手動でトリガーする** ] を選択し、[ **入力を追加** する] を選択し、 **テキスト** を選択して、タイトルとしてを入力し `Name` ます。

![フロートリガーを手動でトリガーするスクリーンショット](./images/manually-trigger.png)

[ **新しい手順** ] を選択し `Batch` 、検索ボックスに入力します。 [ **MS Graph バッチコネクタ** ] アクションを追加します。 省略記号を選択して、このアクションの名前をに変更 `Batch POST-groups` します。

アクションの **本文** テキストボックスに次のコードを追加します。

```json
{
  "requests": [
    {
      "url": "/groups",
      "method": "POST",
      "id": 1,
      "headers": { "Content-Type": "application/json" },
      "body": {
        "description": "REPLACE",
        "displayName": "REPLACE",
        "groupTypes": ["Unified"],
        "mailEnabled": true,
        "mailNickname": "REPLACE",
        "securityEnabled": false
      }
    }
  ]
}
```

`REPLACE` `Name` [ **動的コンテンツの追加** ] メニューから手動トリガーの値を選択して、各プレースホルダーを置き換えます。

![Microsoft Flow の [動的コンテンツ] メニューのスクリーンショット](./images/dynamic-content.png)

[ **新しい手順** ] を選択し、 `delay` **遅延** アクションを検索して追加して、1分間構成します。

[ **新しい手順** ] を選択し `Batch` 、検索ボックスに入力します。 [ **MS Graph バッチコネクタ** ] アクションを追加します。 省略記号を選択して、このアクションの名前をに変更 `Batch PUT-team` します。

アクションの **本文** テキストボックスに次のコードを追加します。

```json
{
  "requests": [
    {
      "id": 1,
      "url": "/groups/REPLACE/team",
      "method": "PUT",
      "headers": {
        "Content-Type": "application/json"
      },
      "body": {
        "memberSettings": {
          "allowCreateUpdateChannels": true
        },
        "messagingSettings": {
          "allowUserEditMessages": true,
          "allowUserDeleteMessages": true
        },
        "funSettings": {
          "allowGiphy": true,
          "giphyContentRating": "strict"
        }
      }
    }
  ]
}
```

プレースホルダーを選択し、 `REPLACE` [動的コンテンツ] ウィンドウで [ **式** ] を選択します。 次の数式を **式** に追加します。

```js
body('Batch_POST-groups').responses[0].body.id
```

![[動的コンテンツ] ウィンドウ内の式のスクリーンショット](./images/flow-formula.png)

この式では、最初のアクションの結果からグループ ID を使用することを指定します。

![更新されたアクション本文のスクリーンショット](./images/updated-body.png)

[ **保存** ] を選択し、[ **テスト** ] を選択してフローを実行します。

> [!TIP]
> このようなエラーが表示される場合は `The template validation failed: 'The action(s) 'Batch_POST-groups' referenced by 'inputs' in action 'Batch_2' are not defined in the template'` 、式が正しくないため、検索できないフローアクションが参照されている可能性があります。 参照しているアクション名が正確に一致することを確認します。

[トリガーアクションを **実行する** ] ラジオボタンを選択して、[ **Save & Test** ] を選択します。 ダイアログの [ **続行** ] を選択します。 スペースを含まない名前を指定し、[ **実行フロー** ] を選択してチームを作成します。

![[実行フロー] ダイアログのスクリーンショット](./images/run-flow.png)

最後に、[ **完了** ] を選択して、アクティビティログを表示します。 フローが完了すると、Office 365 グループとチームが構成されました。 バッチアクションアイテムを選択して、JSON バッチ呼び出しの結果を表示します。 `outputs` `Batch PUT-team` アクションの状態コードは、次の図のようなチームの関連付けを成功させるために201の状態コードである必要があります。

![成功したフローアクティビティログのスクリーンショット](./images/success.png)
