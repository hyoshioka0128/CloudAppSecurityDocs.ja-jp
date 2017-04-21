---
title: "Cloud App Security ポータルをカスタマイズし、最良の結果を得る | Microsoft Docs"
description: "このトピックでは、ポータルをカスタマイズする最初の手順について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/19/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2e7e57b0-db54-4d75-896c-4700dd9abe48
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b55da41080d70a41382a94b9ff527d50046c61b2
ms.sourcegitcommit: 661f4ce41262e8462c90fd2a4f1232e2154d5113
translationtype: HT
---
# <a name="customize-the-portal"></a>ポータルのカスタマイズ
ここでは、Cloud App Security ポータルをカスタマイズする手順について説明します。
  
## <a name="set-up-the-portal"></a>ポータルのセットアップ  
  
1.  Cloud App Security ポータルのメニュー バーで、設定アイコン ![設定アイコン](./media/settings-icon.png "設定アイコン") をクリックし、**[全般設定]** を選択して、以下の構成を行います。  
  
3.  **組織の詳細**  
  
     自社の**組織の表示名**を指定することは重要です。 これは、システムから送信される電子メールや Web ページに表示されます。  
  
     **環境名** (テナント) を指定します。 これは、複数のテナントを管理する場合に特に重要です。  
  
4. システムから送信される電子メールや Web ページで表示する**ロゴ**を指定することもできます。 ロゴには、150 x 50 ピクセル以下のサイズで背景が透明色の png ファイルを使用する必要があります。  

4.  **管理対象ドメイン** のリストを追加します。 管理対象ドメインは、Cloud App Security が内部ユーザーと外部ユーザー、およびファイルの共有の可否を判別する際に使用されます。 これは、レポートとアラートで使用されます。  
> [!NOTE] 
> - 内部として構成されていないドメインのユーザーは、外部として指定され、アクティビティまたはファイルをスキャンされません。
> - Azure Information Protection の統合により統合を行う場合は、「[Azure Information Protection の統合](azip-integration.md)」で詳細を確認してください。 
  
4.  **アクティビティ ログのメールのプライバシー設定**  
  
     Exchange Online で電子メール メッセージが検出された場合、プライバシーを保護するため、表示方法を設定することができます。 電子メール メッセージの表示方法は、**マスクされた件名**、**完全な件名**、または **ID のみ**のいずれかに設定できます。  
  
     ![全般設定](./media/general-settings.png "全般設定")  
  
5.  **地域と言語の設定**  
  
     ポータルで使用する既定の**言語**を設定します。 特定の管理者の言語を変更するには、[**ユーザー設定**] > [**アカウント設定**] の順に移動します。  
  
     ![タイム ゾーンの言語](./media/timezone-language.png "タイム ゾーンの言語")  
  
     [**マスター タイム ゾーン**] を設定します。 Cloud App Security は継続的にデータの分析および集計を行います。 既定では、Cloud App Security ポータルのタイム ゾーンは UTC に設定されています。 システム内の Cloud App Security がインシデントの日付を正確に記録するためには、マスター タイム ゾーンを設定することが重要です。 たとえば、アクティビティ グラフでは、データは日付に基づいて整理されます。この日付は、システムのタイム ゾーンに従います。既定のタイム ゾーンを変更しないと、データは UTC タイム ゾーンの 24 時間ごとの日付に従って整理され、実際のデータと何時間もずれる可能性があります。  
  
     ![マスター タイム ゾーン](./media/master-time-zone.png "マスター タイム ゾーン")  
  
6.  ポータル設定は、この画面からいつでもバックアップできます。 [ポータル設定をエクスポート] をクリックすると、ポリシー規則やユーザー グループ、IP アドレス範囲などのポータル設定がすべて記述された json ファイルが作成されます。  
  
     ![バックアップ コンソール](./media/backup-console.png "バックアップ コンソール")  
  
7.  Cloud App Security に管理者を追加する場合は、設定の歯車アイコン ![設定アイコン](./media/settings-icon.png "設定アイコン") をクリックしてから **[管理者アクセスの管理]** をクリックします。 Cloud App Security へのアクセス権を付与する管理者を追加し、[**閉じる**] をクリックします。  
>[!NOTE]
>適切なロール (グローバル、セキュリティ、コンプライアンス管理者) を持つ非招待ユーザーは、他のユーザーを Cloud App Security に招待できます。
  
![管理者アクセスの管理](./media/manage-admin-access.png "管理者アクセスの管理")  
  
##  <a name="Adminsettings"></a> 管理設定のカスタマイズ  
Cloud App Security の管理者としての設定をセットアップする場合、ポータルのメニュー バーでユーザー名をクリックしてから [**ユーザー設定**] を選択し、次の項目を設定します。  
  
1.  [**アカウント設定**] をクリックします。 ここでは、ユーザー自身がポータルの表示に使用する言語をカスタマイズできます。 ポータルの表示に既定の言語を使用するか、または自分用に別の言語を使用するかを設定できます。  
  
     ![カスタム ユーザー設定](./media/custom-user-settings.png "カスタム ユーザー設定")  
  
2.  [**通知**] をクリックすると、システムから送信される電子メールやテキスト通知の受信設定を変更できます。  電子メールで受信するアラートや違反の重要度を設定できます。重要度はポリシーごとに設定できるため、違反がトリガーされると、この設定と違反が発生したポリシーで設定されている重要度に基づいて電子メール通知が送信されます。 電子メールは、Cloud App Security へのログインに使用される管理者のユーザー アカウントに関連付けられているエイリアスに送信されます。 電話番号を入力してアラートや通知が送信された場合に Cloud App Security からテキスト メッセージを受信できるようにし、テキスト メッセージで通知を受信する重要度レベルを設定します。  
  
> [!NOTE] 
> テキスト メッセージで送信されるアラートの最大数は、1 つの電話番号につき 1 日あたり 10 件です。 日は UTC タイム ゾーンに従って計算されることに注意してください。 
  
  ![通知設定](./media/notification-settings.png "通知設定")  
  
3. 完了したら [**保存**] をクリックします。  
  
##  <a name="IPtagsandRanges"></a> IP 範囲の設定  
物理的なオフィスの IP アドレスなど、既知の IP アドレスを簡単に識別するには、タグを適切に分類できるように IP アドレスの範囲を設定し、またログやアラートの表示や調査の方法をカスタマイズする必要があります。   
詳細については、「[IP タグ](ip-tags.md)」を参照してください。
  
## <a name="import-user-groups"></a>ユーザー グループのインポート

API コネクタを使用してアプリを接続するとき、Cloud App Security を使用し、たとえば、Office 365 や Azure Active Directory からユーザー グループをインポートできます。

詳細については、「[ユーザー グループ](user-groups.md)」を参照してください。

##  <a name="Adallom_mailsettings"></a> エクスペリエンスの個人設定  
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
  
  