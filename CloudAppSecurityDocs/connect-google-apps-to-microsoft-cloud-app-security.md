---
title: G Suite を Cloud App Security に接続する
description: この記事では、使用状況を視覚化して制御できるように、API コネクタを使用して Cloud App Security に G Suite を接続する方法に関する情報を提供します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/27/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 06c6a2db19332bb49e86220464a7eff459657b4b
ms.sourcegitcommit: 00599ac6c64a4c62ed9ebdda3edb58f90f92c24d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912281"
---
# <a name="connect-g-suite-to-microsoft-cloud-app-security"></a>G Suite を Microsoft Cloud App Security に接続する

*適用対象: Microsoft Cloud App Security*

この記事では、コネクタ API を使用して Microsoft Cloud App Security を既存の G Suite アカウントに接続する方法を説明します。 この接続により、G Suite の使用状況を視覚化して制御できるようになります。 Cloud App Security が G Suite を保護する方法の詳細については、「 [Protect g suite](protect-gsuite.md)」を参照してください。

## <a name="configure-g-suite"></a>G Suite を構成する

1. G Suite のスーパー管理者として、<a href="https://cloud.google.com/console/project" target="_blank">https://cloud.google.com/console/project</a> にサインインします。

1. **[プロジェクトの作成]** をクリックして新しいプロジェクトを開始します。

    ![google1](media/google1.png)

1. **[新しいプロジェクト]** 画面で、プロジェクトに次の名前を付けます。 **Cloud App Security** 、 **[作成]** をクリックします。

    ![google2](media/google2.png)

1. プロジェクトが作成されたら、ツール バーの **[Google Cloud Platform]** をクリックします。 上部にあるドロップダウン リストで適切なプロジェクトが選択されていることを確認します。

    ![google プロジェクト](media/googleverify-project.png)

1. メニューを選択し、[ **api & Services** > **ライブラリ**] にアクセスして、次の api を有効にします (api が一覧に表示されていない場合は、検索行を使用します)。

    * 管理 SDK

    * 監査 API

    * Google ドライブ API

    * G Suite Marketplace SDK  
![google api](media/google4.png)

    > [!NOTE]
    > API ごとに、 **[有効]** をクリックしてアクティブにします。
    >
    > ![Google APPI を有効にする](media/google-api.png)
    >
    > ここでは **[資格情報]** の警告は無視します。

1. [メニュー] を選択し、[ **api & Services** > **ダッシュボード**] にアクセスして、次の api が有効になっていることを確認します。

    ![google が有効になっている api](media/google5.png)

1. **[OAuth 同意画面]** タブにアクセスします。

    * **[アプリケーション名]** に「 **Microsoft Cloud App Security**」と入力します。

    * その他のすべてのフィールドは省略できます。

    * **[Save]** (保存) をクリックします。

    ![Google oauth の同意](media/google-oauth-consent.png)

1. **[資格情報]** 画面で、 **[資格情報の作成]** の横にある矢印をクリックし、 **[サービスアカウントキー]** を選択します。

    ![Google の資格情報](media/google7.png)

1. **[サービスアカウント]** で、 **[新しいサービスアカウント]** を選択し、アカウントの名前を指定します。たとえば、「 **service account 1**」と入力します。 **[ロール]** で、 **[プロジェクト]** 、 **[エディター]** と選択します。 **[キーの種類]** で **[P12]** を選択してから **[作成]** をクリックします。 P12 証明書ファイルがコンピューターに保存されます。

    ![Google でのサービスアカウントキーの作成](media/google9.png)

1. **[資格情報]** 画面で、一番右にある **[Manage service accounts (サービス アカウントの管理)]** をクリックします。 サービスアカウントに割り当てられている**電子メール**をコピーします。後で必要になります。

    ![G Suite の資格情報サービスアカウント](media/google10.png)

1. 作成したサービス アカウントの右側にある 3 つの点をクリックし、 **[編集]** を選択します。

    ![google edit](media/google11.png "google edit")

