---
title: ServiceNow を Cloud App Security に接続する
description: この記事では、API コネクタを使用して Cloud App Security に ServiceNow アプリを接続し、使用状況を表示および制御する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 6/24/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a1214e0067d5c83ff001ff6c0e8a27fb227bc7e9
ms.sourcegitcommit: 9fe879ce7f07933866191724de5f108f43e3f923
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/24/2020
ms.locfileid: "77566835"
---
# <a name="connect-servicenow-to-microsoft-cloud-app-security"></a>ServiceNow を Microsoft Cloud App Security に接続する

*適用対象: Microsoft Cloud App Security*

この記事では、App connector API を使用して Microsoft Cloud App Security を既存の ServiceNow アカウントに接続する手順について説明します。 この接続により、ServiceNow の使用を可視化し、制御することができます。 ServiceNow の保護 Cloud App Security 方法の詳細については、「 [servicenow の保護](protect-servicenow.md)」を参照してください。

> [!NOTE]
> Fuji 以降のリリースで使用できる OAuth アプリトークンを使用して ServiceNow をデプロイすることをお勧めします (関連する[servicenow のドキュメント](https://wiki.servicenow.com/index.php?title=OAuth_Applications#gsc.tab=0)を参照してください)。
> 以前のリリースでは、ユーザーとパスワードに基づいて[レガシ接続モード](#legacy-servicenow-connection)を使用できます。 指定されたユーザー名/パスワードは API トークンの生成にのみ使用され、最初の接続プロセスの後には保存されません。

> [!NOTE]
> Cloud App Security は、ジャカルタ、キングストン、Eureka、フィジー、ジュネーブ、ヘルシンキ、イスタンブール、ロンドン、レアルマドリードの ServiceNow バージョンをサポートしています。 ServiceNow を Cloud App Security に接続するには、ロール**管理者**であり、servicenow インスタンスが API アクセスをサポートしていることを確認する必要があります。  詳細については、 [ServiceNow の製品ドキュメント](https://wiki.servicenow.com/index.php?title=Base_System_Roles#gsc.tab=0)を参照してください。

## <a name="how-to-connect-servicenow-to-cloud-app-security-using-oauth"></a>OAuth を使用して ServiceNow を Cloud App Security に接続する方法

1. ServiceNow アカウントに管理者アカウントでサインインします。

    > [!NOTE]
    > 指定されたユーザー名/パスワードは API トークンの生成にのみ使用され、最初の接続プロセスの後には保存されません。

2. **フィルターナビゲーター**の検索バーに「 **OAuth** 」と入力し、[**アプリケーションレジストリ**] を選択します。

3. **アプリケーションレジストリ**のメニューバーで、[**新規**] をクリックして新しい OAuth プロファイルを作成します。

    ![ServiceNow の新しい OAuth プロファイル](media/servicenow-app-registry.png)

4. [ **Oauth アプリケーションの種類**] で、[**外部クライアントの oauth API エンドポイントを作成**する] をクリックします。

    ![ServiceNow OAuth の種類](media/servicenow-oauth-app-type.png)

5. [**アプリケーションレジストリ] [新しいレコード**] で、次のフィールドを入力します。

    - [**名前**] フィールドに新しい OAuth プロファイルの名前を指定します。たとえば、「CloudAppSecurity」と指定します。

    - **クライアント ID**は自動的に生成されます。 この ID をコピーして、接続を完了するために Cloud App Security に貼り付ける必要があります。

    - [**クライアントシークレット**] フィールドに、文字列を入力します。 空のままにすると、ランダムなシークレットが自動的に生成されます。 後で使用するためにコピーして保存します。

    - **アクセストークン**の有効期間を少なくとも3600に増やします。

    - 
          **[送信]** をクリックします。

    ![ServiceNow プロファイル Id](media/servicenow-profile-ids.png)

6. Cloud App Security ポータルで、[**調査**]、[**接続さ**れたアプリ] の順にクリックします。

7. [**アプリコネクタ**] ページで、[+] ボタン、[ **ServiceNow**] の順にクリックします。

    ![ServiceNow の接続](media/connect-servicenow.png "ServiceNow の接続")

8. ポップアップで、該当するボックスに ServiceNow ユーザー ID、パスワード、インスタンス URL、クライアント ID、およびクライアントシークレットを追加します。 ServiceNow のユーザー ID を検索するには、ServiceNow ポータルで、[**ユーザー** ] に移動し、テーブルで自分の名前を見つけます。

    ![ServiceNow ユーザー ID](media/servicenow-userid.png)

9. **[接続]** をクリックします。

    ![ServiceNow を CAS に接続する](media/servicenow-portal-connect.png "ポータルでの ServiceNow 接続")

10. [**今すぐテスト**] をクリックして、接続に成功したことを確認します。

    テストには数分かかる場合があります。 成功通知を受信したら、[**閉じる**] をクリックします。

ServiceNow に接続すると、接続する7日間のイベントが表示されます。

## <a name="legacy-servicenow-connection"></a>従来の ServiceNow 接続

ServiceNow を Cloud App Security に接続するには、管理者レベルのアクセス許可が必要です。また、ServiceNow インスタンスが API アクセスをサポートしていることを確認してください。

1. ServiceNow アカウントに管理者アカウントでサインインします。

2. Cloud App Security 用の新しいサービスアカウントを作成し、新しく作成したアカウントに管理者ロールをアタッチします。

3. REST API プラグインが有効になっていることを確認します。

    ![ServiceNow アカウント](media/servicenow-account.png "ServiceNow アカウント")

4. Cloud App Security ポータルで、[**調査**]、[承認された**アプリ**] の順にクリックします。

5. [ServiceNow] 行の [**アプリコネクタの状態**] 列で [**接続**] をクリックするか、[**アプリを接続**] ボタン、[ **servicenow**] の順にクリックします。

   ![ServiceNow の接続](media/connect-servicenow.png "ServiceNow の接続")

6. [ServiceNow 設定] ページの [API] タブで、該当するボックスに ServiceNow ユーザー ID、パスワード、およびインスタンス URL を追加します。

7. **[接続]** をクリックします。

    ![ServiceNow のパスワードの更新](media/servicenow-update-password.png "ServiceNow のパスワードの更新")

8. [**API のテスト**] をクリックして、正常に接続されたことを確認します。

    テストには数分かかる場合があります。 成功通知を受信したら、[**閉じる**] をクリックします。

ServiceNow に接続すると、接続する7日間のイベントが表示されます。

アプリの接続で問題が発生した場合は、「[アプリコネクタのトラブルシューティング](troubleshooting-api-connectors-using-error-messages.md)」を参照してください。

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
