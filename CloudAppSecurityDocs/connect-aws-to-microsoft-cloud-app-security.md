---
title: "AWS を Cloud App Security に接続して使用状況を表示し、管理する | Microsoft Docs"
description: "このトピックでは、API コネクタを使用して Cloud App Security に AWS アプリを接続する方法に関する情報を提供します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/25/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a6b4c745-cd5c-4458-819c-80cbe8b25f29
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: bb0703442d3568556dc54df5e1bd7901906ca9b3
ms.sourcegitcommit: 8759541301241e03784c5ac87b56986f22bd0561
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/28/2017
---
# <a name="connect-aws-to-microsoft-cloud-app-security"></a>AWS を Microsoft Cloud App Security に接続する
このセクションでは、コネクタ API を使用して Cloud App Security を既存の Amazon Web Services アカウントに接続する方法を説明します。  
  
## <a name="how-to-connect-amazon-web-services-to-cloud-app-security"></a>Amazon Web Services を Cloud App Security に接続する方法  
  
1.  [アマゾン ウェブ サービス コンソール](https://console.aws.amazon.com/)の **[Security, Identity & Compliance (セキュリティ、ID、コンプライアンス)]** で **[IAM]** をクリックします。  
  
     ![AWS の ID とアクセス](./media/aws-identity-and-access.png "AWS の ID とアクセス")  
  
2.  **[ユーザー]** タブをクリックし、**[ユーザーの追加]** をクリックします。  
  
     ![AWS ユーザー](./media/aws-users.png "AWS ユーザー")      
  
4.  **[詳細]** 手順で、Cloud App Security の新しいユーザー名を指定します。 **[アクセスの種類]** で必ず **[プログラムによるアクセス]** を選択して、**[Next Permissions]\(次のアクセス許可へ\)** をクリックします。  

     ![AWS でのユーザー作成](./media/aws-create-user.png "AWS でのユーザー作成")

5. **[アクセス許可]** 手順で、**[Attach existing policies directly (既存のポリシーを直接アタッチする)]** を選択し、**[ポリシーの作成]** をクリックします。

   ![AWS でユーザーをアタッチ ](./media/aws-attach-user-policy.png "AWS でユーザー ポリシーをアタッチ")

6.  **[ポリシーの作成]** で **[Create Your Own Policy (独自のポリシーを作成する)]** を選択します。
 
    ![AWS で独自のポリシーを作成](./media/aws-create-own-policy.png "AWS でポリシーを作成")
 
7.  **[ポリシーの確認]** の **[ポリシー名]** に入力します。たとえば、「CloudAppSecurityPolicy」と入力します。

    ![AWS でポリシーを確認](./media/aws-review-policy.png "AWS でポリシーを確認")

8. **[Policy Document]\(ポリシー ドキュメント\)** フィールドに次のスクリプトを貼り付け、**[ポリシーの作成]** をクリックします。
  
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
            "iam:Get*"  
          ],  
          "Effect" : "Allow",  
          "Resource" : "*"  
        }  
      ]  
     }  
  
    ```  
  
9. **[ユーザーの追加]** 画面に戻り、必要に応じて一覧を更新し、作成したユーザーを選択して、**[Next Review]\(次のレビューへ\)** をクリックします。

   ![AWS でユーザー ポリシーを確認](./media/aws-review-user.png "AWS 内のユーザーを確認")

10. すべての詳細情報が正しい場合は、**[ユーザーの作成]** をクリックします。

    ![AWS でのユーザー アクセス許可](./media/aws-user-permissions.png "AWS でのユーザー アクセス許可の確認")

11. 成功メッセージを受け取ったら、**[Download .csv]\(.csv のダウンロード\)** をクリックし、新しいユーザーの資格情報のコピーを保存します。これは後で必要になります。  

    ![AWS で csv をダウンロード](./media/aws-download-csv.png "AWS で csv をダウンロード")
  
10. AWS コンソールで **[サービス]** をクリックし、**[管理ツール]** で **[CloudTrail]** をクリックします。  
  
     ![AWS CloudTrail](./media/aws-cloudtrail.png "AWS CloudTrail")  
  
    初めて CloudTrail を使用する場合、[**開始する**] ボタンをクリックし、名前を入力し、適切な S3 バケットを選択してセットアップします。それから **[オンにする]** をクリックします。 すべてのリージョンに適用するには、**[Apply to all regions (すべてのリージョンに適用する)]** を **[はい]** に設定します。
  
       ![AWS で CloudTrail の有効化](./media/aws-turnon-cloudtrail.png "AWS で CloudTrail の有効化")
  
    **[Trails (証跡)]** に新しい CloudTrail 名前が表示されるはずです。
    
      ![AWS の CloudTrail 一覧](./media/aws-cloudtrail-list.png "AWS の CloudTrail 一覧")
  
11. Cloud App Security ポータルで、**[調査]**、**[接続アプリ]** の順にクリックします。  
  
12. **[アプリ コネクター]** ページで、[+]、**[AWS]** の順にクリックします。  
  
     ![AWS の接続](./media/connect-aws.png "AWS の接続")  
  
13. ポップアップで、csv ファイルから関連フィールドに**アクセス キー**と**秘密鍵**を貼り付けて、**[接続]** をクリックします。  
   ![AWS アプリに接続](./media/aws-connect-app.png "AWS アプリに接続") 
  
14. [**API のテスト**] をクリックして、正常に接続されたことを確認します。  
  
     テストには数分かかる場合があります。 完了したら、成功または失敗の通知を受信します。 成功の通知を受信したら、[**完了**] をクリックします。  
  
AWS を接続すると、接続までの 7 日間のイベントを受け取ります。 CloudTrail を有効にしただけであれば、CloudTrail を有効にした時点からイベントを受け取ります。
  
## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  