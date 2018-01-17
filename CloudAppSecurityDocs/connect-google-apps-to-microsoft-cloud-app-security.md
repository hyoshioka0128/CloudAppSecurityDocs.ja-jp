---
title: "G Suite を Cloud App Security に接続して使用状況を表示し、管理する | Microsoft Docs"
description: "このトピックでは、API コネクタを使用して Cloud App Security に G Suite を接続する方法に関する情報を提供します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b938e1e0-356d-4cc6-ba4a-862c0c59d709
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 1742fbaae18fe4624bf057e54b9e11d2d68c5335
ms.sourcegitcommit: c4b40afff6a66b101fadfc1bd221c10186bad71a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2018
---
# <a name="connect-g-suite-to-microsoft-cloud-app-security"></a>G Suite を Microsoft Cloud App Security に接続する
このセクションでは、コネクタ API を使用して Cloud App Security を既存の G Suite アカウントに接続する方法を説明します。
  
  
## <a name="configure-g-suite"></a>G Suite を構成する  
  
1.  G Suite の特権管理者として、<a href="https://cloud.google.com/console/project" target="_blank">https://cloud.google.com/console/project</a> にログインします。  
  
2.  **[プロジェクトの作成]** をクリックして新しいプロジェクトを開始します。  
  
     ![google1](./media/google1.png "google1")  
  
3.  **[新しいプロジェクト]** 画面で、プロジェクトに</br>
    **Microsoft Cloud App Security** という名前を付け、**[作成]** をクリックします。  
           ![google2](./media/google2.png "google2")  
  
4.  プロジェクトが作成された後、ツール バーで **[Google Cloud Platform]** をクリックして、上部のドロップ ダウンで適切なプロジェクトが選ばれていることを確認します。
       
       ![google プロジェクト](./media/googleverify-project.png "googleverify プロジェクト")  

5. **[API]** で、**[Go to APIs overview]**/(API 概要に進む/) をクリックします。  
  
     ![google3](./media/google3.png "google3")  
  
6.  **[API]** で、一覧に表示されているすべての API を無効にします。  
      
7.  **[ライブラリ]** タブをクリックし、次の API を有効にします (API が **[Popular APIs (よく使用される API)]** リストに表示されていない場合、検索行を使用します)。  
     
    -   管理 SDK  
  
    -   監査 API  
  
    -   Google ドライブ API  
  
    -   Google Apps Marketplace SDK  
  
    -   Gmail API  
            
 ![Google API](./media/google4.png "google4")  
  
   > [!NOTE]  
   >  ここでは **[資格情報]** の警告は無視します。  

8.  5 つの **有効にされた API** が必要です:  
  
     ![Google の有効にされた API](./media/google5.png "google5")  
  
9.  **[Credentials]**/(認証情報/) を選択して、**[OAuth consent screen]**/(OAuth 同意画面/) タブを選択します。
  
    -   **[Product name shown to users]**\(製品名をユーザーに表示する\) で、「**Microsoft Cloud App Security**」と入力します。  
  
    -   その他のすべてのフィールドは省略できます。  
  
    -   **[Save]**(保存) をクリックします。  
  
     ![Google の製品名](./media/google6.png "google6")  
  
10. **[Credentials]**/(認証情報/) タブで、**[Create credentials]**/(認証情報の作成/) の隣にある矢印をクリックします。  
  
     ![Google の資格情報](./media/google7.png "google7")  

11. **[サービス アカウント キー]** を選択します。

     ![Google サービス アカウント キー](./media/google8.png "google8")  
  
12. **[Create service account key]\(サービス アカウント キーの作成\)** で、**[New service account]\(新しいサービス アカウント\)** を選択して、「**Service account 1**」などの任意の名前を入力します。 **[ロール]** で、**[プロジェクト]**、**[エディター]** と選択します。 **[キーの種類]** で **[P12]** を選択してから **[作成]** をクリックします。 P12 証明書ファイルがコンピューターに保存されます。
 
     ![Google でのサービス アカウント キーの作成](./media/google9.png "google9")  
  
13.  サービスに割り当てられている**サービス アカウント ID** をコピーします。この ID は後で必要になります。    
        
14. **[資格情報]** 画面で、一番右にある **[Manage service accounts (サービス アカウントの管理)]** をクリックします。  
     
    ![G Suite の資格情報サービス アカウント](./media/google10.png "G Suite の資格情報サービス アカウント")  
  
15. 作成したサービス アカウントの右側にある 3 つの点をクリックし、**[編集]** を選択します。  
  
     ![Google 編集](./media/google11.png "google edit")  
  
16. **[Enable G Suite Domain-wide Delegation (G Suite ドメイン全体の委任を有効にする)]** チェック ボックスを選択し、**[保存]** をクリックします。  
  
     ![Google のサービス アカウント ID](./media/google12.png "google12")  
  
17. タイトルバーで Google Cloud Platform の横にある 3 本の水平線をクリックして Google のメニューを開きます。 **[Google Cloud Platform]** をクリックし、左側のメニューの **[APIs and services**]/(API とサービス/) タブをクリックします。  
    
18. 開いているダッシュボードで、下にスクロールして有効になっている API の一覧を表示し、**[Google ドライブ API]** をクリックします。   
       ![Google ドライブを選択](./media/google14.png "google14")  

