---
title: "Cloud App Security ポータルへの管理アクセス権を管理する | Microsoft Docs"
description: "ここでは、管理者用の Cloud App Security ポータルへのアクセス権を設定する手順について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/7/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b718edad-350c-4d90-b045-92529d701dc5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ce7a3bb3951e16efeaeafa3e2fc463a3ac5d9dbc
ms.sourcegitcommit: 945cb3c047ae1bfc05be20cc7798c43005b27c9b
ms.translationtype: HT
ms.contentlocale: ja-JP
---
## <a name="managing-admin-access"></a>管理アクセス許可の管理

Cloud App Security は、次の管理者ロールをサポートしています。

- 全体管理者: 全体管理者は**フル アクセス**権を持っています。フル アクセス権を持つ管理者は、Cloud App Security で管理者の追加、ポリシーと設定の追加、ログのアップロード、ガバナンス アクションを実行するフル アクセス許可を持っています。
- セキュリティ管理者: セキュリティ管理者は**フル アクセス**権を持っています。フル アクセス権を持つ管理者は、Cloud App Security で管理者の追加、ポリシーと設定の追加、ログのアップロード、ガバナンス アクションを実行するフル アクセス許可を持っています。
- セキュリティ閲覧者: セキュリティ閲覧者は読み取り専用アクセス許可を持ち、アラートを管理できます。 セキュリティ閲覧者は、以下の機能を実行できません。
      - ポリシーを作成する、または既存のポリシーを編集および変更する 
      - ガバナンス アクションを実行する 
      - 探索ログをアップロードする
      - サードパーティ アプリの禁止または承認
      - IP アドレス範囲設定ページへのアクセスと表示
      - すべての設定ページへのアクセスと表示 
      - 探索設定へのアクセスと表示 
      - アプリ コネクタ ページへのアクセスと表示
      - ガバナンス ログへのアクセスと表示 
      - [スナップショット レポートの管理] ページへのアクセスと表示 

Azure Active Directory または Office 365 でこれらのロールを持つ管理者は、Cloud App Security でも同じロールを持ちます。 管理者ロールの詳細については、「[Azure Active Directory での管理者ロールの割り当て](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-assign-admin-roles)」を参照してください。

Cloud App Security に管理者を追加するには:

1. 設定の歯車アイコン ![設定アイコン](./media/settings-icon.png "設定アイコン")をクリックし、**[管理者アクセス権を管理します]** をクリックします。 

2. Cloud App Security へのアクセス権を付与する管理者を追加します。
  
      
3. 次に、ドロップダウンをクリックして、管理者に付与するアクセス権の種類 (**[フル アクセス]** または **[セキュリティ閲覧者]**) を設定します。

     >[!NOTE]
      >**セキュリティ閲覧者**が制限されているページにアクセスしたり、制限されている操作を実行しようとしたりすると、そのページへのアクセスまたは操作の実行のアクセス許可がないというエラーが表示されます。

4. [ **閉じる**] をクリックします。  

   >[!NOTE]
    >適切なロール (グローバル、セキュリティ、コンプライアンス管理者) を持つ非招待ユーザーは、他のユーザーを Cloud App Security に招待できます。
  
 ![管理者アクセスの管理](./media/manage-admin-access.png "管理者アクセスの管理")  

**管理者のアクセス許可を上書きするには:**

Azure Active Directory または Office 365 の管理者のアクセス許可を上書きするには、手動で Cloud App Security にユーザーを追加し、ユーザーにロールを割り当てます。
たとえば、Azure Active Directory でセキュリティ閲覧者である佐藤さんに、Cloud App Security ではフル アクセス権を付与するには、手動で佐藤さんを Cloud App Security に追加し、フル アクセスを割り当てて元のロールを上書きして、Cloud App Security で目的のアクセス許可を持たせることができます。 