1. **[ドメイン全体の委任を表示]** をクリックし、 **[G Suite ドメイン全体の委任を有効にする]** を選択します。

    ![google クライアント ID](media/google12.png "google12")

    1. **クライアント ID**をコピーします。後で必要になります。
    ![api クライアントアクセスの管理](media/google12-2.png "google12-2")

    1. **[保存]** をクリックします。

    1. [admin.google.com](https://admin.google.com/) にアクセスし、 **[セキュリティ]** を選択します。

    1. **[詳細設定]** を展開し、 **[認証]** で **[API クライアントアクセスの管理]** を選択します。

    1. **[クライアント名]** ボックスに、前の手順でコピーした**クライアント ID**を入力します。  

    1. **[1 つまたは複数の API スコープ]** ボックスに、次の必要なスコープの一覧を入力します (テキストをコピーし、ボックスに貼り付けます)。  
`https://www.googleapis.com/auth/admin.reports.audit.readonly,https://www.googleapis.com/auth/admin.reports.usage.readonly,https://www.googleapis.com/auth/drive,https://www.googleapis.com/auth/drive.appdata,https://www.googleapis.com/auth/drive.apps.readonly,https://www.googleapis.com/auth/drive.file,https://www.googleapis.com/auth/drive.metadata.readonly,https://www.googleapis.com/auth/drive.readonly,https://www.googleapis.com/auth/drive.scripts,https://www.googleapis.com/auth/admin.directory.user.readonly,https://www.googleapis.com/auth/admin.directory.user.security,https://www.googleapis.com/auth/admin.directory.user.alias,https://www.googleapis.com/auth/admin.directory.orgunit,https://www.googleapis.com/auth/admin.directory.notifications,https://www.googleapis.com/auth/admin.directory.group.member,https://www.googleapis.com/auth/admin.directory.group,https://www.googleapis.com/auth/admin.directory.device.mobile.action,https://www.googleapis.com/auth/admin.directory.device.mobile,https://www.googleapis.com/auth/admin.directory.user`

    1. **[承認]** をクリックします。

1. [Google Cloud Platform](https://console.cloud.google.com/)で、[メニュー] を選択し、[ **api とサービス** > **ダッシュボード**] にアクセスします。

1. ダッシュボードで、有効になっている Api の一覧まで下にスクロールし、 **[Google DRIVE API]** をクリックします。
    Google Drive](media/google14.png) を選択 ![

1. **[Drive UI 統合]** /(Drive UI 統合/) タブをクリックし、次の情報を入力します。

    * **アプリケーション名**: Microsoft Cloud App Security。

    * **簡単な説明と詳しい説明** (省略可能): Microsoft Cloud App Security を使用すると、クラウド アプリケーションの状況を把握できるようになり、クラウド アプリケーションの使用を制御、調査、および管理できるほか、企業データを保護したり、クラウド アプリケーション上での疑わしいアクティビティを検出したりするのに役立ちます。

    * Google から、少なくとも 1 つのアプリケーション アイコンをアップロードするように要求されます。 [https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826) に移動して、Cloud App Security のアイコンが含まれる zip ファイルをダウンロードします。 次に、 **[Application icon]\(アプリケーション アイコン\)** で 128x128 のイメージの横にある **[Select]\(選択\)** をクリックし、ポップアップ画面にドラッグします。 32x32 のイメージの横にある **[Select]\(選択\)** をクリックして、ポップアップ画面にドラッグします。

    * 下にスクロールし、**ドライブの統合** セクションで、 **url を開く:** 
    `https://portal.cloudappsecurity.com/#/services/11770?tab=files` に次の url を入力します。

    ![Google Drive の編集](media/google15.png)

1. **[送信]** をクリックします。

1. **[Enabled APIs]** /(有効にされた API/) の一覧に戻ります。 **[G Suite Marketplace SDK]** をクリックします。

1. **[構成]** タブを選択します。

    1. 上部に表示される**プロジェクト番号 (アプリ ID)** を、後で使用できるようにコピーしておきます。

    1. **[アプリケーション名]** で、「**Microsoft Cloud App Security**」と入力します。  
**[アプリケーションの説明]** に、「Microsoft Cloud App Security を使用すると、クラウド アプリケーションの状況が把握できるようになり、クラウド アプリケーションの使用を制御、調査、および管理できるほか、企業データを保護したり、クラウド アプリケーション上での疑わしいアクティビティを検出したりするのに役立ちます」と入力します。

    1. **[新しい項目]** ウィンドウの **[完了]** をクリックします。

    ![google の新しい項目](media/google-new-item.png)

    * **[個々のインストールを有効にする]** チェックボックスをオフにします。

    * **[アプリケーション アイコン]** で、4 つの必須イメージを設定します。

    イメージは [https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826) にあります。

    * 次に **[Support URLs (サポートの URL)]** を入力します:

    * **サービス利用規約 URL**: https://go.microsoft.com/fwlink/?LinkID=733268

    * **プライバシー ポリシー URL**: https://go.microsoft.com/fwlink/?LinkId=512132

    * **[OAuth 2.0 scopes]\(OAuth 2.0 スコープ\)** で、以下の URL をコピーして貼り付けます (1 つコピーするたびに Enter キーを押します)。  
`https://www.googleapis.com/auth/admin.reports.audit.readonly`  
`https://www.googleapis.com/auth/admin.reports.usage.readonly`  
`https://www.googleapis.com/auth/drive`  
`https://www.googleapis.com/auth/drive.appdata`  
`https://www.googleapis.com/auth/drive.apps.readonly`  
`https://www.googleapis.com/auth/drive.file`  
`https://www.googleapis.com/auth/drive.metadata.readonly`  
`https://www.googleapis.com/auth/drive.readonly`  
`https://www.googleapis.com/auth/drive.scripts`  
`https://www.googleapis.com/auth/admin.directory.user.readonly`  
`https://www.googleapis.com/auth/admin.directory.user.security`  
`https://www.googleapis.com/auth/admin.directory.user.alias`  
`https://www.googleapis.com/auth/admin.directory.orgunit`  
`https://www.googleapis.com/auth/admin.directory.notifications`  
`https://www.googleapis.com/auth/admin.directory.group.member`  
`https://www.googleapis.com/auth/admin.directory.group`  
`https://www.googleapis.com/auth/admin.directory.device.mobile.action`  
`https://www.googleapis.com/auth/admin.directory.device.mobile`  
`https://www.googleapis.com/auth/admin.directory.user`

    * **[Visibility]\(可視性\)** で **[My domain]\(独自ドメイン\)** (パブリックではありません) を選択します。
    * **[変更を保存]** をクリックします。
        ![google visibility](media/google-visibility.png)
1. Google 管理コンソールで、[ [Manage App Access Control](https://admin.google.com/)] にアクセスします。 **G Suite 管理者**の行を探し、**無制限**のアクセス権があることを確認します。

    ![google のセキュリティ](media/googlesec.png)

## <a name="configure-cloud-app-security"></a>Cloud App Security の設定

1. Cloud App Security ポータルで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。

1. G Suite 接続の詳細を指定するには、 **[アプリコネクタ]** の下で、次のいずれかの操作を行います。

    **既に接続されている GCP インスタンスがある G Suite 組織の場合**

    * コネクタの一覧で、GCP インスタンスが表示されている行の末尾にある3つの点をクリックし、 **[G Suite の追加]** をクリックします。

    **接続された GCP インスタンスをまだ持っていない G Suite 組織の場合**

    * **[接続アプリ]** ページで、プラス記号をクリックし、 **[G Suite]** を選択します。

1. ポップアップで、次の情報を入力します。

    ![Cloud App Security での G Suite 構成](media/gsuite-config-cas.png "Cloud App Security での G Suite 構成")

    1. 前の手順でコピー**した** **サービスアカウント ID**を入力します。

    1. 前の手順でコピーした**プロジェクト番号 (アプリ ID)** を入力します。

    1. 先ほど保存した P12**証明書**ファイルをアップロードします。

    1. G Suite 管理者の**管理者アカウントの電子メール**を 1 つ入力します。

    1. G Suite Business または Enterprise のアカウントがある場合、このチェック ボックスをオンにします。 Cloud App Security で使用できる G Suite Business または Enterprise の機能の詳細については、[アプリの表示、保護、ガバナンスの操作をすぐに実行できるようにする](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)方法に関するページをご覧ください。

    1. **[設定の保存]** をクリックします。

    1. **[リンクに移動]** をクリックし、G Suite に接続します。 これにより G Suite が開き、Cloud App Security へのアクセス承認を求められます。

    1. **[今すぐテスト]** をクリックし、正常に接続されたことを確認します。  
    テストには数分かかる場合があります。  
    接続成功の通知を受信したら、 **[完了]** をクリックして [G Suite] ページを閉じます。

G Suite を接続すると、接続までの 60 日間のイベントを受け取ります。

G Suite を接続すると、Cloud App Security がフル スキャンを実行します。 所有するファイルとユーザーの数に応じて、フル スキャンの実行に時間がかかる場合があります。 ほぼリアルタイムのスキャンを有効にするために、アクティビティが検出されたファイルはスキャン キューの先頭に移動されます。 たとえば、編集、更新、または共有されたファイルはすぐにスキャンされます。 これは、本質的に変更されていないファイルには適用されません。 たとえば、表示、プレビュー、印刷、またはエクスポートされたファイルは、定期スキャンのときにスキャンされます。

アプリの接続で問題が発生した場合は、「[アプリコネクタのトラブルシューティング](troubleshooting-api-connectors-using-error-messages.md)」を参照してください。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
