---
title: AWS と Cloud App Security を接続する
description: この記事では、使用状況を視覚化して制御できるように、API コネクタを使用して Cloud App Security に AWS アプリを接続する方法に関する情報を提供します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a6b4c745-cd5c-4458-819c-80cbe8b25f29
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c85b55d52de91d58fccaba2241008ef5be6beca2
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53176129"
---
# <a name="connect-aws-to-microsoft-cloud-app-security"></a>AWS を Microsoft Cloud App Security に接続する

*適用対象:Microsoft Cloud App Security*

この記事では、コネクタ API を使用して Microsoft Cloud App Security を既存のアマゾン ウェブ サービス アカウントに接続する方法を説明します。 この接続により、AWS アプリの使用状況を視覚化して制御できるようになります。 
  
## <a name="how-to-connect-amazon-web-services-to-cloud-app-security"></a>Amazon Web Services を Cloud App Security に接続する方法  
  
1.  [アマゾン ウェブ サービス コンソール](https://console.aws.amazon.com/)の **[Security, Identity & Compliance (セキュリティ、ID、コンプライアンス)]** で **[IAM]** をクリックします。  
  
     ![AWS の ID とアクセス](./media/aws-identity-and-access.png "AWS の ID とアクセス")  
  
2.  **[ユーザー]** タブをクリックし、**[ユーザーの追加]** をクリックします。  
  
     ![AWS ユーザー](./media/aws-users.png "AWS ユーザー")      
  
4.  **[詳細]** 手順で、Cloud App Security の新しいユーザー名を指定します。 **[アクセスの種類]** で必ず **[プログラムによるアクセス]** を選択して、**[Next Permissions]\(次のアクセス許可へ\)** をクリックします。  

     ![AWS でのユーザー作成](./media/aws-create-user.png "AWS でのユーザー作成")

5. [JSON] タブをクリックします。

     ![AWS JSON](./media/aws-json.png "AWS JSON タブ")

6. 与えられた領域に次のスクリプトを貼り付けます。

    ```     
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

     ![AWS コード](./media/aws-code.png "AWS コード")
    
6. **[ポリシーの確認]** をクリックします。

7. **名前**を付け、**[ポリシーの作成]** をクリックします。

     ![AWS 名のポリシー](./media/aws-create-policy.png "AWS 名のポリシー")

9. **[ユーザーの追加]** 画面に戻り、必要に応じて一覧を更新し、作成したユーザーを選択して、**[Next Review]\(次のレビューへ\)** をクリックします。

   ![AWS でユーザー ポリシーを確認](./media/aws-review-user.png "AWS 内のユーザーを確認")

10. すべての詳細情報が正しい場合は、**[ユーザーの作成]** をクリックします。

    ![AWS でのユーザー アクセス許可](./media/aws-user-permissions.png "AWS でのユーザー アクセス許可の確認")

11. 成功メッセージを受け取ったら、**[Download .csv]\(.csv のダウンロード\)** をクリックし、新しいユーザーの資格情報のコピーを保存します。これは後で必要になります。  

    ![AWS で csv をダウンロード](./media/aws-download-csv.png "AWS で csv をダウンロード")
  
10. AWS コンソールで **[サービス]** をクリックし、**[管理ツール]** で **[CloudTrail]** をクリックします。  
  
     ![AWS CloudTrail](./media/aws-cloudtrail.png "AWS CloudTrail")  
  
    これまでに CloudTrail を使用したことがない場合、**[開始する]** ボタンをクリックし、名前を入力し、適切な S3 バケットを選択してセットアップします。それから **[オンにする]** をクリックします。 すべてのリージョンに適用するには、**[Apply to all regions (すべてのリージョンに適用する)]** を **[はい]** に設定します。
  
       ![AWS で CloudTrail の有効化](./media/aws-turnon-cloudtrail.png "AWS で CloudTrail の有効化")
  
    **[Trails (証跡)]** に新しい CloudTrail 名前が表示されるはずです。
    
      ![AWS の CloudTrail 一覧](./media/aws-cloudtrail-list.png "AWS の CloudTrail 一覧")
  
11. Cloud App Security ポータルで、**[調査]**、**[接続アプリ]** の順にクリックします。  
  
12. **[アプリ コネクタ]** ページで、[+]、**[アマゾン ウェブ サービス]** の順にクリックします。  
  
     ![AWS の接続](./media/connect-aws.png "AWS の接続")  
  
13. ポップアップで、csv ファイルから関連フィールドに**アクセス キー**と**秘密鍵**を貼り付けて、**[接続]** をクリックします。  
   ![AWS アプリに接続](./media/aws-connect-app.png "AWS アプリに接続") 
  
14. **[API のテスト]** をクリックして、正常に接続されたことを確認します。  
  
     テストには数分かかる場合があります。 完了したら、成功または失敗の通知を受け取ります。 成功の通知を受信したら、**[完了]** をクリックします。  
  
AWS を接続すると、接続までの 7 日間のイベントを受け取ります。 CloudTrail を有効にしただけであれば、CloudTrail を有効にした時点からイベントを受け取ります。
  
## <a name="next-steps"></a>次の手順  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
  