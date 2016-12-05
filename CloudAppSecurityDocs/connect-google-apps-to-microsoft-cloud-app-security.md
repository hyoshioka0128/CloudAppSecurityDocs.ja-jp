---
title: "Google Apps の接続 | Microsoft Docs"
description: "このトピックでは、API コネクタを使用して Cloud App Security に Google アプリを接続する方法に関する情報を提供します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/23/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b938e1e0-356d-4cc6-ba4a-862c0c59d709
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6beb9041b338406fb5b16f4bd045dbdc4592c6d9
ms.openlocfilehash: b28eaa521980cb7ec8eee94f0168ca07286533e7


---

# <a name="connect-google-apps-to-microsoft-cloud-app-security"></a>Google Apps を Microsoft Cloud App Security に接続する
このセクションでは、コネクタ API を使用して Cloud App Security を既存の Google Apps に接続する方法を説明します。

  
  
## <a name="configure-google-apps"></a>Google Apps の設定  
  
1.  Google Apps の特権管理者として、[https://cloud.google.com/console/project](https://cloud.google.com/console/project) にログインします。  
  
2.  [**Create an empty project (空のプロジェクトを作成)**] をクリックして新しいプロジェクトを開始します。  
  
     ![google1](./media/google1.png "google1")  
  
3.  [**新しいプロジェクト**] 画面で次の操作を行います。  
  
    1.  プロジェクトに「**Cloud App Security for Google**」という名前を付けます。  
  
    2.  更新をサブスクライブするかどうかを選択します。  
  
    3.  サービスの条件を確認してから承認します。  
  
    4.  [**作成**] をクリックします。  
  
         ![google2](./media/google2.png "google2")  
  
4.  プロジェクトが作成されたら [**Enable and manage APIs (API を有効にして管理)**] をクリックします。  
  
     ![google3](./media/google3.png "google3")  
  
5.  [**Enabled APIs (有効化された API) **] タブをクリックし、リストされているすべての API を無効にします。  
  
     ![google5](./media/google5.png "google5")  
  
6.  **[Google APIs]** タブをクリックして、次の API を有効にします (このとき API が **[Popular APIs]** (よく使用される API) リストに表示されていない場合は、検索行を使用します)。  
  
     ![google8](./media/google8.png "google8")  
  
    > [!NOTE]  
    >  ここでは [**資格情報**] の警告は無視します。  
  
    -   管理 SDK  
  
    -   監査 API  
  
    -   ドライブ API  
  
    -   Google Apps Marketplace SDK  
  
    -   Gmail API  
  
         ![google11 警告](./media/google11-warning.png "google11 warning")  
  
7.  5 つの **有効にされた API** が必要です:  
  
     ![google15](./media/google15.png "google15")  
  
8.  [**資格情報**]、[**OAuth consent (OAuth の承認) **] の順にクリックします。  
  
    -   [**Product name shown to users (製品名をユーザーに表示する)**] で、「**Cloud App Security for Google**」と入力します。  
  
    -   その他のすべてのフィールドは省略できます。  
  
    -   **[Save]**(保存) をクリックします。  
  
     ![google16](./media/google16.png "google16")  
  
9. [**資格情報**] タブで、[**サインイン情報の作成**] の隣にある矢印をクリックしてから [**サービス アカウントのキー**] を選択します。  
  
     ![google17](./media/google17.png "google17")  
  
10. [**サービス アカウント**] で、[**新しいサービス アカウント**] を選択して、たとえば「**Service account 1**」などの任意の名前を入力します。  
  
     ![google19](./media/google19.png "google19")  
  
     [**キーの種類**] で [**P12**] を選択してから [**作成**] をクリックします。  
  
     P12 証明書ファイルがダウンロードされます。 後で使用できるように証明書を保存します。  
  
     ![google20](./media/google20.png "google20")  
  
11. [**資格情報**] タブで、 一番右にある [**Manage service accounts (サービス アカウントの管理)**] をクリックします。  
  
     ![Google Apps の資格情報サービス アカウント](./media/google-apps-credentials-service-account.png "google apps credentials service account")  
  
12. 作成したサービス アカウントの右側にある 3 つの点をクリックし、[**編集**] を選択します。  
  
     ![google22](./media/google22.png "google22")  
  
13. **[Enable Google Apps Domain-wide Delegation]** (Google Apps ドメイン全体の委任を有効にする) チェック ボックスを選択してから **[保存]** をクリックします。  
  
     ![google24](./media/google24.png "google24")  
  
14. サービスに割り当てられている**電子メール アドレス**をコピーしておきます。このアドレスは後で必要になります。  
  
     ![google25](./media/google25.png "google25")  
  
15. Google Cloud Platform の横にある 3 本の水平線アイコンをクリックして Google のメニューを開き、[**API マネージャー**] を選択します。  
  
     ![Google のメニュー](./media/google-menu.png "google menu")  
  
     [**Enabled APIs (有効にされた API)**] を選択します。  
  
     ![google27](./media/google27.png "google27")  
  
16. [**Drive API (ドライブ API) **] の隣にある設定用の歯車アイコンをクリックし、[**Drive UI Integration (UI 統合のドライブ)**] で次を入力します。  
  
    -   **アプリケーション名**: Cloud App Security for Google。  
  
    -   **簡単な説明と詳しい説明**: Microsoft Cloud App Security を使用すると、クラウド アプリケーションの状況を把握できるようになり、クラウド アプリケーションの使用を制御、調査、および管理できるほか、企業データを保護したり、クラウド アプリケーション上での疑わしいアクティビティを検出したりするのに役立ちます。  
  
    -   [**アプリケーション アイコン**] で、サイズが 128 x 128 と 32 × 32 のイメージをアップロードします。  
  
         イメージは [https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip](https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip) にあります。  
  
    -   [**URL を開く**] で次を入力します。  
  
         https://portal.cloudappsecurity.com/#/services/11770?tab=files  
  
    -   [**変更を保存**] をクリックします。  
  
         ![google29](./media/google29.png "google29")  
  
17. **「Enabled APIs」** (有効にされた API) の一覧で、[**Google Apps Marketplace SDK**] の横にある設定用の歯車アイコンをクリックし、[**設定**] タブを選択します。  
  
    -   上部に表示される**プロジェクト番号 (アプリ ID)** を、後で使用できるようにコピーしておきます。  
  
    -   **アプリケーション名**: Cloud App Security for Google。  
  
         [**アプリケーションの説明**] フィールドに、「Microsoft Cloud App Security を使用すると、クラウド アプリケーションの状況が把握できるようになり、クラウド アプリケーションの使用を制御、調査、および管理できるほか、企業データを保護したり、クラウド アプリケーション上での疑わしいアクティビティを検出したりするのに役立ちます」と入力します。  
  
    -   [**Enable individual install (個々のインストールを有効にする)**] チェック ボックスをオフにします。  
  
    -   [**アプリケーション アイコン**] で、4 つの必須イメージを設定します。  
  
         イメージは [https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip](https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip) にあります。  
  
         ![google31](./media/google31.png "google31")  
  
    -   次に [**Support URLs (サポートの URL)**] を入力します:  
  
        -   **サービス利用規約 URL**: http://go.microsoft.com/fwlink/?LinkID=733268  
  
        -   **プライバシー ポリシー URL**: http://go.microsoft.com/fwlink/?LinkId=512132  
  
    -   **[OAuth 2.0 スコープ]** で、次を入力します (1 行に 1 つ入力します。 確認するには Enter キーを押します):  
  
        -   https://www.googleapis.com/auth/admin.reports.audit.readonly  
  
        -   https://www.googleapis.com/auth/admin.reports.usage.readonly  
  
        -   https://www.googleapis.com/auth/drive  
  
        -   https://www.googleapis.com/auth/drive.appdata  
  
        -   https://www.googleapis.com/auth/drive.apps.readonly  
  
        -   https://www.googleapis.com/auth/drive.file  
  
        -   https://www.googleapis.com/auth/drive.metadata.readonly  
  
        -   https://www.googleapis.com/auth/drive.readonly  
  
        -   https://www.googleapis.com/auth/drive.scripts  
  
        -   https://www.googleapis.com/auth/admin.directory.user.readonly  
  
        -   https://www.googleapis.com/auth/admin.directory.user.security  
  
        -   https://www.googleapis.com/auth/admin.directory.user.alias  
  
        -   https://www.googleapis.com/auth/admin.directory.orgunit  
  
        -   https://www.googleapis.com/auth/admin.directory.notifications  
  
        -   https://www.googleapis.com/auth/admin.directory.group.member  
  
        -   https://www.googleapis.com/auth/admin.directory.group  
  
        -   https://www.googleapis.com/auth/admin.directory.device.mobile.action  
  
        -   https://www.googleapis.com/auth/admin.directory.device.mobile  
  
        -   https://www.googleapis.com/auth/admin.directory.user  
  
    -   [**変更を保存**] をクリックします。  
  
18. コントロール リストから [**セキュリティ**] を選択します。 このオプションが表示されない場合は、ページ下部にある灰色のバーからその他のコントロールを選択してから [**セキュリティ**] をクリックします。  
  
     ![Google Apps のセキュリティ](./media/google-apps-security.png "google apps security")  
  
19. [**API リファレンス**] を選択します。  
  
     ![Google の API リファレンス](./media/google-api-ref.png "google api ref")  
  
20. [**Enable API Access (API アクセスの有効化)**] を選択してから [**変更を保存**] をクリックします。  
  
     ![Google の API アクセス](./media/google-api-access.png "google api access")  
  
## <a name="configure-cloud-app-security"></a>Cloud App Security の設定  
  
1.  Cloud App Security ポータルで、**[調査]**、**[接続アプリ]** の順にクリックします。  
  
2.  **[接続アプリ]** ページで、[+]、**[Google Apps]** の順にクリックします。  
  
     ![Google Apps を接続する](./media/connect-google-apps.png "connect google apps")  
  
3.  ポップアップで、以下のように入力します。  
  
     ![Cloud App Security での Google Apps 構成](./media/google-apps-configuration-in-cloud-app-security.png "Google Apps Configuration in Cloud App Security")  
  
    1.  手順 14 でコピーした **Google サービス アカウントの電子メール アドレス**。  
  
    2.  手順 17 でコピーした **Google プロジェクト番号 (アプリ ID)**。  
  
    3.  手順 10 で保存した **Google 証明書** P12 をアップロードします。  
  
    4.  Google Apps 管理者の**管理者の電子メール**を 1 つ入力します。  
  
    5.  Google Apps Unlimited のアカウントがある場合は、このチェック ボックスをオンにします。 Cloud App Security で使用できる Google Apps Unlimited の機能の詳細については、「[Enable instant visibility, protection and governance actions for your apps](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)」 (アプリケーションの表示、保護、およびガバナンス アクションを短時間で有効にする) を参照してください。  
  
    6.  [**設定の保存**] をクリックします。  
  
    7.  [**リンクに移動**] をクリックして Google Apps に接続します。 これで Google Apps が開き、Cloud App Security へのアクセス承認を求められます。  
  
         ![Google Apps の認証要求](./media/google-apps-authorization-request.png "Google Apps authorization request")  
  
    8.  [**API のテスト**] をクリックして、正常に接続されたことを確認します。  
  
         テストには数分かかる場合があります。  
  
         接続成功の通知を受信したら、[**完了**] をクリックして [Google Apps] ページを閉じます。  
  
  
Google Apps に接続すると、接続までの 60 日間のイベントを受け取ります。
  
Google Apps を接続すると、Cloud App Security がフル スキャンを実行します。 所有するファイルとユーザーの数に応じて、フル スキャンの実行に時間がかかる場合があります。 ほぼリアルタイムにスキャンできるように、アクティビティの検出対象ファイルがスキャン キューの先頭に移動されます。たとえば、編集、更新、または共有対象のファイルはすぐにスキャンされ、通常のスキャン プロセスが到達するまで待ちません。 これは本質的に変更されないファイル (表示、プレビュー、印刷またはエクスポート対象のファイルなど) には適用されません。
  
  
## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->


