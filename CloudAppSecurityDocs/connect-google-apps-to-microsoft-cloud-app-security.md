---
title: G Suite を Cloud App Security に接続する
description: この記事では、使用状況を視覚化して制御できるように、API コネクタを使用して Cloud App Security に G Suite を接続する方法に関する情報を提供します。
keywords: ''
author: ShlomoSagir-MS
ms.author: ShlomoSagir-MS
manager: ShlomoSagir-MS
ms.date: 6/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b938e1e0-356d-4cc6-ba4a-862c0c59d709
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fd1330b48919b41ac528e754095652a6c041052d
ms.sourcegitcommit: 24d93184339bf2642411472a03d5d25e48d2bf86
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2019
ms.locfileid: "67171012"
---
# <a name="connect-g-suite-to-microsoft-cloud-app-security"></a>G Suite を Microsoft Cloud App Security に接続する

*適用対象:Microsoft Cloud App Security*

この記事では、コネクタ API を使用して Microsoft Cloud App Security を既存の G Suite アカウントに接続する方法を説明します。 この接続により、G Suite の使用状況を視覚化して制御できるようになります。 
    
## <a name="configure-g-suite"></a>G Suite を構成する  
  
1. G Suite のスーパー管理者として、<a href="https://cloud.google.com/console/project" target="_blank">https://cloud.google.com/console/project</a> にサインインします。  
  
2. **[プロジェクトの作成]** をクリックして新しいプロジェクトを開始します。  
  
    ![google1](./media/google1.png "google1")  
  
3. **[新しいプロジェクト]** 画面で、プロジェクトに</br>
   **Cloud App Security**クリック**作成**です。  
          ![google2](./media/google2.png "google2")  
  
4. プロジェクトが作成されたら、ツール バーの **[Google Cloud Platform]** をクリックします。 上部にあるドロップダウン リストで適切なプロジェクトが選択されていることを確認します。
       
      ![google プロジェクト](./media/googleverify-project.png "googleverify プロジェクト")  

5. [ **Api**、] をクリックして**API の概要に移動**します。  
  
     ![google3](./media/google3.png "google3")  
   
6. **[ライブラリ]** をクリックし、次の API を有効にします (API が **[Popular APIs]\(よく使用される API\)** リストに表示されていない場合、検索行を使用します)。  

   -   管理 SDK  
  
   -   監査 API
  
   -   Google ドライブ API
  
   -   G Suite Marketplace SDK

   ![Google API](./media/google4.png "google4")  
  
   > [!NOTE]  
   >  ここでは **[資格情報]** の警告は無視します。  

7. 各 API に対して [有効] をクリックします。
     ![Google API を有効にする](./media/google-api.png "google-api")  
8. 次の API が有効になっていることを確認します。
  
     ![Google の有効にされた API](./media/google5.png "google5")  
  
9. **[Credentials]** /(認証情報/) を選択して、 **[OAuth consent screen]** /(OAuth 同意画面/) タブを選択します。
  
    - **[Product name shown to users]** \(製品名をユーザーに表示する\) で、「**Microsoft Cloud App Security**」と入力します。  
  
    - その他のすべてのフィールドは省略できます。  
  
    - **[Save]** (保存) をクリックします。  
  
      ![Google oauth 同意](./media/google-oauth-consent.png "google oauth 同意")  
  
10. **[Credentials]** /(認証情報/) タブで、 **[Create credentials]** /(認証情報の作成/) の隣にある矢印をクリックします。  
  
     ![Google の資格情報](./media/google7.png "google7")  

11. **[サービス アカウント キー]** を選択します。

     ![Google サービス アカウント キー](./media/google8.png "google8")  
  
12. **[Create service account key]\(サービス アカウント キーの作成\)** で、 **[New service account]\(新しいサービス アカウント\)** を選択して、「**Service account 1**」などの任意の名前を入力します。 **[ロール]** で、 **[プロジェクト]** 、 **[エディター]** と選択します。 **[キーの種類]** で **[P12]** を選択してから **[作成]** をクリックします。 P12 証明書ファイルがコンピューターに保存されます。
 
     ![Google でのサービス アカウント キーの作成](./media/google9.png "google9")  
  
13. サービスに割り当てられている**サービス アカウント ID** をコピーします。この ID は後で必要になります。
        
14. **[資格情報]** 画面で、一番右にある **[Manage service accounts (サービス アカウントの管理)]** をクリックします。  
     
    ![G Suite の資格情報サービス アカウント](./media/google10.png "G Suite の資格情報サービス アカウント")  
  
