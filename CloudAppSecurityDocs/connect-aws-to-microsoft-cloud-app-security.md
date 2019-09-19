---
title: Cloud App Security を使用したアマゾンウェブサービスの接続
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
ms.openlocfilehash: 34e1c361d5b1a49093f927dfde1ae2391570b958
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083828"
---
# <a name="connect-aws-to-microsoft-cloud-app-security"></a>AWS を Microsoft Cloud App Security に接続する

*適用対象:Microsoft Cloud App Security*

この記事では、コネクタ Api を使用して、既存のアマゾンウェブサービス (AWS) アカウントを Microsoft Cloud App Security に接続する手順について説明します。

Cloud App Security 接続には、次のいずれかまたは両方の AWS を接続できます。

- **セキュリティ監査**:この接続により、AWS アプリの使用状況を視覚化して制御できるようになります。
- **セキュリティ構成**:この接続では、AWS 用の Internet Security (CI) ベンチマークに基づく基本的なセキュリティの推奨事項が提供されます。

接続のいずれかまたは両方を追加できるため、この記事の手順は独立した指示として記述されています。 接続のいずれかを既に追加している場合は、関連する既存の構成を編集します。

## <a name="how-to-connect-aws-security-auditing-to-cloud-app-security"></a>AWS セキュリティ監査を Cloud App Security に接続する方法

