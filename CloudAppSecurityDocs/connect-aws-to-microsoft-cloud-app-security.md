---
title: "AWS の接続 | Microsoft Docs"
description: "このトピックでは、API コネクタを使用して Cloud App Security に AWS アプリを接続する方法に関する情報を提供します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a6b4c745-cd5c-4458-819c-80cbe8b25f29
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6beb9041b338406fb5b16f4bd045dbdc4592c6d9
ms.openlocfilehash: a56257b7c149c3ea054f200ef88df0ab41b7e25b


---

# <a name="connect-aws-to-microsoft-cloud-app-security"></a>AWS を Microsoft Cloud App Security に接続する
このセクションでは、コネクタ API を使用して Cloud App Security を既存の Amazon Web Services アカウントに接続する方法を説明します。  
  
## <a name="how-to-connect-amazon-web-services-to-cloud-app-security"></a>Amazon Web Services を Cloud App Security に接続する方法  
  
1.  Amazon Web Services コンソールで [**ID およびアクセス管理**] をクリックします。  
  
     ![AWS の ID およびアクセス](./media/aws-identity-and-access.png "aws identity and access")  
  
2.  [**ユーザー**] タブをクリックします。  
  
     ![AWS のユーザー](./media/aws-users.png "aws users")  
  
3.  [**Create New Users (新しいユーザーを作成する)**] をクリックします。  
  
     ![AWS のユーザーの作成](./media/aws-create-user.png "AWS create user")  
  
4.  Cloud App Security の新規ユーザーを作成し、**[Generate an access key for each user]** (各ユーザーのアクセス キーを生成する) チェック ボックスがオンになっていることを確認します。  
  
5.  [**Download Credentials (資格情報をダウンロードする)**] をクリックします。  
  
     ![AWS の資格情報のダウンロード](./media/aws-dl-cred.png "aws dl cred")  
  
6.  **[アクセス許可]** タブで、**[Attach Policy]** (ポリシーのアタッチ) をクリックします。  
  
     ![AWS のユーザーへのポリシーのアタッチ](./media/aws-attach-user-policy.png "aws attach user policy")  
  
7.  **[ポリシーの確認]** 画面が開きます。
 
     ![ポリシーの確認](./media/aws-review-policy.png "aws review policy")  
  

8. **[ポリシー名]** に「AdallomTrustPolicy」と入力します。 
10. **[ポリシー ドキュメント]** で、以下をコピーして貼り付けます。  
  
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
  
9. ダウンロードしたファイル (`credentials.csv`) で新しいユーザーの資格情報を検索します。 これは後でコピーする必要があります。  
  
10. AWS コンソールのメイン ページに戻り、右上隅のドロップダウン ウィンドウで主なリージョンを選択してからメイン メニューで [**CloudTrail**] をクリックします。  
  
     ![AWS の CloudTrail](./media/aws-cloudtrail.png "aws cloudtrail")  
  
    1.  このリージョンで初めて CloudTrail を使用する場合、[**開始する**] ボタンをクリックし、適切な S3 バケットを選択してセットアップします。  
  
         画面左上の [**構成**] タブをクリックします。 [**追加の構成**] で編集アイコンをクリックします。  
  
         ![AWS の CloudTrail 構成](./media/aws-cloudtrail-config.png "aws cloudtrail config")  
  
    2.  [**Include global services (グローバル サービスを含む)**] を選択する画面で [**はい**] をクリックしてから [**保存**] をクリックします。 これは、選択したリージョンにのみ適用されます。  
  
         ![AWS のグローバル サービスを含む](./media/aws-include-global-svc.png "aws include global svc")  
  
    3.  グローバル サービスを含むように設定するすべてのリージョンで手順 11 を繰り返し、それ以外のリージョンではこの設定を適用しないようにします。  
  
11. Cloud App Security ポータルで、**[調査]**、**[接続アプリ]** の順にクリックします。  
  
12. **[アプリ コネクター]** ページで、[+]、**[AWS]** の順にクリックします。  
  
     ![AWS を接続する](./media/connect-aws.png "connect AWS")  
  
13. ポップアップで、csv ファイルから API ページのフィールドに**アクセス キー**と**秘密鍵**を貼り付けて、**[アクセス キーの更新]** をクリックします。  
  
14. [**API のテスト**] をクリックして、正常に接続されたことを確認します。  
  
     テストには数分かかる場合があります。 完了したら、成功または失敗の通知が送信されます。 成功の通知を受信したら、[**完了**] をクリックします。  
  
AWS を接続すると、接続までの 7 日間のイベントを受け取ります。
  
## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->


