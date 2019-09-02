---
title: Okta を Cloud App Security に接続する
description: この記事では、使用状況を視覚化して制御できるように、API コネクタを使用して Cloud App Security に Okta を接続する方法に関する情報を提供します。
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: shsagir
ms.date: 9/1/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 59798c191a90f9be252e42ff9a9d4582f7d2221e
ms.sourcegitcommit: 0b78b13bc163bfcd6f2ae13b1f57acee05e5b423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/01/2019
ms.locfileid: "70208813"
---
# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Okta を Microsoft Cloud App Security に接続する

*適用対象:Microsoft Cloud App Security*

この記事では、コネクタ API を使用して Microsoft Cloud App Security を既存の Okta アカウントに接続する方法を説明します。 この接続により、Okta の使用状況を視覚化して制御できるようになります。

## <a name="how-to-connect-okta-to-cloud-app-security"></a>Okta を Cloud App Security に接続する方法

1. Okta で、Cloud App Security 向けの管理者サービス アカウントを作成することをお勧めします。

    スーパー管理者のアクセス許可を付与されたアカウントを必ず使用してください。

    Okta アカウントが検証済みであることを確認します。

1. Okta コンソールで **[管理者]** をクリックします。

    - **[セキュリティ]** 、 **[API]** の順にクリックします。

         ![Okta API](./media/okta-api.png "Okta API")

    - **[トークンを作成します]** をクリックします。

         ![Okta のトークンの作成](./media/okta-createtoken.jpg "Okta のトークンの作成")

    - **[トークンを作成します]** ポップアップで、Cloud App Security トークンに名前を付けてから **[トークンを作成します]** をクリックします。

         ![Okta のトークン ポップアップ](./media/okta-token-popup.png "Okta のトークン ポップアップ")

    - **[Token created successfully (トークンは正常に作成されました)]** ポップアップで、 **[Token value (トークン値)]** をコピーします。

         ![Okta のトークン値](./media/okta-token-value.png "Okta のトークン値")

1. Cloud App Security コンソールで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。

1. **[アプリ コネクター]** ページで、[+] ボタン、 **[Okta]** の順にクリックします。

    ![Okta の接続](./media/connect-okta.png "Okta の接続")

1. 表示されたポップアップの **[ドメイン]** フィールドに Okta ドメインを入力し、トークンを **[トークン]** フィールドに貼り付けます。

1. **[接続]** をクリックして、Okta のトークンを Cloud App Security で作成します。

1. **[API のテスト]** をクリックして、正常に接続されたことを確認します。

    テストには数分かかる場合があります。 成功通知を受信したら、 **[閉じる]** をクリックします。

Okta を接続すると、接続までの 60 日間のイベントを受け取ります。

## <a name="next-steps"></a>次の手順

[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)
