---
title: Connect Amazon Web Services with Cloud App Security
description: この記事では、使用状況を視覚化して制御できるように、API コネクタを使用して Cloud App Security に AWS アプリを接続する方法に関する情報を提供します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a6b4c745-cd5c-4458-819c-80cbe8b25f29
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 387a9a9184bb805db7659d6f67eae26239f812f3
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461060"
---
# <a name="connect-aws-to-microsoft-cloud-app-security"></a>AWS を Microsoft Cloud App Security に接続する

*適用対象: Microsoft Cloud App Security*

This article provides instructions for connecting your existing Amazon Web Services (AWS) account to Microsoft Cloud App Security using the connector APIs.

You can connect one or both of the following AWS to Cloud App Security connections:

- **Security auditing**: This connection gives you visibility into and control over AWS app use.
- **Security configuration**: This connection gives you fundamental security recommendations based on the Center for Internet Security (CIS) benchmark for AWS.

Since you can add either or both of the connections, the steps in this article are written as independent instructions. If you have already added one of the connections, where relevant edit the existing configurations.

## <a name="how-to-connect-aws-security-auditing-to-cloud-app-security"></a>How to connect AWS Security auditing to Cloud App Security

1. In your [Amazon Web Services console](https://console.aws.amazon.com/), under **Security, Identity & Compliance**, click **IAM**.

    ![AWS identity and access](media/aws-identity-and-access.png "AWS identity and access")

1. Select **Users** and then click **Add user**.

    ![AWS users](media/aws-users.png "AWS users")

1. **[詳細]** 手順で、Cloud App Security の新しいユーザー名を指定します。 Make sure that under **Access type** you select **Programmatic access** and click **Next Permissions**.<a name="set-permissions"></a>

    ![Create user in AWS](media/aws-create-user.png "Create user in AWS")

1. Click on the **JSON** tab:

    ![AWS JSON tab](media/aws-json.png "AWS JSON tab")

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

     ![AWS code](media/aws-code.png "AWS code")

1. **[ポリシーの確認]** をクリックします。

1. **名前**を付け、 **[ポリシーの作成]** をクリックします。

    ![Provide AWS policy name](media/aws-create-policy.png "Provide AWS policy name")

1. **[ユーザーの追加]** 画面に戻り、必要に応じて一覧を更新し、作成したユーザーを選択して、 **[Next Review]\(次のレビューへ\)** をクリックします。

    ![Attach existing policy in AWS](media/aws-attach-policy.png "Attach existing policy in AWS")

1. すべての詳細情報が正しい場合は、 **[ユーザーの作成]** をクリックします。

    ![User permissions in AWS](media/aws-user-permissions.png "Review user permissions in AWS")

1. 成功メッセージを受け取ったら、 **[Download .csv]\(.csv のダウンロード\)** をクリックし、新しいユーザーの資格情報のコピーを保存します。これは後で必要になります。

    ![Download csv in AWS](media/aws-download-csv.png "Download csv in AWS")

1. AWS コンソールで **[サービス]** をクリックし、 **[管理ツール]** で **[CloudTrail]** をクリックします。

    ![AWS CloudTrail](media/aws-cloudtrail.png "AWS CloudTrail")

    これまでに CloudTrail を使用したことがない場合、 **[開始する]** ボタンをクリックし、名前を入力し、適切な S3 バケットを選択してセットアップします。それから **[オンにする]** をクリックします。 すべてのリージョンに適用するには、 **[Apply to all regions (すべてのリージョンに適用する)]** を **[はい]** に設定します。

    ![Turn on CloudTrail in AWS](media/aws-turnon-cloudtrail.png "Turn on CloudTrail in AWS")

    **[Trails (証跡)]** に新しい CloudTrail 名前が表示されるはずです。

    ![CloudTrail list in AWS](media/aws-cloudtrail-list.png "CloudTrail list in AWS")

    > [!NOTE]
    > AWS を接続すると、接続までの 7 日間のイベントを受け取ります。 If you just enabled CloudTrail, you'll receive events from the time you enabled CloudTrail.

1. Cloud App Security ポータルで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。

1. In the **App connectors** page, to provide the AWS connector credentials, do one of the following:

    **For a new connector**

    1. Click the plus sign followed by **Amazon Web Services**.

        ![connect AWS](media/connect-aws.png "AWS を接続する")

    1. In the pop-up, provide a name for the connector, and then click **Connect Amazon Web Services**.

        ![AWS connector name](media/aws-connect-name.png)

    1. On the Connect Amazon Web services page, select **Security auditing**, paste the **Access key** and **Secret key** from the .csv file into the relevant fields, and click **Connect**.

        ![Connect AWS app security auditing](media/aws-connect-app-audit.png "Connect AWS app security auditing")

    **For an existing connector**

    1. In the list of connectors, on the row in which the AWS connector appears, click **Connect security auditing**.

        ![Screenshot of the Connected Apps page, showing edit Security Auditing link](media/aws-connect-app-edit-audit.png)

    1. On the Connect Amazon Web Services page, paste the **Access key** and **Secret key** from the .csv file into the relevant fields, and click **Connect**.

        ![Connect AWS app security auditing](media/aws-connect-app-edit-audit-creds.png "Connect AWS app security auditing")

1. **[API のテスト]** をクリックして、正常に接続されたことを確認します。  

    テストには数分かかる場合があります。 完了したら、成功または失敗の通知を受け取ります。 成功の通知を受信したら、 **[完了]** をクリックします。

## <a name="how-to-connect-aws-security-configuration-to-cloud-app-security"></a>How to connect AWS Security configuration to Cloud App Security

Follow the [How to connect AWS Security auditing](#how-to-connect-aws-security-auditing-to-cloud-app-security) steps to get to the [permissions](#set-permissions) page.

1. On the permissions page, click **Attach existing policies directly**, apply the **AWSSecurityHubReadOnlyAccess** and **SecurityAudit** policies, and then click **Next Tags**.

    ![Attach existing policy in AWS](media/aws-attach-policy.png "Attach existing policy in AWS")

1. Optional: Add tags to the user.

    ![Add tags to user in AWS](media/aws-add-tags.png)

    > [!NOTE]
    > Adding tags to the user won't affect the connection.

1. Click **Next Review**.

1. すべての詳細情報が正しい場合は、 **[ユーザーの作成]** をクリックします。

    ![User permissions in AWS](media/aws-user-permissions.png "Review user permissions in AWS")

1. When you get the success message, click **Download .csv** to save a copy of the **Access key ID** and the **Secret access key**, you need these later.

    ![Download csv in AWS](media/aws-download-csv.png "Download csv in AWS")

1. Cloud App Security ポータルで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。

1. In the **App connectors** page, to provide the AWS connector credentials, do one of the following:

    **For a new connector**
    1. Click the plus sign followed by **Amazon Web Services**.<br>

        ![connect AWS](media/connect-aws.png "AWS を接続する")

    1. In the pop-up, provide a name for the connector, and then click **Connect Amazon Web Services**.

        ![AWS connector name](media/aws-connect-name.png)

    1. On the Connect Amazon Web services page, select **Security configuration**, paste the **Access key** and **Secret key** from the .csv file into the relevant fields, and click **Connect**.

        ![Connect AWS app security configuration](media/aws-connect-app-config.png "Connect AWS app security configuration")

    **For an existing connector**
    1. In the list of connectors, on the row in which the AWS connector appears, click **Connect security configuration**.

        ![Screenshot of the Connected Apps page, showing edit Security Configuration link](media/aws-connect-app-edit-config.png)

    1. On the Connect Amazon Web Services page, paste the **Access key** and **Secret key** from the .csv file into the relevant fields, and click **Connect**.

        ![Connect AWS app security configuration](media/aws-connect-app-edit-config-creds.png "Connect AWS app security configuration")

1. **[API のテスト]** をクリックして、正常に接続されたことを確認します。  

    テストには数分かかる場合があります。 完了したら、成功または失敗の通知を受け取ります。 成功の通知を受信したら、 **[完了]** をクリックします。

## <a name="next-steps"></a>次のステップ

[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]