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
ms.openlocfilehash: df64be6f8e3d8739934ae575ee90f3813dabaae6
ms.sourcegitcommit: 00599ac6c64a4c62ed9ebdda3edb58f90f92c24d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912315"
---
# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Okta を Microsoft Cloud App Security に接続する

*適用対象: Microsoft Cloud App Security*

この記事では、コネクタ API を使用して Microsoft Cloud App Security を既存の Okta アカウントに接続する方法を説明します。 この接続により、Okta の使用状況を視覚化して制御できるようになります。 Cloud App Security が Okta を保護する方法については、「 [Protect okta](protect-okta.md)」を参照してください。

## <a name="how-to-connect-okta-to-cloud-app-security"></a>Okta を Cloud App Security に接続する方法

1. Okta で、Cloud App Security 向けの管理者サービス アカウントを作成することをお勧めします。

    スーパー管理者のアクセス許可を付与されたアカウントを必ず使用してください。

    Okta アカウントが検証済みであることを確認します。

1. Okta コンソールで **[管理者]** をクリックします。

    - **[セキュリティ]** 、 **[API]** の順にクリックします。

         ![Okta api](media/okta-api.png "Okta api")

    - **[トークンを作成します]** をクリックします。

         ![Okta のトークンの作成](media/okta-createtoken.jpg "Okta のトークンの作成")

    - **[トークンを作成します]** ポップアップで、Cloud App Security トークンに名前を付けてから **[トークンを作成します]** をクリックします。

         ![Okta トークンのポップアップ](media/okta-token-popup.png "Okta トークンのポップアップ")

    - **[Token created successfully (トークンは正常に作成されました)]** ポップアップで、 **[Token value (トークン値)]** をコピーします。

         ![Okta トークン値](media/okta-token-value.png "Okta トークン値")

1. Cloud App Security コンソールで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。

1. **[アプリ コネクター]** ページで、[+] ボタン、 **[Okta]** の順にクリックします。

    ![Okta の接続](media/connect-okta.png "Okta の接続")

1. 表示されたポップアップの **[ドメイン]** フィールドに Okta ドメインを入力し、トークンを **[トークン]** フィールドに貼り付けます。

1. **[接続]** をクリックして、Okta のトークンを Cloud App Security で作成します。

1. **[API のテスト]** をクリックして、正常に接続されたことを確認します。

    テストには数分かかる場合があります。 成功通知を受信したら、 **[閉じる]** をクリックします。

Okta を接続すると、接続までの 60 日間のイベントを受け取ります。

アプリの接続で問題が発生した場合は、「[アプリコネクタのトラブルシューティング](troubleshooting-api-connectors-using-error-messages.md)」を参照してください。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
