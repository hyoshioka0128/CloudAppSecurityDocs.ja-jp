---
title: Salesforce を Cloud App Security に接続する
description: この記事では、使用状況を視覚化して制御できるように、API コネクタを使用して Cloud App Security に Salesforce を接続する方法に関する情報を提供します。
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
ms.openlocfilehash: 6121851590f31189cbee7cbeab2efd77a842f964
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720031"
---
# <a name="connect-salesforce-to-microsoft-cloud-app-security"></a>Salesforce を Microsoft Cloud App Security に接続する

*適用対象: Microsoft Cloud App Security*

この記事では、App Connector API を使用して Microsoft Cloud App Security を既存の Salesforce アカウントに接続する方法を説明します。 この接続により、Salesforce の使用状況を視覚化して制御できるようになります。

## <a name="how-to-connect-salesforce-to-cloud-app-security"></a>Salesforce を Cloud App Security に接続する方法

1. Cloud App Security 専用のサービス管理者アカウントを用意することをお勧めします。

1. Salesforce で REST API が有効になっていることを確認します。

    Salesforce アカウントには、REST API のサポートを含むエディション

    (**Performance**、**Enterprise**、**Unlimited**、**Developer** のいずれか) を使用する必要があります。

    **Professional** エディションには、既定では REST API が含まれていませんが、オンデマンドで追加することができます。

    現在のエディションで REST API を使用可能かどうか、有効化されているかどうかを確認するには、以下の手順を実行します。

    * Salesforce アカウントにサインインし、 **[設定]** ページに移動します。

    * **[Manage Users]\(ユーザーの管理\)** で、 **[User Profiles]\(ユーザー プロファイル\)** ページに移動します。

        ![salesforce のユーザープロファイルの管理](media/salesforce-manageusers-profiles.png "salesforce のユーザープロファイルの管理")

    * **[New]\(新規\)** をクリックして、新しいプロファイルを作成します。
    * Cloud App Security のデプロイ用に作成したプロファイルを選び、 **[Edit]\(編集\)** をクリックします。 このプロファイルは、アプリコネクタをセットアップするために Cloud App Security サービスアカウントに使用されます。

         ![salesforce のプロファイルの編集](media/salesforce-edit-profile.png "Salesforce のプロファイルの編集")

    * 次のチェックボックスをオンにします。
      * **[API Enabled]\(API 有効化\)**
      * **[View All Data]\(すべてのデータを表示する\)**
      * **[Manage Salesforce CRM Content]\(Salesforce CRM コンテンツを管理する\)**
      * **[ユーザーを管理する]**
      * **[すべてのファイルを照会する](https://go.microsoft.com/fwlink/?linkid=2106480)**

      チェックボックスがオフになっている場合は、Salesforce に連絡して自分のアカウントに追加する必要があります。

1. 組織で **[Salesforce CRM Content]** を有効化している場合は、現在の管理者アカウントでも有効になっていることを確認します。

    1. Salesforce の設定ページに移動します。

        ![salesforce のセットアップ](media/salesforce-setup.png "Salesforce の設定")

    1. サイド メニューから **[ユーザーの管理]** を選択し、 **[ユーザー]** をクリックします。

        ![salesforce メニューユーザー](media/salesforce-menu-users.png "Salesforce メニューのユーザー")

    1. 専用の Cloud App Security ユーザーの現在の管理ユーザーを選択します。

    1. **[Salesforce CRM Content ユーザー]** チェックボックスがオンになっていることを確認します。

        オフになっている場合は、 **[編集]** をクリックしてチェックボックスをオンにします。

        ![salesforce crm コンテンツユーザー](media/salesforce-crm-content-user.png "Salesforce CRM Content ユーザー")

    1. **[Save]** (保存) をクリックします。

1. Cloud App Security コンソールで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。

1. **[アプリ コネクター]** ページで、[+] ボタン、 **[Salesforce]** の順にクリックします。

    ![salesforce の接続](media/connect-salesforce.png "Salesforce を接続する")

1. Salesforce の設定ページの API タブで、インストールするインスタンスに応じて **Follow this link (このリンクに移動)** をクリックします。

1. これで Salesforce のサインイン ページが開きます。 Cloud App Security がチームの Salesforce アプリにアクセスできるように、資格情報を入力します。

    ![salesforce のサインイン](media/salesforce-logon.png "Salesforce のログオン")

1. Cloud App Security からチームの情報やアクティビティ ログにアクセスし、任意のチーム メンバーと同様に任意のアクティビティを実行することを許可するかどうかを確認するメッセージが Salesforce で表示されます。 続行するには、 **[許可]** をクリックします。

1. この時点で、デプロイの成功または失敗に関する通知を受信します。 Cloud App Security が Salesforce.com で承認されました。

1. Cloud App Security コンソールに戻ると、Salesforce が正常に接続されたことを示すメッセージが表示されます。

1. **[API のテスト]** をクリックして、正常に接続されたことを確認します。

    テストには数分かかる場合があります。 成功の通知を受信したら、 **[完了]** をクリックします。

Salesforce を接続すると、Salesforce EventMonitoring ライセンスに応じて、接続した時点からのトリガー、接続までの 60 日間のログイン イベントとセットアップ監査証跡、30 日前または 1 日前の EventMonitoring などのイベントを受け取ります。 Cloud App Security API は Salesforce から利用できる API と直接通信します。 Salesforce はそれが受け取る API 呼び出しの数を制限できるため、Cloud App Security はそれを考慮し、制限を順守します。 Salesforce API は、利用できる合計数や残りの数など、API カウンターのフィールドと共に各応答を送信します。 Cloud App Security はこれを百分率に計算し、利用できる API 呼び出しの 10% が常に残るようにします。

> [!NOTE]
> Cloud App Security の調整は、Salesforce で呼び出した Cloud App Security の API に基づいてのみ計算されます。他のアプリケーションが Salesforce で呼び出した API は計算対象になりません。
> API 呼び出しが制限されることで Cloud App Security にデータが取り込まれる速度が遅くなることがありますが、通常、一晩で追いつきます。

Salesforce イベントは Cloud App Security により次のように処理されます。

* 15 分ごとにサインイン イベント
* 15 分ごとにセットアップ監査証跡
* Salesforce のログは、利用状況を 24 時間 (UTC 時刻の午前 00 時 00 分から 午後 11 時 59 分まで ) 追跡します。 Salesforce のイベントは、リアルタイムにログ データを生成します。 ただし、ログ ファイルは、イベントが発生した翌日の非ピーク時に、Salesforce によって生成されます。 そのため、ログ ファイル データはイベントが発生してから少なくとも 1 日は利用できません。 Salesforce のイベントについて詳しくは、「[Using event monitoring](https://developer.salesforce.com/docs/atlas.en-us.api_rest.meta/api_rest/using_resources_event_log_files.htm)」(イベント監視の使用) をご覧ください。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
