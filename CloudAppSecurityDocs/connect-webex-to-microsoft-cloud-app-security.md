---
title: Webex を Cloud App Security に接続する
description: この記事では、使用状況を表示および制御するために、API コネクタを使用して Cloud App Security に Webex アプリを接続する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/16/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f50ff4ae3b3a5a04ab9ffe052b0fb1e8ecdb2f7d
ms.sourcegitcommit: 00599ac6c64a4c62ed9ebdda3edb58f90f92c24d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912163"
---
# <a name="connect-cisco-webex-to-microsoft-cloud-app-security"></a>Cisco Webex を Microsoft Cloud App Security に接続する

*適用対象: Microsoft Cloud App Security*

この記事では、コネクタ Api を使用して、既存の Cisco Webex アカウントに Microsoft Cloud App Security を接続する手順について説明します。 この接続により、Webex のユーザー、アクティビティ、ファイルを可視化し、制御できます。 Cloud App Security が Cisco Webex を保護する方法については、「 [Cisco webex を保護](protect-webex.md)する」を参照してください。

## <a name="prerequisites"></a>Prerequisites

- 接続用に専用のサービスアカウントを作成することをお勧めします。 これにより、Webex で送信されたメッセージの削除など、Webex で実行されるガバナンスアクションがこのアカウントから実行されていることを確認できます。 それ以外の場合は、Webex に Cloud App Security 接続した管理者の名前が、アクションを実行したユーザーとして表示されます。
- Webex で、完全な管理者**と**コンプライアンス管理者のアクセス許可を持っている必要があります。

## <a name="how-to-connect-webex-to-cloud-app-security"></a>Webex を Cloud App Security に接続する方法

1. Cloud App Security コンソールで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。

1. **[アプリコネクタ]** ページで、プラスボタンをクリックし、続いて**Cisco Webex**をクリックします。

    ![Webex に接続する](media/cisco-webex.png "Webex に接続する")

1. ポップアップで、このコネクタのインスタンス名を入力します。

1. **[Cisco Webex に接続]** をクリックします。 Webex サインインページが開きます。 チームの Webex インスタンスへの Cloud App Security アクセスを許可するための資格情報を入力します。

1. Webex は、チームの情報やアクティビティログへの Cloud App Security アクセスを許可し、チームメンバーとしてアクティビティを実行できるようにするかどうかをたずねます。 続行するには、 **[許可]** をクリックします。

1. Cloud App Security コンソールに戻ると、Webex が正常に接続されたことを示すメッセージが表示されます。

1. **[API のテスト]** をクリックして、正常に接続されたことを確認します。

    テストには数分かかる場合があります。 成功通知を受信したら、 **[閉じる]** をクリックします。

Webex に接続すると、接続する7日間のイベントを受け取ります。 Cloud App Security は過去3か月にわたってイベントをスキャンします。 これを増やすには、Cisco Webex pro ライセンスを所有し、Cloud App Security サポートでチケットを開く必要があります。

アプリの接続で問題が発生した場合は、「[アプリコネクタのトラブルシューティング](troubleshooting-api-connectors-using-error-messages.md)」を参照してください。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
