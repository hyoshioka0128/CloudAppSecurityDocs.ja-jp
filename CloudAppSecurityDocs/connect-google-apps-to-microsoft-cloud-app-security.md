---
title: "G Suite を Cloud App Security に接続して使用状況を表示し、管理する | Microsoft Docs"
description: "このトピックでは、API コネクタを使用して Cloud App Security に G Suite を接続する方法に関する情報を提供します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/4/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b938e1e0-356d-4cc6-ba4a-862c0c59d709
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: af60110859b027a9e9d58443f202752d6044d1a2
ms.sourcegitcommit: f9851779aa15b11f559e56ac818f1333f027c000
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2017
---
# <a name="connect-g-suite-to-microsoft-cloud-app-security"></a>G Suite を Microsoft Cloud App Security に接続する
このセクションでは、コネクタ API を使用して Cloud App Security を既存の G Suite アカウントに接続する方法を説明します。

  
  
## <a name="configure-g-suite"></a>G Suite を構成する  
  
1.  G Suite の特権管理者として、[https://cloud.google.com/console/project](https://cloud.google.com/console/project) にログインします。  
  
2.  **[プロジェクトの作成]** をクリックして新しいプロジェクトを開始します。  
  
     ![google1](./media/google1.png "google1")  
  
3.  **[新しいプロジェクト]** 画面で、プロジェクトに</br>
    **Microsoft Cloud App Security** という名前を付け、**[作成]** をクリックします。  
           ![google2](./media/google2.png "google2")  
  
4.  プロジェクトが作成されたら、ツール バーで、Google Cloud Platform の隣にあるプロジェクトを選択し、**[API]** で **[Go to APIs overview (API 概要に進む)]** をクリックします。  
  
     ![google3](./media/google3.png "google3")  
  
5.  **[API]** で、一覧に表示されているすべての API を無効にします。  
      
6.  **[ライブラリ]** タブをクリックし、次の API を有効にします (API が **[Popular APIs (よく使用される API)]** リストに表示されていない場合、検索行を使用します)。  
  
     ![Google API](./media/google4.png "google4")  
  
    > [!NOTE]  
    >  ここでは [**資格情報**] の警告は無視します。  
  
    -   管理 SDK  
  
    -   監査 API  
  
    -   Google ドライブ API  
  
    -   Google Apps Marketplace SDK  
  
    -   Gmail API  
            
7.  5 つの **有効にされた API** が必要です:  
  
     ![Google の有効にされた API](./media/google5.png "google5")  
  
8.  **[資格情報]** をクリックします。**[OAuth consent (OAuth の承認)]** 画面が表示されます。  
  
    -   [**Product name shown to users**]\(製品名をユーザーに表示する\) で、「**Microsoft Cloud App Security**」と入力します。  
  
    -   その他のすべてのフィールドは省略できます。  
  
    -   **[Save]**(保存) をクリックします。  
  
     ![Google の製品名](./media/google6.png "google6")  
  
9. **[API Credentials (API 資格情報)]** 画面で、**[サインイン情報の作成]** の隣にある矢印をクリックします。  
  
     ![Google の資格情報](./media/google7.png "google7")  

10. **[サービス アカウント キー]** を選択します。

     ![Google サービス アカウント キー](./media/google8.png "google8")  
  
11. **[Create service account key (サービス アカウント キー)]** で **[新しいサービス アカウント]** を選択し、名前を入力します。たとえば、「**Service account 1**」とします。**[ロール]** で **[プロジェクト]**、**[エディター]** の順に選択し、**[キーの種類]** で **[P12]** を選択し、**[作成]** をクリックします。 **[Enable G Suite Domain-wide Delegation (G Suite ドメイン全体の委任を有効にする)]** チェック ボックスを選択し、**[保存]** をクリックします。  
  
     ![Google のサービス アカウント キーの作成](./media/google9.png "google9")  
  
12.  P12 証明書ファイルがコンピューターに保存されます。  
        
12. [**資格情報**] 画面で、一番右にある [**Manage service accounts (サービス アカウントの管理)**] をクリックします。  
       ![G Suite の資格情報サービス アカウント](./media/google10.png "G Suite の資格情報サービス アカウント")  
  
13. 作成したサービス アカウントの右側にある 3 つの点をクリックし、[**編集**] を選択します。  
  
     ![Google 編集](./media/google11.png "google edit")  
  
15. サービスに割り当てられている**サービス アカウント ID** をコピーします。この ID は後で必要になります。  
  
     ![Google のサービス アカウント ID](./media/google13.png "google13")  
  
16. Google Cloud Platform のタイトル バーの横にある 3 本の水平線アイコンをクリックして Google のメニューを開き、[**API マネージャー**] を選択します。**ダッシュボード**が表示されます。  
    
17. 下にスクロールして有効になっている API の一覧を表示し、**Google ドライブ API** の隣にある歯車の形をした設定アイコンをクリックします。   
       ![Google ドライブ選択](./media/google14.png "google14")  

18. 次の項目に入力します。

    -   **アプリケーション名**: Microsoft Cloud App Security。  
  
    -   **簡単な説明と詳しい説明** (省略可能): Microsoft Cloud App Security を使用すると、クラウド アプリケーションの状況を把握できるようになり、クラウド アプリケーションの使用を制御、調査、および管理できるほか、企業データを保護したり、クラウド アプリケーション上での疑わしいアクティビティを検出したりするのに役立ちます。  
  
    -   Google から、少なくとも 1 つのアプリケーション アイコンをアップロードするように要求されます。 [https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip](https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip) にアクセスし、Cloud App Security アイコンが入っている zip ファイルをダウンロードします。 [**アプリケーション アイコン**] で、サイズが 128 x 128 と 32 × 32 のイメージをドラッグ アンド ドロップします。  
  
    -   **[Drive Integration (ドライブ統合)]** の **[URL を開く]** に次を入力します。  
  
         https://portal.cloudappsecurity.com/#/services/11770?tab=files  
     
         ![Google のドライブ構成](./media/google15.png "googledriveconfig")  
  
19. **[Enabled APIs (有効にされた API)]** 一覧で、**[Google Apps Marketplace SDK]** の横にある設定用の歯車アイコンをクリックします。 
         ![Google Marketplace SDK 構成](./media/google16.png "googledriveconfig")  

       >[!NOTE]
       > 歯車アイコンが無効になっている場合は、**[Google Apps Marketplace SDK]** を代わりにクリックしてもかまいません。 
20. **[構成]** タブを選択します。 
  
    -   上部に表示される**プロジェクト番号 (アプリ ID)** を、後で使用できるようにコピーしておきます。  
  
    -   **[アプリケーション名]** は **Microsoft Cloud App Security** になります。
  
         [**アプリケーションの説明**] フィールドに、「Microsoft Cloud App Security を使用すると、クラウド アプリケーションの状況が把握できるようになり、クラウド アプリケーションの使用を制御、調査、および管理できるほか、企業データを保護したり、クラウド アプリケーション上での疑わしいアクティビティを検出したりするのに役立ちます」と入力します。  
  
    -   [**Enable individual install (個々のインストールを有効にする)**] チェック ボックスをオフにします。  
  
    -   [**アプリケーション アイコン**] で、4 つの必須イメージを設定します。  
  
         イメージは [https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip](https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip) にあります。  
  
         ![Google Marketplace SDK 構成](./media/google17.png "google17")  
  
    -   次に [**Support URLs (サポートの URL)**] を入力します:  
  
        -   **サービス利用規約 URL**: http://go.microsoft.com/fwlink/?LinkID=733268  
  
        -   **プライバシー ポリシー URL**: http://go.microsoft.com/fwlink/?LinkId=512132  
  
    -   **[OAuth 2.0 スコープ]** で次をコピーし、貼り付けます。 一度に 1 つずつコピーする必要があります。1 つコピーしたら Enter を押してください。  
  
           https://www.googleapis.com/auth/admin.reports.audit.readonly  
  
           https://www.googleapis.com/auth/admin.reports.usage.readonly  
  
           https://www.googleapis.com/auth/drive  
  
           https://www.googleapis.com/auth/drive.appdata  
  
           https://www.googleapis.com/auth/drive.apps.readonly  
  
           https://www.googleapis.com/auth/drive.file  
  
           https://www.googleapis.com/auth/drive.metadata.readonly  
  
           https://www.googleapis.com/auth/drive.readonly  
  
           https://www.googleapis.com/auth/drive.scripts  
  
           https://www.googleapis.com/auth/admin.directory.user.readonly  
  
           https://www.googleapis.com/auth/admin.directory.user.security  
  
           https://www.googleapis.com/auth/admin.directory.user.alias  
  
           https://www.googleapis.com/auth/admin.directory.orgunit  
  
           https://www.googleapis.com/auth/admin.directory.notifications  
  
           https://www.googleapis.com/auth/admin.directory.group.member  
  
           https://www.googleapis.com/auth/admin.directory.group  
  
           https://www.googleapis.com/auth/admin.directory.device.mobile.action  
  
           https://www.googleapis.com/auth/admin.directory.device.mobile  
  
           https://www.googleapis.com/auth/admin.directory.user  
  
    -   [**変更を保存**] をクリックします。  
  
18. [admin.google.com](https://admin.google.com/) にアクセスし、**[セキュリティ]** を選択します。 
       ![Google セキュリティ](./media/googlesecurity.png "google8")  
 
19. [**API リファレンス**] を選択します。  
       ![Google API 有効化](./media/googleapi.png "google8")  
      
20. [**Enable API Access (API アクセスの有効化)**] を選択してから [**変更を保存**] をクリックします。  
  
    ![Google API 参照](./media/googleapiref.png "google8")  

  
## <a name="configure-cloud-app-security"></a>Cloud App Security の設定  
  
1.  Cloud App Security ポータルで、**[調査]**、**[接続アプリ]** の順にクリックします。  
  
2.  **[接続アプリ]** ページで、プラス記号をクリックし、**[G Suite]** を選択します。  
       
  
3.  ポップアップで、次の項目に入力します。  
  
     ![Cloud App Security での G Suite 構成](./media/gsuite-config-cas.png "Cloud App Security での G Suite 構成")  
  
    1.  手順 16 でコピーした**サービス アカウントの電子メール アドレス**。  
  
    2.  手順 21 でコピーした**プロジェクト番号 (アプリ ID)**。  
  
    3.  手順 12 で保存した**証明書** P12 をアップロードします。 保存しておいたパスワードがここで必要になります。  
  
    4.  G Suite 管理者の**管理者アカウントの電子メール**を 1 つ入力します。  
  
    5.  G Suite Unlimited のアカウントがある場合、このチェック ボックスをオンにします。 Cloud App Security で使用できる G Suite Unlimited の機能の詳細については、[アプリの表示、保護、ガバナンスの操作をすぐに実行できるようにする](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)方法に関するページを参照してください。  
  
    6.  [**設定の保存**] をクリックします。  
  
    7.  **[リンクに移動]** をクリックし、G Suite に接続します。 これで G Suite が開き、Cloud App Security へのアクセス承認を求められます。  
         
    8.  [**今すぐテスト**] をクリックし、正常に接続されたことを確認します。  
  
         テストには数分かかる場合があります。  
  
         接続成功の通知を受信したら、**[完了]** をクリックして [G Suite] ページを閉じます。  
  
  
G Suite を接続すると、接続までの 60 日間のイベントを受け取ります。
  
G Suite を接続すると、Cloud App Security がフル スキャンを実行します。 所有するファイルとユーザーの数に応じて、フル スキャンの実行に時間がかかる場合があります。 ほぼリアルタイムにスキャンできるように、アクティビティの検出対象ファイルがスキャン キューの先頭に移動されます。たとえば、編集、更新、または共有対象のファイルはすぐにスキャンされ、通常のスキャン プロセスが到達するまで待ちません。 これは本質的に変更されないファイル (表示、プレビュー、印刷またはエクスポート対象のファイルなど) には適用されません。
  
  
## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  