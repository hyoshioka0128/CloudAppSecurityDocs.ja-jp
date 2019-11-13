---
title: Cloud App Security への Google Cloud Platform の接続
description: この記事では、API コネクタを使用して Cloud App Security に Google Cloud Platform を接続する方法について説明します。これにより、使用状況を表示して制御できます。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: cloud-app-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 27d32ca6daf7221d84b0cb0942d42c3555049e43
ms.sourcegitcommit: b48842b6622bd45af66afbffc70f92d31ec232a8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73934482"
---
# <a name="connect-google-cloud-platform-to-microsoft-cloud-app-security-preview"></a>Microsoft Cloud App Security への Google Cloud Platform の接続 (プレビュー)

*適用対象: Microsoft Cloud App Security*

この記事では、コネクタ Api を使用して Microsoft Cloud App Security を既存の Google Cloud Platform (GCP) アカウントに接続する手順について説明します。 この接続により、GCP の使用を可視化し、制御することができます。

> [!NOTE]
> GCP 環境を接続するための手順は、集計されたログを使用するための[Google の推奨事項](https://cloud.google.com/blog/products/gcp/best-practices-for-working-with-google-cloud-audit-logging)に従います。 統合は Google StackDriver を活用し、課金に影響する可能性のある追加のリソースを消費します。 消費されたリソースは次のとおりです。
>
> * [集約されたエクスポートシンク-組織レベル](https://cloud.google.com/logging/docs/export/aggregated_exports#concept)
> * [Pub/Sub トピック– GCP プロジェクトレベル](https://cloud.google.com/logging/docs/export/using_exported_logs#pubsub-overview)
> * [Pub/Sub サブスクリプション– GCP プロジェクトレベル](https://cloud.google.com/logging/docs/export/using_exported_logs#pubsub-overview)
>
> 現時点では、Cloud App Security 管理アクティビティの監査ログのみをインポートします。データアクセスとシステムイベントの監査ログはインポートされません。 GCP ログの詳細については、「[クラウド監査ログ](https://go.microsoft.com/fwlink/?linkid=2109230)」を参照してください。

統合には専用のプロジェクトを使用し、安定した統合を維持し、セットアッププロセスが削除または変更されないように、プロジェクトへのアクセスを制限することをお勧めします。 また、GCP インスタンスが既に Cloud App Security に接続されている G Suite インスタンスの一部である場合は、GCP 接続の詳細を追加するときに、**接続された g suite 組織の手順に含まれる GCP インスタンス**のに従うことをお勧めします。

## <a name="prerequisites"></a>必要条件

統合 GCP ユーザーには、次のアクセス許可が必要です。

* **IAM と管理者**による編集–組織レベル
* **プロジェクトの作成と編集**

## <a name="configure-google-cloud-platform"></a>Google Cloud Platform の構成

* 統合 GCP ユーザーアカウントを使用して、GCP ポータルにサインインします。

### <a name="create-a-dedicated-project"></a>専用プロジェクトを作成する

組織で GCP に専用のプロジェクトを作成して、統合の分離と安定性を実現する

1. **[プロジェクトの作成]** をクリックして、新しいを開始します。
1. **[新しいプロジェクト]** 画面で、プロジェクトに名前を指定し、 **[作成]** をクリックします。

    ![GCP のプロジェクトの作成ダイアログを示すスクリーンショット](media/connect-gcp-create-project.png)

### <a name="enable-the-pubsub-api"></a>Pub/Sub API を有効にする

1. 専用プロジェクトに切り替えます。
1. [Pub/Sub] タブにアクセスします。サービスアクティベーションメッセージが表示されます。

### <a name="create-a-dedicated-service-account-for-the-integration"></a>統合用の専用サービスアカウントを作成する

1. **[IAM & admin]** で、 **[サービスアカウント]** をクリックします。
1. **[サービスアカウントの作成]** をクリックして、専用のサービスアカウントを作成します。
1. アカウント名を入力し、 **[作成]** をクリックします。
1. **ロール**として「 **Pub/Sub Admin** 」と指定し、 **[保存]** をクリックします。

    ![GCP add IAM ロールを示すスクリーンショット](media/connect-gcp-iam-role.PNG)

1. **電子メール**の値をコピーします。後で必要になります。

    ![GCP サービスアカウントダイアログを示すスクリーンショット](media/connect-gcp-create-service-account.png)

1. **[Iam & admin]** で、 **[iam]** をクリックします。

    1. 組織レベルに切り替えます。
    1. **[追加]** をクリックします。
    1. **[新しいメンバー]** ボックスに、前の手順でコピーした**電子メール**の値を貼り付けます。
    1. **[ロール]** として「 **Logs Configuration Writer** 」と指定し、 **[保存]** をクリックします。

        ![[メンバーの追加] ダイアログを示すスクリーンショット](media/connect-gcp-add-member.png)

### <a name="create-a-private-key-for-the-dedicated-service-account"></a>専用サービスアカウントの秘密キーを作成する

1. プロジェクトレベルに切り替えます。
1. **[IAM & admin]** で、 **[サービスアカウント]** をクリックします。
1. 専用サービスアカウントを開き、 **[編集]** をクリックします。
1. **[キーの作成]** をクリックします。
1. **[秘密キーの作成]** 画面で、 **[JSON]** を選択し、 **[作成]** をクリックします。

    ![秘密キーの作成ダイアログを示すスクリーンショット](media/connect-gcp-create-private-key.png)

    > [!NOTE]
    > 後でコンピューターにダウンロードされる JSON ファイルが必要になります。

### <a name="retrieve-your-organization-id"></a>組織 ID を取得する

**組織 ID**をメモしておきます。後で必要になります。 詳細については、「[組織 ID を取得する](https://cloud.google.com/resource-manager/docs/creating-managing-organization#retrieving_your_organization_id)」を参照してください。
    ![組織 ID ダイアログ](media/connect-gcp-org-id.png) を示すスクリーンショット

## <a name="configure-cloud-app-security"></a>Cloud App Security の設定

* Cloud App Security ポータルで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。

### <a name="add-the-gcp-connection-details"></a>GCP 接続の詳細を追加する

GCP 接続の詳細を指定するには、 **[アプリコネクタ]** の下で、次のいずれかの操作を行います。

**接続された G Suite 組織の一部ではない GCP インスタンスの場合**

1. プラス記号をクリックし、次に**Google Cloud Platform**をクリックします。

    ![[Add GCP] メニューを示すスクリーンショット](media/connect-gcp-add.png)

1. ポップアップで、コネクタの名前を指定し、 **[Google Cloud Platform の接続]** をクリックします。

1. [Google Cloud Platform] ページで、次の操作を行います。
    1. **[組織 ID]** ボックスに、事前にメモしておいた組織を入力します。
    1. **[秘密キーファイル]** ボックスで、前の手順でダウンロードした JSON ファイルを参照します。
    1. **[接続 Google Cloud Platform]** をクリックします。

    > [!NOTE]
    > ユーザー管理とガバナンスを統合するには、G Suite インスタンスを接続することをお勧めします。 これは、G Suite 製品を使用せず、GCP ユーザーが G Suite ユーザー管理システムを介して管理されている場合でも推奨されます。

**接続された G Suite 組織の一部である GCP インスタンスの場合**

1. 接続されたインスタンスの一覧で、G Suite コネクタが表示されている行の末尾にある3つのドットをクリックし、 **[Google Cloud Platform の追加]** をクリックします。

1. [Google Cloud Platform] ページで、次の操作を行います。
    1. **[組織 ID]** ボックスに、事前にメモしておいた組織を入力します。
    1. **[秘密キーファイル]** ボックスで、前の手順でダウンロードした JSON ファイルを参照します。
    1. **[接続 Google Cloud Platform]** をクリックします。

    > [!NOTE]
    > これにより、G Suite ユーザー id 領域を使用して、統合されたユーザー管理とガバナンスを実現できます。

### <a name="test-the-connection"></a>接続をテストする

**[API のテスト]** をクリックして、正常に接続されたことを確認します。

テストには数分かかる場合があります。 完了したら、成功または失敗の通知を受け取ります。 成功の通知を受信したら、 **[完了]** をクリックします。

## <a name="aggregated-export-sink"></a>集計されたエクスポートシンク

現時点では、集計エクスポートシンクの無効化は Google Cloud Shell 経由でのみ可能です。

### <a name="to-disable-aggregated-export-sink"></a>集計されたエクスポートシンクを無効にするには

| 手順 | スクリプト | 詳細情報 |
|-|-|-|
| 1. Google Cloud Shell セッションを開始します。 | | [Cloud Shell の使用](https://cloud.google.com/shell/docs/using-cloud-shell) |
| 2. 現在のプロジェクトを設定します。 | `gcloud config set project {PROJECT_ID}` | [gcloud 構成セット](https://cloud.google.com/sdk/gcloud/reference/config/set) |
| 3. 組織レベルのシンクを一覧表示します。 | `gcloud logging sinks list --organization={ORGANIZATION_ID}` | [gcloud ログシンクの一覧](https://cloud.google.com/sdk/gcloud/reference/logging/sinks/list) |
| 4. 関連するシンクを削除します。 | `gcloud logging sinks delete {SINK_NAME} --organization={ORGANIZATION_ID}` | [gcloud ログシンクの削除](https://cloud.google.com/sdk/gcloud/reference/logging/sinks/delete) |

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)
