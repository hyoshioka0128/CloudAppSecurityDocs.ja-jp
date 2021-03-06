---
title: Cloud App Security を使用したアマゾンウェブサービスの接続
description: この記事では、使用状況を視覚化して制御できるように、API コネクタを使用して Cloud App Security に AWS アプリを接続する方法に関する情報を提供します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 01/06/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 3441f2b78c015ba38185ca2c584a347985b9a71f
ms.sourcegitcommit: 00599ac6c64a4c62ed9ebdda3edb58f90f92c24d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912255"
---
# <a name="connect-aws-to-microsoft-cloud-app-security"></a>AWS を Microsoft Cloud App Security に接続する

*適用対象: Microsoft Cloud App Security*

この記事では、コネクタ Api を使用して、既存のアマゾンウェブサービス (AWS) アカウントを Microsoft Cloud App Security に接続する手順について説明します。 Cloud App Security で AWS を保護する方法の詳細については、「 [PROTECT AWS](protect-aws.md)」を参照してください。

Cloud App Security 接続には、次のいずれかまたは両方の AWS を接続できます。

- **セキュリティ監査**: この接続により、AWS アプリの使用を可視化し、制御することができます。
- **[セキュリティの構成]** : この接続は、AWS の Internet SECURITY (ci) ベンチマークベンチマークに基づいて、基本的なセキュリティの推奨事項を提供します。

接続のいずれかまたは両方を追加できるため、この記事の手順は独立した指示として記述されています。 接続のいずれかを既に追加している場合は、関連する既存の構成を編集します。

## <a name="how-to-connect-aws-security-auditing-to-cloud-app-security"></a>AWS セキュリティ監査を Cloud App Security に接続する方法

