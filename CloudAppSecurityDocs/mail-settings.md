---
title: 電子メールの通知の基本設定 |Microsoft Docs
description: この記事では、Cloud App Security によって送信された電子メール通知を個人用に設定する方法について情報を提供します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/27/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 8402cdc9-4969-4150-b567-ccc9d75e5370
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 6b9ec2fca122bfdfdea4e6ad298a689dd79bcaf6
ms.sourcegitcommit: 0d73d21f961dc883f01a329bcf16dcaf070dca2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/27/2018
ms.locfileid: "34558891"
---
*適用対象: Microsoft Cloud App Security*


##  <a name="mailsettings"></a> 電子メールの通知の基本設定  

Microsoft Cloud App Security から管理者に送信されるアラート要求の電子メール通知、および関与している支社についてエンド ユーザーに送信される通知のパラメーターを設定するには、次の手順に従います。 迷惑メール対策サービスにホワイトリスト登録すべきMicrosoft Cloud App Security 電子メール サーバーの IP アドレスの詳細については、「[ネットワーク要件](network-requirements.md)」をご覧ください。 


1. メニュー バーで設定の歯車アイコン ![設定アイコン](./media/settings-icon.png "設定アイコン")を選択し、**[設定]** を選択して、**[メールの設定]** タブを選択します。  

 ![メールの設定](./media/mail-settings-config.png)

2. **[メール送信者の ID]**: 既定の電子メール設定を使用する予定の場合、このセクションでは何も変更する必要はありません。 電子メールの送信者 ID をカスタマイズする場合は、**[From display name]\(表示名から\)**、**[From email address]\(電子メール アドレスから\)**、**[返信用メール アドレス]** を設定できます。 Microsoft Cloud App Security では、これを実現するために、MailChimp® というサード パーティのメール サービスを自動的に使用します。 これを有効にするためには、MailChimp のサービス利用規約とプライバシーに関する声明を確認して同意する必要があります - それ以外の場合は、Microsoft Cloud App Security は既定の設定を使用して通知を送信します。
   
   > [!NOTE]
   > [rfc822 標準](http://www.rfc-editor.org/rfc/rfc822.txt)に従い、表示名と電子メール アドレスには Unicode 文字のみがサポートされています。

  
3. **[メールのデザイン]** では、HTML ファイルを使用すると、システムから送信される電子メール メッセージのカスタマイズやデザインを行えます。 テンプレートに使用される HTML ファイルには次の項目が含まれます。  
  
   -   すべてのテンプレートの CSS ファイルは、テンプレート内でインラインである必要があります。  
  
   -   テンプレートには編集不可能なプレースホルダーが 3 つ含まれます。  
  
        %%logo%% - [全般設定] ページでアップロードされた企業のロゴの URL。  
  
        %%title%% - ポリシーにより設定された電子メールのタイトルのプレースホルダー。  

        %%content%% - ポリシーにより設定されたエンド ユーザー向けコンテンツのプレースホルダー。  
     
4. **[テンプレートのアップロード]** をクリックして、作成したファイルを選択します。 

5. 次に、**[テスト メールの送信]** をクリックしてテスト メールを自分自身に送信し、作成したテンプレートの例を確認します。 電子メールは、ポータルへのログインに使用されたアカウントに送信されます。 テスト メールでは、メタデータ フィールド、テンプレート、電子メールの件名、電子メール本文のタイトルと内容を確認できます。  電子メール テンプレートのサンプルを次に示します。 



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
  

  
  

  
    
## <a name="see-also"></a>参照  
[Cloud Discovery のセットアップ](set-up-cloud-discovery.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  