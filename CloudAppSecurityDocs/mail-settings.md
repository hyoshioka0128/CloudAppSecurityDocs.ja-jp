---
title: 電子メールの通知の基本設定 |Microsoft Docs
description: この記事では、Cloud App Security によって送信された電子メール通知を個人用に設定する方法について情報を提供します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/16/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 8402cdc9-4969-4150-b567-ccc9d75e5370
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 2d1621dd7a1e082631b941ecfb711a686a69991a
ms.sourcegitcommit: 851ff017c226435d38bed18dbece640a632cd2a0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2018
ms.locfileid: "51943703"
---
# <a name="email-notification-preferences"></a>電子メールの通知の基本設定

*適用対象: Microsoft Cloud App Security*

この記事では、Cloud App Security によって送信された電子メール通知を個人用に設定する方法について情報を提供します。

## <a name="mailsettings"></a> 電子メールの通知の基本設定  

 Microsoft Cloud App Security では、アラートを要求している管理者、および侵害に関係のあるエンド ユーザーに、メール通知が送信されます。 メール通知のパラメーターを設定するには、次の手順のようにします。 迷惑メール対策サービスにホワイトリスト登録すべきMicrosoft Cloud App Security 電子メール サーバーの IP アドレスの詳細については、「[ネットワーク要件](network-requirements.md)」をご覧ください。

1. メニュー バーで設定の歯車アイコンをクリックし、**[設定]** を選択して、**[メールの設定]** タブを選択します。  

   ![メールの設定](./media/mail-settings-config.png)

2. **[メール送信者の ID]**: 既定の電子メール設定を使用する予定の場合、このセクションでは何も変更する必要はありません。 メール送信者の ID をカスタマイズするには、変更するフィールドをカスタマイズする設定をここで行います。 次の項目のいずれか、またはすべてを変更することができます。**[送信元表示名]**、**[送信元メール アドレス]**、**[返信用メール アドレス]**。 Microsoft Cloud App Security では、これを実現するために、MailChimp® というサード パーティのメール サービスを使用することで、カスタマイズを実現します。 カスタマイズを有効にするには、MailChimp のサービス利用規約とプライバシーに関する声明を確認して同意する必要があります。 そうしないと、Microsoft Cloud App Security では既定の設定を使用して通知が送信されます。
 
   > [!NOTE]
   > [rfc822 標準](http://www.rfc-editor.org/rfc/rfc822.txt)に従い、表示名と電子メール アドレスには Unicode 文字のみがサポートされています。

  
3. [**メールのデザイン**] では、HTML ファイルを使用すると、システムから送信される電子メール メッセージのカスタマイズやデザインを行えます。 テンプレートに使用される HTML ファイルには次の設定が含まれます。  
  
   - すべてのテンプレートの CSS ファイルは、テンプレート内でインラインである必要があります。  
  
   - テンプレートには、次の 3 つの編集不可能なプレースホルダーが必要です。  
  
        - **%%logo%%** - [全般設定] ページでアップロードされた企業のロゴの URL。  
  
        - **%%title%%** - ポリシーにより設定された電子メールのタイトルのプレースホルダー。  

        - **%%content%%** - ポリシーにより設定されたエンド ユーザー向けコンテンツのプレースホルダー。  

4. [**テンプレートのアップロード**] をクリックして、作成したファイルを選択します。 

5. **[テスト メールの送信]** をクリックして、作成したテンプレートの例のメールを自分自身に送信し。 電子メールは、ポータルへのログインに使用されたアカウントに送信されます。 テスト メールで、次の項目を確認します。
    - メタデータ フィールド
    - テンプレート
    - メールの件名
    - メール本文のタイトル
    - 内容

## <a name="sample-email-template"></a>サンプルのメール テンプレート

メール テンプレートのサンプルを次に示します。

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

## <a name="next-steps"></a>次の手順

[Cloud Discovery のセットアップ](set-up-cloud-discovery.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  