1. [アマゾンウェブサービスコンソール](https://console.aws.amazon.com/)で、[**セキュリティ]、[id & コンプライアンス**] の順にクリックし、 **[IAM]** をクリックします。

    ![AWS の id とアクセス](media/aws-identity-and-access.png "AWS の id とアクセス")

1. **[ユーザー]** を選択し、 **[ユーザーの追加]** をクリックします。

    ![AWS ユーザー](media/aws-users.png "AWS ユーザー")

1. **[詳細]** 手順で、Cloud App Security の新しいユーザー名を指定します。 **[アクセスの種類]** で **[プログラムによるアクセス]** を選択し、 **[次のアクセス許可]** をクリックします。<a name="set-permissions"></a>

    ![AWS でのユーザーの作成](media/aws-create-user.png "AWS でのユーザーの作成")

1. **[JSON]** タブをクリックします。

    ![AWS JSON タブ](media/aws-json.png "AWS JSON タブ")

1. 与えられた領域に次のスクリプトを貼り付けます。

    ```json
    {
      "Version" : "2012-10-17",
      "Statement" : [{
          "Action" : [
            "cloudtrail:DescribeTrails",
            "cloudtrail:LookupEvents",
            "cloudtrail:GetTrailStatus",
            "cloudwatch:Describe*",
            "cloudwatch:Get*",
            "cloudwatch:List*",
            "iam:List*",
            "iam:Get*",
            "s3:ListAllMyBuckets",
            "s3:PutBucketAcl",
            "s3:GetBucketAcl",
            "s3:GetBucketLocation"
          ],
          "Effect" : "Allow",
          "Resource" : "*"
        }
      ]
     }
    ```

     ![AWS コード](media/aws-code.png "AWS コード")

1. **[ポリシーの確認]** をクリックします。

1. **名前**を付け、 **[ポリシーの作成]** をクリックします。

    ![AWS ポリシー名を指定する](media/aws-create-policy.png "AWS ポリシー名を指定する")

1. **[ユーザーの追加]** 画面に戻り、必要に応じて一覧を更新し、作成したユーザーを選択して、 **[Next Review]\(次のレビューへ\)** をクリックします。

    ![AWS で既存のポリシーをアタッチする](media/aws-attach-policy.png "AWS で既存のポリシーをアタッチする")

1. すべての詳細情報が正しい場合は、 **[ユーザーの作成]** をクリックします。

    ![AWS でのユーザーのアクセス許可](media/aws-user-permissions.png "AWS でのユーザーのアクセス許可の確認")

1. 成功メッセージを受け取ったら、 **[Download .csv]\(.csv のダウンロード\)** をクリックし、新しいユーザーの資格情報のコピーを保存します。これは後で必要になります。

    ![AWS で csv をダウンロードする](media/aws-download-csv.png "AWS で csv をダウンロードする")

1. AWS コンソールで **[サービス]** をクリックし、 **[管理ツール]** で **[CloudTrail]** をクリックします。

    ![AWS CloudTrail](media/aws-cloudtrail.png "AWS CloudTrail")

    これまでに CloudTrail を使用したことがない場合、 **[開始する]** ボタンをクリックし、名前を入力し、適切な S3 バケットを選択してセットアップします。それから **[オンにする]** をクリックします。 すべてのリージョンに適用するには、 **[Apply to all regions (すべてのリージョンに適用する)]** を **[はい]** に設定します。

    ![AWS で CloudTrail を有効にする](media/aws-turnon-cloudtrail.png "AWS で CloudTrail を有効にする")

    **[Trails (証跡)]** に新しい CloudTrail 名前が表示されるはずです。

    ![AWS の CloudTrail リスト](media/aws-cloudtrail-list.png "AWS の CloudTrail リスト")

    > [!NOTE]
    > AWS を接続すると、接続までの 7 日間のイベントを受け取ります。 CloudTrail を有効にしたばかりの場合は、CloudTrail を有効にした時点からイベントを受信します。

1. Cloud App Security ポータルで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。

1. **[アプリコネクタ]** ページで、AWS コネクタの資格情報を指定するには、次のいずれかの操作を行います。

    **新しいコネクタの場合**

    1. プラス記号をクリックし、次に**アマゾンウェブサービス**をクリックします。

        ![AWS の接続](media/connect-aws.png "AWS を接続する")

    1. ポップアップで、コネクタの名前を指定し、 **[アマゾンウェブサービスの接続]** をクリックします。

        ![AWS コネクタ名](media/aws-connect-name.png)

    1. Amazon Web services の接続 ページで **セキュリティ監査** を選択し、.csv ファイルから関連するフィールドに**アクセスキー**と**秘密キー**を貼り付けて、**接続** をクリックします。

        ![Connect AWS app security auditing](media/aws-connect-app-audit.png "Connect AWS app security auditing")

    **既存のコネクタの場合**

    1. コネクタの一覧で、AWS コネクタが表示されている行の **[セキュリティ監査の接続]** をクリックします。

        ![[セキュリティ監査の編集] リンクが表示されている [接続済みアプリ] ページのスクリーンショット](media/aws-connect-app-edit-audit.png)

    1. [アマゾンウェブサービスの接続] ページで、.csv ファイルの**アクセスキー**と**秘密キー**を関連フィールドに貼り付け、 **[接続]** をクリックします。

        ![Connect AWS app security auditing](media/aws-connect-app-edit-audit-creds.png "Connect AWS app security auditing")

1. **[API のテスト]** をクリックして、正常に接続されたことを確認します。  

    テストには数分かかる場合があります。 完了したら、成功または失敗の通知を受け取ります。 成功の通知を受信したら、 **[完了]** をクリックします。

## <a name="how-to-connect-aws-security-configuration-to-cloud-app-security"></a>AWS セキュリティ構成を Cloud App Security に接続する方法

AWS セキュリティ構成を接続することで、AWS のインターネットセキュリティ (CI) ベンチマークに基づいて、基本的なセキュリティの推奨事項を把握できます。

AWS のセキュリティ構成を Cloud App Security に接続するには、次の手順に従います。

> [!div class="checklist"]
>
> - [AWS Security Hub のセットアップ](#set-up-aws-security-hub)
> - [AWS のセキュリティ構成を Cloud App Security に接続する](#connect-aws-security-configuration-to-cloud-app-security)

### <a name="set-up-aws-security-hub"></a>AWS Security Hub のセットアップ

複数のリージョンのセキュリティに関する推奨事項を表示するには、該当するリージョンごとに次の手順を繰り返します。

> [!NOTE]
> マスターアカウントを使用している場合は、これらの手順を繰り返して、関連するすべてのリージョンでマスターアカウントとすべての接続されたメンバーアカウントを構成します。

1. [AWS Config](https://docs.aws.amazon.com/config/latest/developerguide/gs-console.html)を有効にします。
1. [AWS セキュリティハブ](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-settingup.html)を有効にします。
1. セキュリティハブにデータが流れていることを確認します。

    > [!NOTE]
    > Security Hub を初めて有効にすると、データが使用可能になるまでに数時間かかることがあります。

### <a name="connect-aws-security-configuration-to-cloud-app-security"></a>AWS のセキュリティ構成を Cloud App Security に接続する

AWS セキュリティ構成に接続する前に、セキュリティとコンプライアンスに関する基本的な推奨事項を収集するように[AWS 環境を設定](#set-up-aws-security-hub)しておく必要があります。

> [!NOTE]
> [AWS マスターアカウント](https://aws.amazon.com/security-hub/faqs/)を使用している場合は、次の手順を使用して、マスターアカウントに接続します。 マスターアカウントに接続すると、すべてのリージョンのすべてのメンバーアカウントに関する推奨事項を受け取ることができます。

1. 「 *How to CONNECT AWS Security auditing* 」の手順に従って、[[アクセス許可](#set-permissions)] ページに移動します。

1. アクセス許可 ページで、**既存のポリシーを直接接続**する をクリックし、 **AWSSecurityHubReadOnlyAccess**ポリシーと**securityaudit**ポリシーを適用して、**次のタグ** をクリックします。

    ![AWS で既存のポリシーをアタッチする](media/aws-attach-policy.png "AWS で既存のポリシーをアタッチする")

1. 省略可能: ユーザーにタグを追加します。

    ![AWS のユーザーにタグを追加する](media/aws-add-tags.png)

    > [!NOTE]
    > ユーザーにタグを追加しても、接続には影響しません。

1. **[次のレビュー]** をクリックします。

1. すべての詳細情報が正しい場合は、 **[ユーザーの作成]** をクリックします。

    ![AWS でのユーザーのアクセス許可](media/aws-user-permissions.png "AWS でのユーザーのアクセス許可の確認")

1. 成功メッセージが表示されたら、 **[.csv のダウンロード]** をクリックして**アクセスキー ID**と**シークレットアクセスキー**のコピーを保存します。後で必要になります。

    ![AWS で csv をダウンロードする](media/aws-download-csv.png "AWS で csv をダウンロードする")

1. Cloud App Security ポータルで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。

1. **[アプリコネクタ]** ページで、AWS コネクタの資格情報を指定するには、次のいずれかの操作を行います。

    **新しいコネクタの場合**

    1. プラス記号をクリックし、次に**アマゾンウェブサービス**をクリックします。<br />

        ![AWS の接続](media/connect-aws.png "AWS を接続する")

    1. ポップアップで、コネクタの名前を指定し、 **[アマゾンウェブサービスの接続]** をクリックします。

        ![AWS コネクタ名](media/aws-connect-name.png)

    1. Amazon Web services の接続 ページで、**セキュリティの構成** を選択し、.csv ファイルから関連するフィールドに**アクセスキー**と**秘密鍵**を貼り付けて、**接続** をクリックします。

        ![Connect AWS app security の構成](media/aws-connect-app-config.png "Connect AWS app security の構成")

    **既存のコネクタの場合**

    1. コネクタの一覧で、AWS コネクタが表示されている行の **[セキュリティ構成の接続]** をクリックします。

        ![[セキュリティ構成の編集] リンクが表示されている [接続済みアプリ] ページのスクリーンショット](media/aws-connect-app-edit-config.png)

    1. [アマゾンウェブサービスの接続] ページで、.csv ファイルの**アクセスキー**と**秘密キー**を関連フィールドに貼り付け、 **[接続]** をクリックします。

        ![Connect AWS app security の構成](media/aws-connect-app-edit-config-creds.png "Connect AWS app security の構成")

1. **[API のテスト]** をクリックして、正常に接続されたことを確認します。  

    テストには数分かかる場合があります。 完了したら、成功または失敗の通知を受け取ります。 成功の通知を受信したら、 **[完了]** をクリックします。

アプリの接続で問題が発生した場合は、「[アプリコネクタのトラブルシューティング](troubleshooting-api-connectors-using-error-messages.md)」を参照してください。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