19. **[Drive UI 統合]**/(Drive UI 統合/) タブをクリックし、次の情報を入力します。

    -   **アプリケーション名**: Microsoft Cloud App Security。  
  
    -   **簡単な説明と詳しい説明** (省略可能): Microsoft Cloud App Security を使用すると、クラウド アプリケーションの状況を把握できるようになり、クラウド アプリケーションの使用を制御、調査、および管理できるほか、企業データを保護したり、クラウド アプリケーション上での疑わしいアクティビティを検出したりするのに役立ちます。  
  
    -   Google から、少なくとも 1 つのアプリケーション アイコンをアップロードするように要求されます。 [https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826) に移動して、Cloud App Security のアイコンを含む zip ファイルをダウンロードします。 次に、**[Application icon]\(アプリケーション アイコン\)** で 128x128 のイメージの横にある **[Select]\(選択\)** をクリックし、ポップアップ画面にドラッグします。 32x32 のイメージの横にある **[Select]\(選択\)** をクリックして、ポップアップ画面にドラッグします。  
  
    -   下にスクロールして **[Drive Integration]**/(ドライブ統合/)セクションを表示し、**[Open URL]**/(URL を開く/) に次の URL を入力します。  
  
         https://portal.cloudappsecurity.com/#/services/11770?tab=files  
    
       ![Google ドライブの編集](./media/google15.png "google15")  

20. **[変更を保存]** をクリックします。

20. **[Enabled APIs]**/(有効にされた API/) の一覧に戻ります。 **[Google Apps Marketplace SDK]** をクリックします。 
      
21. **[構成]** タブを選択します。 
  
    -   上部に表示される**プロジェクト番号 (アプリ ID)** を、後で使用できるようにコピーしておきます。  
  
    -   **[アプリケーション名]** で、「**Microsoft Cloud App Security**」と入力します。
  
         **[アプリケーションの説明]** に、「Microsoft Cloud App Security を使用すると、クラウド アプリケーションの状況が把握できるようになり、クラウド アプリケーションの使用を制御、調査、および管理できるほか、企業データを保護したり、クラウド アプリケーション上での疑わしいアクティビティを検出したりするのに役立ちます」と入力します。  
  
    -   **[Enable individual install (個々のインストールを有効にする)]** チェック ボックスをオフにします。  
  
    -   **[アプリケーション アイコン]** で、4 つの必須イメージを設定します。  
  
         イメージは、[https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826) から探すことができます。  
  
    -   次に **[Support URLs (サポートの URL)]** を入力します:  
  
        -   **サービス利用規約 URL**: http://go.microsoft.com/fwlink/?LinkID=733268  
  
        -   **プライバシー ポリシー URL**: http://go.microsoft.com/fwlink/?LinkId=512132  
  
    -   **[OAuth 2.0 scopes]\(OAuth 2.0 スコープ\)** で、以下の URL をコピーして貼り付けます (1 つコピーするたびに Enter キーを押します)。  
  
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

    -   G Suite で可視性のメッセージが表示されたら、**[My domain]\(独自ドメイン\)** (パブリックではありません) を選択します。 
    -   **[変更を保存]** をクリックします。  
  
22. [admin.google.com](https://admin.google.com/) にアクセスし、**[セキュリティ]** を選択します。 
   
      ![Google セキュリティ](./media/googlesec.png "Google セキュリティ")  
 
23. **[API リファレンス]** を選択します。  
       ![Google API 有効化](./media/googleapi.png "google api")  
      
24. **[Enable API Access (API アクセスの有効化)]** を選択してから **[変更を保存]** をクリックします。  
  
    ![Google API 参照](./media/googleapiref.png "google8")  

  
## <a name="configure-cloud-app-security"></a>Cloud App Security の設定  
  
1.  Cloud App Security ポータルで、**[調査]**、**[接続アプリ]** の順にクリックします。  
  
2.  **[接続アプリ]** ページで、プラス記号をクリックし、**[G Suite]** を選択します。  
       
  
3.  ポップアップで、次の情報を入力します。  
  
     ![Cloud App Security での G Suite 構成](./media/gsuite-config-cas.png "Cloud App Security での G Suite 構成")  
  
    1.  手順 13 でコピーした**サービス アカウント ID**。  
  
    2.  手順 21 でコピーした**プロジェクト番号 (アプリ ID)**。  
  
    3.  手順 12 で保存した**証明書** P12 をアップロードします。 保存しておいたパスワードがここで必要になります。  
  
    4.  G Suite 管理者の**管理者アカウントの電子メール**を 1 つ入力します。  
  
    5.  G Suite Unlimited のアカウントがある場合、このチェック ボックスをオンにします。 Cloud App Security で使用できる G Suite Unlimited の機能の詳細については、[アプリの表示、保護、ガバナンスの操作をすぐに実行できるようにする](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)方法に関するページをご覧ください。  
  
    6.  **[設定の保存]** をクリックします。  
  
    7.  **[リンクに移動]** をクリックし、G Suite に接続します。 これにより G Suite が開き、Cloud App Security へのアクセス承認を求められます。  
         
    8.  **[今すぐテスト]** をクリックし、正常に接続されたことを確認します。  
  
         テストには数分かかる場合があります。  
  
         接続成功の通知を受信したら、**[完了]** をクリックして [G Suite] ページを閉じます。  
  
  
G Suite を接続すると、接続までの 60 日間のイベントを受け取ります。
  
G Suite を接続すると、Cloud App Security がフル スキャンを実行します。 所有するファイルとユーザーの数に応じて、フル スキャンの実行に時間がかかる場合があります。 ほぼリアルタイムのスキャンを有効にするために、アクティビティが検出されたファイルはスキャン キューの先頭に移動されます。 たとえば、編集、更新、または共有されたファイルはすぐにスキャンされます。 これは、本質的に変更されていないファイルには適用されません。 たとえば、表示、プレビュー、印刷、またはエクスポートされたファイルは、定期スキャンのときにスキャンされます。
  
  
## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  