15. 作成したサービス アカウントの右側にある 3 つの点をクリックし、 **[編集]** を選択します。  
  
     ![Google 編集](./media/google11.png "google edit")  
  
16. クリックして**ビュー ドメイン全体の委任のクライアント ID**します。
  
     ![google クライアント ID](./media/google12.png "google12") 

    -   コピー、**クライアント ID** -後で必要です。

    -   [admin.google.com](https://admin.google.com/) にアクセスし、 **[セキュリティ]** を選択します。

    -   選択**詳細を表示する**選び、**詳細設定**します。

    -   **認証**セクションで、**管理 API のクライアント アクセス**します。

    -   **クライアント名**ボックスに、入力、**クライアント ID**先ほどコピーしました。

          ![api のクライアント アクセスを管理](./media/google12-2.png "google12 2")

    -   **1 つまたは複数の API のスコープ**ボックスに、次の必要なスコープの一覧を入力 (テキストをコピーし、ボックスに貼り付けます)。

        `https://www.googleapis.com/auth/admin.reports.audit.readonly,https://www.googleapis.com/auth/admin.reports.usage.readonly,https://www.googleapis.com/auth/drive,https://www.googleapis.com/auth/drive.appdata,https://www.googleapis.com/auth/drive.apps.readonly,https://www.googleapis.com/auth/drive.file,https://www.googleapis.com/auth/drive.metadata.readonly,https://www.googleapis.com/auth/drive.readonly,https://www.googleapis.com/auth/drive.scripts,https://www.googleapis.com/auth/admin.directory.user.readonly,https://www.googleapis.com/auth/admin.directory.user.security,https://www.googleapis.com/auth/admin.directory.user.alias,https://www.googleapis.com/auth/admin.directory.orgunit,https://www.googleapis.com/auth/admin.directory.notifications,https://www.googleapis.com/auth/admin.directory.group.member,https://www.googleapis.com/auth/admin.directory.group,https://www.googleapis.com/auth/admin.directory.device.mobile.action,https://www.googleapis.com/auth/admin.directory.device.mobile,https://www.googleapis.com/auth/admin.directory.user`

    -    クリックして**承認**します。

17. タイトルバーで Google Cloud Platform の横にある 3 本の水平線をクリックして Google のメニューを開きます。 **[Google Cloud Platform]** をクリックし、左側のメニューの **[APIs and services**]/(API とサービス/) タブをクリックします。  

18. 開いているダッシュボードで、下にスクロールして有効になっている API の一覧を表示し、 **[Google ドライブ API]** をクリックします。
       ![Google ドライブを選択](./media/google14.png "google14")  

19. **[Drive UI 統合]** /(Drive UI 統合/) タブをクリックし、次の情報を入力します。

    - **[Application Name]\(アプリケーション名\)** :Microsoft Cloud App Security。  
  
    - **[Short Description]\(簡単な説明\)、[Long Description]\(詳しい説明\)** (省略可能):Microsoft Cloud App Security を使用すると、クラウド アプリケーションの状況を把握できるようになり、クラウド アプリケーションの使用を制御、調査、および管理できるほか、企業データを保護したり、クラウド アプリケーション上での疑わしいアクティビティを検出したりするのに役立ちます。  
  
    - Google から、少なくとも 1 つのアプリケーション アイコンをアップロードするように要求されます。 [https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826) に移動して、Cloud App Security のアイコンが含まれる zip ファイルをダウンロードします。 次に、 **[Application icon]\(アプリケーション アイコン\)** で 128x128 のイメージの横にある **[Select]\(選択\)** をクリックし、ポップアップ画面にドラッグします。 32x32 のイメージの横にある **[Select]\(選択\)** をクリックして、ポップアップ画面にドラッグします。  
  
    - 下にスクロールして **[Drive Integration]** /(ドライブ統合/)セクションを表示し、 **[Open URL]** /(URL を開く/) に次の URL を入力します。  
  
       https://portal.cloudappsecurity.com/#/services/11770?tab=files  
    
      ![Google ドライブの編集](./media/google15.png "google15")  

20. **[変更を保存]** をクリックします。

21. **[Enabled APIs]** /(有効にされた API/) の一覧に戻ります。 **[G Suite Marketplace SDK]** をクリックします。 
      
22. **[構成]** タブを選択します。 
  
    -   上部に表示される**プロジェクト番号 (アプリ ID)** を、後で使用できるようにコピーしておきます。  
  
    -   **[アプリケーション名]** で、「**Microsoft Cloud App Security**」と入力します。
  
         **[アプリケーションの説明]** に、「Microsoft Cloud App Security を使用すると、クラウド アプリケーションの状況が把握できるようになり、クラウド アプリケーションの使用を制御、調査、および管理できるほか、企業データを保護したり、クラウド アプリケーション上での疑わしいアクティビティを検出したりするのに役立ちます」と入力します。 
    - **[新しい項目]** ウィンドウの **[完了]** をクリックします。      
     
       ![google の新しい項目](./media/google-new-item.png "google の新しい項目")  

    -   **[Enable individual install (個々のインストールを有効にする)]** チェック ボックスをオフにします。  
  
    -   **[アプリケーション アイコン]** で、4 つの必須イメージを設定します。  
  
         イメージは [https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826) にあります。  
  
    -   次に **[Support URLs (サポートの URL)]** を入力します:  
  
        -   **サービス利用規約 URL**: https://go.microsoft.com/fwlink/?LinkID=733268  
  
        -   **プライバシー ポリシー URL**: https://go.microsoft.com/fwlink/?LinkId=512132  
  
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

    -   **[Visibility]\(可視性\)** で **[My domain]\(独自ドメイン\)** (パブリックではありません) を選択します。 
    -   **[変更を保存]** をクリックします。  
        ![google の可視性](./media/google-visibility.png "google の可視性")  
23. [admin.google.com](https://admin.google.com/) にアクセスし、 **[セキュリティ]** を選択します。
   
      ![Google セキュリティ](./media/googlesec.png "Google セキュリティ")  
 
24. **[API リファレンス]** を選択します。  
       ![Google API 有効化](./media/googleapi.png "google api")  
      
25. **[Enable API Access (API アクセスの有効化)]** を選択してから **[変更を保存]** をクリックします。  
  
    ![Google API 参照](./media/googleapiref.png "google8")  

  
## <a name="configure-cloud-app-security"></a>Cloud App Security の設定  
  
1.  Cloud App Security ポータルで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。  
  
2.  **[接続アプリ]** ページで、プラス記号をクリックし、 **[G Suite]** を選択します。  
       
  
3.  ポップアップで、次の情報を入力します。  
  
     ![Cloud App Security での G Suite 構成](./media/gsuite-config-cas.png "Cloud App Security での G Suite 構成")  
  
    1.  手順 13 でコピーした**サービス アカウント ID**。  
  
    2.  **プロジェクト番号 (アプリ ID)** 22 の手順でコピーします。  
  
    3.  手順 12 で保存した**証明書** P12 をアップロードします。 保存しておいたパスワードがここで必要になります。  
  
    4.  G Suite 管理者の**管理者アカウントの電子メール**を 1 つ入力します。  
  
    5.  G Suite Business または Enterprise のアカウントがある場合、このチェック ボックスをオンにします。 Cloud App Security で使用できる G Suite Business または Enterprise の機能の詳細については、[アプリの表示、保護、ガバナンスの操作をすぐに実行できるようにする](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)方法に関するページをご覧ください。  
  
    6.  **[設定の保存]** をクリックします。  
  
    7.  **[リンクに移動]** をクリックし、G Suite に接続します。 これにより G Suite が開き、Cloud App Security へのアクセス承認を求められます。  
         
    8.  **[今すぐテスト]** をクリックし、正常に接続されたことを確認します。  
  
         テストには数分かかる場合があります。  
  
         接続成功の通知を受信したら、 **[完了]** をクリックして [G Suite] ページを閉じます。  
  
  
G Suite を接続すると、接続までの 60 日間のイベントを受け取ります。
  
G Suite を接続すると、Cloud App Security がフル スキャンを実行します。 所有するファイルとユーザーの数に応じて、フル スキャンの実行に時間がかかる場合があります。 ほぼリアルタイムのスキャンを有効にするために、アクティビティが検出されたファイルはスキャン キューの先頭に移動されます。 たとえば、編集、更新、または共有されたファイルはすぐにスキャンされます。 これは、本質的に変更されていないファイルには適用されません。 たとえば、表示、プレビュー、印刷、またはエクスポートされたファイルは、定期スキャンのときにスキャンされます。
  
  
## <a name="next-steps"></a>次の手順 
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
  