##  <a name="Adminsettings"></a> 管理設定のカスタマイズ  
Cloud App Security の管理者としての設定をセットアップする場合、ポータルのメニュー バーでユーザー名をクリックしてから [**ユーザー設定**] を選択し、次の項目を設定します。  
  
1.  [**アカウント設定**] をクリックします。 ここでは、ユーザー自身がポータルの表示に使用する言語をカスタマイズできます。 ポータルの表示に既定の言語を使用するか、または自分用に別の言語を使用するかを設定できます。  
  
     ![カスタム ユーザー設定](./media/custom-user-settings.png "カスタム ユーザー設定")  
  
2.  [**通知**] をクリックすると、システムから送信される電子メールやテキスト通知の受信設定を変更できます。  電子メールで受信するアラートや違反の重要度を設定できます。重要度はポリシーごとに設定できるため、違反がトリガーされると、この設定と違反が発生したポリシーで設定されている重要度に基づいて電子メール通知が送信されます。 電子メールは、Cloud App Security へのログインに使用される管理者のユーザー アカウントに関連付けられているエイリアスに送信されます。 電話番号を入力してアラートや通知が送信された場合に Cloud App Security からテキスト メッセージを受信できるようにし、テキスト メッセージで通知を受信する重要度レベルを設定します。  
  
   > [!NOTE] 
   > テキスト メッセージで送信されるアラートの最大数は、1 つの電話番号につき 1 日あたり 10 件です。 日は UTC タイム ゾーンに従って計算されることに注意してください。 
  
  ![通知設定](./media/notification-settings.png "通知設定")  
  
3. 完了したら [**保存**] をクリックします。  


## <a name="region-and-language-settings"></a>地域と言語の設定  
  
1. ポータルで使用する既定の**言語**を設定します。 特定の管理者の言語を変更するには、[**ユーザー設定**] > [**アカウント設定**] の順に移動します。  
  
   ![タイム ゾーンの言語](./media/timezone-language.png "タイム ゾーンの言語")  
  
2. [**マスター タイム ゾーン**] を設定します。 Cloud App Security は継続的にデータの分析および集計を行います。 既定では、Cloud App Security ポータルのタイム ゾーンは UTC に設定されています。 システム内の Cloud App Security がインシデントの日付を正確に記録するためには、マスター タイム ゾーンを設定することが重要です。 たとえば、アクティビティ グラフでは、データは日付に基づいて整理されます。この日付は、システムのタイム ゾーンに従います。既定のタイム ゾーンを変更しないと、データは UTC タイム ゾーンの 24 時間ごとの日付に従って整理され、実際のデータと何時間もずれる可能性があります。  
  
     ![マスター タイム ゾーン](./media/master-time-zone.png "マスター タイム ゾーン")  
  
## <a name="back-up-portal-settings"></a>ポータル設定のバックアップ

ポータル設定は、この画面からいつでもバックアップできます。 [ポータル設定をエクスポート] をクリックすると、ポリシー規則やユーザー グループ、IP アドレス範囲などのポータル設定がすべて記述された json ファイルが作成されます。  
  
![バックアップ コンソール](./media/backup-console.png "バックアップ コンソール")  
  
##  <a name="mailsettings"></a> エクスペリエンスの個人設定  
メニュー バーで設定アイコン ![設定アイコン](./media/settings-icon.png "設定アイコン") をクリックして [**メールの設定**] を選択し、Cloud App Security から管理者に送信されるアラート要求の電子メール通知、および関与している支社についてエンド ユーザーに送信される通知のパラメーターを設定できます。  
  
![[メールの設定] メニュー](./media/mail-setting-menu.png "[メールの設定] メニュー")  
  
次を構成します。  
  
1.  **From email address (電子メール アドレスから)**: 通知の送信に使用する電子メール アカウント。  
  
     **From display name (表示名から)**: 電子メール メッセージの [**From**] フィールドに表示する名前。  
  
     **返信用メール アドレス**: メッセージの返信に使用される電子メール アカウント。  
  
     ![[メールの設定] の構成](./media/mail-settings-config.png "[メールの設定] の構成")  
  
