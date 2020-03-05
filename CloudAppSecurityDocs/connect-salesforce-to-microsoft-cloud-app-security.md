---
title: Salesforce を Cloud App Security に接続する
description: この記事では、API コネクタを使用して Cloud App Security に Salesforce を接続する方法について説明します。これにより、使用状況を表示して制御できます。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/06/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b47b17e74df346b1e1b1cdf01522d5b980360b78
ms.sourcegitcommit: 582779b75be41e57fb1d773d1cf01f6b8598521e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2020
ms.locfileid: "78274679"
---
# <a name="connect-salesforce-to-microsoft-cloud-app-security"></a>Salesforce を Microsoft Cloud App Security に接続する

*適用対象: Microsoft Cloud App Security*

この記事では、App connector API を使用して、既存の Salesforce アカウントに Microsoft Cloud App Security を接続する手順について説明します。 この接続により、Salesforce の使用を可視化し、制御できます。 Cloud App Security が Salesforce を保護する方法については、「 [Protect salesforce](protect-salesforce.md)」を参照してください。

## <a name="how-to-connect-salesforce-to-cloud-app-security"></a>Salesforce を Cloud App Security に接続する方法

1. Cloud App Security 専用のサービス管理者アカウントを用意することをお勧めします。

1. Salesforce で REST API が有効になっていることを確認します。

    Salesforce アカウントには、REST API のサポートを含むエディション

    **パフォーマンス**、**エンタープライズ**、**無制限**、または**開発者**。

    既定では、 **Professional**エディションには REST API がありませんが、オンデマンドで追加することができます。

    現在のエディションで REST API を使用可能かどうか、有効化されているかどうかを確認するには、以下の手順を実行します。

    * Salesforce アカウントにサインインし、**セットアップ**ページにアクセスします。

    * **[ユーザーの管理]** で、 **[ユーザープロファイル]** ページにアクセスします。

        ![salesforce のユーザープロファイルの管理](media/salesforce-manageusers-profiles.png "salesforce のユーザープロファイルの管理")

    * 新しいプロファイルを作成するには、[**新規**作成] をクリックします。
    * Cloud App Security デプロイするために作成したプロファイルを選択し、 **[編集]** をクリックします。 このプロファイルは、アプリコネクタをセットアップするために Cloud App Security サービスアカウントに使用されます。

         ![salesforce のプロファイルの編集](media/salesforce-edit-profile.png "salesforce のプロファイルの編集")

    * 次のチェックボックスをオンにします。
      * **[API Enabled]\(API 有効化\)**
      * **[View All Data]\(すべてのデータを表示する\)**
      * **[Manage Salesforce CRM Content]\(Salesforce CRM コンテンツを管理する\)**
      * **[ユーザーを管理する]**
      * **[すべてのファイルを照会する](https://go.microsoft.com/fwlink/?linkid=2106480)**

      これらのチェックボックスがオフになっている場合は、Salesforce に連絡してアカウントに追加する必要があります。

1. 組織で **[Salesforce CRM Content]** を有効化している場合は、現在の管理者アカウントでも有効になっていることを確認します。

    1. Salesforce の設定ページに移動します。

        ![salesforce のセットアップ](media/salesforce-setup.png "salesforce のセットアップ")

    1. サイド メニューから **[ユーザーの管理]** を選択し、 **[ユーザー]** をクリックします。

        ![salesforce メニューユーザー](media/salesforce-menu-users.png "salesforce メニューユーザー")

    1. 専用の Cloud App Security ユーザーの現在の管理ユーザーを選択します。

    1. **[Salesforce CRM Content ユーザー]** チェックボックスがオンになっていることを確認します。

        選択されていない場合は、 **[編集]** をクリックし、チェックボックスをオンにします。

        ![salesforce crm コンテンツユーザー](media/salesforce-crm-content-user.png "salesforce crm コンテンツユーザー")

    1. **[保存]** をクリックします。

1. Cloud App Security コンソールで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。

1. **[アプリ コネクター]** ページで、[+] ボタン、 **[Salesforce]** の順にクリックします。

    ![salesforce の接続](media/connect-salesforce.png "salesforce の接続")

1. Salesforce の設定ページの API タブで、インストールするインスタンスに応じて **Follow this link (このリンクに移動)** をクリックします。

1. Salesforce のサインインページが開きます。 Cloud App Security がチームの Salesforce アプリにアクセスできるように、資格情報を入力します。

    ![salesforce のサインイン](media/salesforce-logon.png "salesforce ログオン")

1. Cloud App Security からチームの情報やアクティビティ ログにアクセスし、任意のチーム メンバーと同様に任意のアクティビティを実行することを許可するかどうかを確認するメッセージが Salesforce で表示されます。 続行するには、 **[許可]** をクリックします。

1. この時点で、デプロイの成功または失敗に関する通知が表示されます。 Cloud App Security が Salesforce.com で承認されました。

1. Cloud App Security コンソールに戻ると、Salesforce が正常に接続されたことを示すメッセージが表示されます。

1. **[API のテスト]** をクリックして、正常に接続されたことを確認します。

    テストには数分かかる場合があります。 成功の通知を受信したら、 **[完了]** をクリックします。

Salesforce を接続した後、次のようなイベントが表示されます。 Salesforce EventMonitoring に応じて、接続の時点からのトリガー、イベントのログイン、および60日前の接続、EventMonitoring 30 日、または1日後のイベントを受け取ります。使用. Cloud App Security API は Salesforce から利用できる API と直接通信します。 Salesforce はそれが受け取る API 呼び出しの数を制限できるため、Cloud App Security はそれを考慮し、制限を順守します。 Salesforce API は、利用できる合計数や残りの数など、API カウンターのフィールドと共に各応答を送信します。 Cloud App Security はこれを百分率に計算し、利用できる API 呼び出しの 10% が常に残るようにします。

> [!NOTE]
> Cloud App Security の調整は、Salesforce で呼び出した Cloud App Security の API に基づいてのみ計算されます。他のアプリケーションが Salesforce で呼び出した API は計算対象になりません。
> API 呼び出しが制限されることで Cloud App Security にデータが取り込まれる速度が遅くなることがありますが、通常、一晩で追いつきます。

Salesforce イベントは Cloud App Security により次のように処理されます。

* 15分ごとのサインインイベント
* 15分ごとに監査証跡をセットアップする
* 1時間ごとのイベントログ。 Salesforce のイベントの詳細については、「[イベント監視の使用](https://developer.salesforce.com/docs/atlas.en-us.api_rest.meta/api_rest/using_resources_event_log_files.htm)」をご覧ください。

アプリの接続で問題が発生した場合は、「[アプリコネクタのトラブルシューティング](troubleshooting-api-connectors-using-error-messages.md)」を参照してください。

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