1. [アマゾンウェブサービスコンソール](https://console.aws.amazon.com/)で、[**セキュリティ]、[id & コンプライアンス**] の順にクリックし、 **[IAM]** をクリックします。

    ![AWS の ID とアクセス](media/aws-identity-and-access.png "AWS の ID とアクセス")

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

    ![AWS ポリシー名を指定]する(media/aws-create-policy.png "AWS ポリシー名を指定")する

1. **[ユーザーの追加]** 画面に戻り、必要に応じて一覧を更新し、作成したユーザーを選択して、 **[Next Review]\(次のレビューへ\)** をクリックします。

    ![AWS で既存のポリシーをアタッチ]する(media/aws-attach-policy.png "AWS で既存のポリシーをアタッチ")する

1. すべての詳細情報が正しい場合は、 **[ユーザーの作成]** をクリックします。

    ![AWS でのユーザー アクセス許可](media/aws-user-permissions.png "AWS でのユーザー アクセス許可の確認")

1. 成功メッセージを受け取ったら、 **[Download .csv]\(.csv のダウンロード\)** をクリックし、新しいユーザーの資格情報のコピーを保存します。これは後で必要になります。

    ![AWS で csv をダウンロード](media/aws-download-csv.png "AWS で csv をダウンロード")

1. AWS コンソールで **[サービス]** をクリックし、 **[管理ツール]** で **[CloudTrail]** をクリックします。

    ![AWS CloudTrail](media/aws-cloudtrail.png "AWS CloudTrail")

    これまでに CloudTrail を使用したことがない場合、 **[開始する]** ボタンをクリックし、名前を入力し、適切な S3 バケットを選択してセットアップします。それから **[オンにする]** をクリックします。 すべてのリージョンに適用するには、 **[Apply to all regions (すべてのリージョンに適用する)]** を **[はい]** に設定します。

    ![AWS で CloudTrail の有効化](media/aws-turnon-cloudtrail.png "AWS で CloudTrail の有効化")

    **[Trails (証跡)]** に新しい CloudTrail 名前が表示されるはずです。

    ![AWS の CloudTrail 一覧](media/aws-cloudtrail-list.png "AWS の CloudTrail 一覧")

    > [!NOTE]
    > AWS を接続すると、接続までの 7 日間のイベントを受け取ります。 CloudTrail を有効にしたばかりの場合は、CloudTrail を有効にした時点からイベントを受信します。

1. Cloud App Security ポータルで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。

1. **[アプリコネクタ]** ページで、AWS コネクタの資格情報を指定するには、次のいずれかの操作を行います。

    **新しいコネクタの場合**

    1. プラス記号をクリックし、次に**アマゾンウェブサービス**をクリックします。

        ![AWS の接続](media/connect-aws.png "AWS の接続")

    1. ポップアップで、コネクタの名前を指定し、 **[アマゾンウェブサービスの接続]** をクリックします。

        ![AWS コネクタ名](media/aws-connect-name.png)

    1. Amazon Web services の接続 ページで **セキュリティ監査** を選択し、.csv ファイルから関連するフィールドに**アクセスキー**と**秘密キー**を貼り付けて、**接続** をクリックします。

        ![CONNECT AWS app security auditing](media/aws-connect-app-audit.png "CONNECT AWS app security auditing")

    **既存のコネクタの場合**

    1. コネクタの一覧で、AWS コネクタが表示されている行の **[セキュリティ監査の接続]** をクリックします。

        ![[セキュリティ監査の編集] リンクが表示されている [接続済みアプリ] ページのスクリーンショット](media/aws-connect-app-edit-audit.png)

    1. [アマゾンウェブサービスの接続] ページで、.csv ファイルの**アクセスキー**と**秘密キー**を関連フィールドに貼り付け、 **[接続]** をクリックします。

        ![CONNECT AWS app security auditing](media/aws-connect-app-edit-audit-creds.png "CONNECT AWS app security auditing")

1. **[API のテスト]** をクリックして、正常に接続されたことを確認します。  

    テストには数分かかる場合があります。 完了したら、成功または失敗の通知を受け取ります。 成功の通知を受信したら、 **[完了]** をクリックします。

## <a name="how-to-connect-aws-security-configuration-to-cloud-app-security"></a>AWS セキュリティ構成を Cloud App Security に接続する方法

「 [How to CONNECT AWS Security auditing](#how-to-connect-aws-security-auditing-to-cloud-app-security) 」の手順に従って、[[アクセス許可](#set-permissions)] ページに移動します。

1. アクセス許可 ページで、**既存のポリシーを直接接続**する をクリックし、 **AWSSecurityHubReadOnlyAccess**ポリシーと**securityaudit**ポリシーを適用して、**次のタグ** をクリックします。

    ![AWS で既存のポリシーをアタッチ]する(media/aws-attach-policy.png "AWS で既存のポリシーをアタッチ")する

1. 省略可能:ユーザーにタグを追加します。

    ![AWS のユーザーにタグを追加する](media/aws-add-tags.png)

    > [!NOTE]
    > ユーザーにタグを追加しても、接続には影響しません。

1. **[次のレビュー]** をクリックします。

1. すべての詳細情報が正しい場合は、 **[ユーザーの作成]** をクリックします。

    ![AWS でのユーザー アクセス許可](media/aws-user-permissions.png "AWS でのユーザー アクセス許可の確認")

1. 成功メッセージが表示されたら、 **[.csv のダウンロード]** をクリックして**アクセスキー ID**と**シークレットアクセスキー**のコピーを保存します。後で必要になります。

    ![AWS で csv をダウンロード](media/aws-download-csv.png "AWS で csv をダウンロード")

1. Cloud App Security ポータルで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。

1. **[アプリコネクタ]** ページで、AWS コネクタの資格情報を指定するには、次のいずれかの操作を行います。

    **新しいコネクタの場合**
    1. プラス記号をクリックし、次に**アマゾンウェブサービス**をクリックします。<br>

        ![AWS の接続](media/connect-aws.png "AWS の接続")

    1. ポップアップで、コネクタの名前を指定し、 **[アマゾンウェブサービスの接続]** をクリックします。

        ![AWS コネクタ名](media/aws-connect-name.png)

    1. Amazon Web services の接続 ページで、**セキュリティの構成** を選択し、.csv ファイルから関連するフィールドに**アクセスキー**と**秘密鍵**を貼り付けて、**接続** をクリックします。

        ![CONNECT AWS app security の構成](media/aws-connect-app-config.png "CONNECT AWS app security の構成")

    **既存のコネクタの場合**
    1. コネクタの一覧で、AWS コネクタが表示されている行の **[セキュリティ構成の接続]** をクリックします。

        ![[セキュリティ構成の編集] リンクが表示されている [接続済みアプリ] ページのスクリーンショット](media/aws-connect-app-edit-config.png)

    1. [アマゾンウェブサービスの接続] ページで、.csv ファイルの**アクセスキー**と**秘密キー**を関連フィールドに貼り付け、 **[接続]** をクリックします。

        ![CONNECT AWS app security の構成](media/aws-connect-app-edit-config-creds.png "CONNECT AWS app security の構成")

1. **[API のテスト]** をクリックして、正常に接続されたことを確認します。  

    テストには数分かかる場合があります。 完了したら、成功または失敗の通知を受け取ります。 成功の通知を受信したら、 **[完了]** をクリックします。

## <a name="next-steps"></a>次の手順

[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)