2.  HTML ファイルを使用すると、システムから送信される電子メール メッセージのカスタマイズやデザインを行えます。 テンプレートに使用される HTML ファイルには次の項目が含まれます。  
  
    -   すべてのテンプレートの CSS は、テンプレート内でインラインである必要があります。  
  
    -   テンプレートには編集不可能なプレースホルダーが 3 つ含まれます。  
  
         %%logo%% - [全般設定] ページでアップロードされた企業のロゴの URL。  
  
         %%title%% - ポリシーにより設定された電子メールのタイトルのプレースホルダー。  
  
         %%content%% - ポリシーにより設定されたエンド ユーザー向けコンテンツのプレースホルダー。  
  
     電子メール テンプレートのサンプルを次に示します。 
```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
  <html>  
       <head>  
            <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>  
            <meta name="viewport" content="width=device-width, initial-scale=1.0"/>  
          </head>  
          <body class="end-user">  
          <table border="0" cellpadding="20%" cellspacing="0" width="100%" id="background-table">  
            <tr>  
              <td align="center">  
                <!--[if (gte mso 9)|(IE)]>  
                <table width="600" align="center" cellpadding="0" cellspacing="0" border="0">  
                  <tr>  
                    <td>  
                <![endif]-->  
                <table bgcolor="#ffffff" align="center" border="0" cellpadding="0" cellspacing="0" style="padding-bottom: 40px;" id="container-table">  
                  <tr>  
                    <td align="right" id="header-table-cell">  
                      <img src="%%logo%%" alt="Microsoft Cloud App Security" id="org-logo" />  
                    </td>  
                  </tr>  
                  <tr>  
                    <td style="padding-top: 58px;" align="center" valign="top">  
                      <table width="100%" cellpadding="12">  
                        <tr>  
                          <td align="center" class="round-title">  
                            %%title%%  
                          </td>  
                        </tr>  
                      </table>  
                    </td>  
                  </tr>  
                  <tr>  
                    <td style="padding: 0 40px 79px 40px;" class="content-table-cell" align="left" valign="top">  
                        %%content%%  
                    </td>  
                  </tr>  
                  <tr>  
                    <td class="last-row"></td>  
                  </tr>  
                </table>  
                <!--[if (gte mso 9)|(IE)]>  
                </td>  
                </tr>  
                </table>  
                  <![endif]-->  
              </td>  
              </tr>  
          </table>  
            </body>  
          </html>  
    ```

  
3.  Click **Upload a template...** and select the file you created.  
  
     Then, click **Send a test email** to send yourself a test email to see an example of the template you created.  
     The email will be sent to the account you used to log into the portal. In the test email you will be able to see the metadata fields, the template, the email subject, the title in the email body and the content.  
  
## Single sign-on  
Cloud App Security is coupled with Azure Active Directory for authentication, provisioning, and licensing related activities. For information on how to manage single sign-on, see [Azure Active Directory federation compatibility list: third-party identity providers that can be used to implement single sign-on](https://msdn.microsoft.com/library/azure/jj679342.aspx).  


> [!NOTE] 
> If you use ExpressRoute, Cloud App Security is deployed in Azure and fully integrated with [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). All interactions with the Cloud App Security apps and traffic sent to Cloud App Security, including upload of discovery logs, is routed via ExpressRoute **public peering** for improved latency, performance and security. There are no configuration steps required from the customer side.  
    For more information about  Public Peering, see [ExpressRoute circuits and routing domains](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).  
    
## See Also  
[Set up Cloud Discovery](set-up-cloud-discovery.md)   
[For technical support, please visit the Cloud App Security assisted support page.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier customers can also choose Cloud App Security directly from the Premier Portal.](https://premier.microsoft.com/)  
  
  