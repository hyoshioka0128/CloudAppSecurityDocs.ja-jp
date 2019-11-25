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
ms.openlocfilehash: c51cbcb3d8f08fb7b1fc1fc4668905ae11eaeed0
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461096"
---
# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Okta を Microsoft Cloud App Security に接続する

*適用対象: Microsoft Cloud App Security*

この記事では、コネクタ API を使用して Microsoft Cloud App Security を既存の Okta アカウントに接続する方法を説明します。 この接続により、Okta の使用状況を視覚化して制御できるようになります。

## <a name="how-to-connect-okta-to-cloud-app-security"></a>Okta を Cloud App Security に接続する方法

1. Okta で、Cloud App Security 向けの管理者サービス アカウントを作成することをお勧めします。

    スーパー管理者のアクセス許可を付与されたアカウントを必ず使用してください。

    Okta アカウントが検証済みであることを確認します。

1. Okta コンソールで **[管理者]** をクリックします。

    - **[セキュリティ]** 、 **[API]** の順にクリックします。

         ![Okta api](./media/okta-api.png "Okta api")

    - **[トークンを作成します]** をクリックします。

         ![Okta create token](./media/okta-createtoken.jpg "Okta create token")

    - **[トークンを作成します]** ポップアップで、Cloud App Security トークンに名前を付けてから **[トークンを作成します]** をクリックします。

         ![Okta token popup](./media/okta-token-popup.png "Okta token popup")

    - **[Token created successfully (トークンは正常に作成されました)]** ポップアップで、 **[Token value (トークン値)]** をコピーします。

         ![Okta token value](./media/okta-token-value.png "Okta token value")

1. Cloud App Security コンソールで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。

1. **[アプリ コネクター]** ページで、[+] ボタン、 **[Okta]** の順にクリックします。

    ![connect Okta](./media/connect-okta.png "connect Okta")

1. 表示されたポップアップの **[ドメイン]** フィールドに Okta ドメインを入力し、トークンを **[トークン]** フィールドに貼り付けます。

1. **[接続]** をクリックして、Okta のトークンを Cloud App Security で作成します。

1. **[API のテスト]** をクリックして、正常に接続されたことを確認します。

    テストには数分かかる場合があります。 成功通知を受信したら、 **[閉じる]** をクリックします。

Okta を接続すると、接続までの 60 日間のイベントを受け取ります。

## <a name="next-steps"></a>次のステップ

[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
