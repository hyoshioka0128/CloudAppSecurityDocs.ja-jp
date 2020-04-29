---
title: Okta を Cloud App Security に接続する
description: この記事では、使用状況を視覚化して制御できるように、API コネクタを使用して Cloud App Security に Okta を接続する方法に関する情報を提供します。
keywords: ''
author: shsagir
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
ms.openlocfilehash: b86f8ef6eef534301b21371021295587c6535786
ms.sourcegitcommit: ecb1835d1cd880de38f32ce7a7031b0015f3cae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2020
ms.locfileid: "81230044"
---
# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Okta を Microsoft Cloud App Security に接続する

*適用対象:Microsoft Cloud App Security*

この記事では、コネクタ API を使用して Microsoft Cloud App Security を既存の Okta アカウントに接続する方法を説明します。 この接続により、Okta の使用状況を視覚化して制御できるようになります。 Cloud App Security が Okta を保護する方法については、「 [Protect okta](protect-okta.md)」を参照してください。

## <a name="how-to-connect-okta-to-cloud-app-security"></a>Okta を Cloud App Security に接続する方法

1. Okta で、Cloud App Security 向けの管理者サービス アカウントを作成することをお勧めします。

    スーパー管理者のアクセス許可を付与されたアカウントを必ず使用してください。

    Okta アカウントが検証済みであることを確認します。

1. Okta コンソールで [**管理者**] をクリックします。

    - [**セキュリティ**]、[**API**] の順にクリックします。

         ![Okta api](media/okta-api.png "Okta api")

    - [**トークンを作成します**] をクリックします。

         ![Okta のトークンの作成](media/okta-createtoken.jpg "Okta のトークンの作成")

    - [**トークンの作成**] ポップアップで、Cloud App Security トークンに名前を設定し、[**トークンの作成**] をクリックします。

         ![Okta トークンのポップアップ](media/okta-token-pop-up.png)

    - [**Token created successfully (トークンは正常に作成されました)**] ポップアップで、[**Token value (トークン値)**] をコピーします。

         ![Okta トークン値](media/okta-token-value.png "Okta トークン値")

1. Cloud App Security コンソールで、**[調査]**、**[接続アプリ]** の順にクリックします。

1. **[アプリ コネクター]** ページで、[+] ボタン、**[Okta]** の順にクリックします。

    ![Okta の接続](media/connect-okta.png "Okta の接続")

1. 表示されたポップアップの **[ドメイン]** フィールドに Okta ドメインを入力し、トークンを **[トークン]** フィールドに貼り付けます。

1. **[接続]** をクリックして、Okta のトークンを Cloud App Security で作成します。

1. [**API のテスト**] をクリックして、正常に接続されたことを確認します。

    テストには数分かかる場合があります。 成功通知を受信したら、 [**閉じる**] をクリックします。

Okta を接続すると、接続までの 60 日間のイベントを受け取ります。

アプリの接続で問題が発生した場合は、「[アプリコネクタのトラブルシューティング](troubleshooting-api-connectors-using-error-messages.md)」を参照してください。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [ポリシーを使用してクラウドアプリを制御する](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
