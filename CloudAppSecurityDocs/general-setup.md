---
title: "ポータルのカスタマイズ | Microsoft Docs"
description: "このトピックでは、ポータルをカスタマイズする最初の手順について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/21/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2e7e57b0-db54-4d75-896c-4700dd9abe48
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 49b64ea6cee1a33fd4005388d5b09cfbdcf59052
ms.openlocfilehash: b5250ccb93dda950b417bbbe3fc2e64f0bab8320


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
  
##  <a name="a-nameadminsettingsa-customize-your-admin-settings"></a><a name="Adminsettings"></a> 管理設定のカスタマイズ  
Cloud App Security の管理者としての設定をセットアップする場合、ポータルのメニュー バーでユーザー名をクリックしてから [**ユーザー設定**] を選択し、次の項目を設定します。  
  
1.  [**アカウント設定**] をクリックします。 ここでは、ユーザー自身がポータルの表示に使用する言語をカスタマイズできます。 ポータルの表示に既定の言語を使用するか、または自分用に別の言語を使用するかを設定できます。  
  
     ![カスタム ユーザー設定](./media/custom-user-settings.png "カスタム ユーザー設定")  
  
2.  [**通知**] をクリックすると、システムから送信される電子メールやテキスト通知の受信設定を変更できます。  電子メールで受信するアラートや違反の重要度を設定できます。重要度はポリシーごとに設定できるため、違反がトリガーされると、この設定と違反が発生したポリシーで設定されている重要度に基づいて電子メール通知が送信されます。 電子メールは、Cloud App Security へのログインに使用される管理者のユーザー アカウントに関連付けられているエイリアスに送信されます。 電話番号を入力してアラートや通知が送信された場合に Cloud App Security からテキスト メッセージを受信できるようにし、テキスト メッセージで通知を受信する重要度レベルを設定します。  
  
> [!NOTE] 
> テキスト メッセージで送信されるアラートの最大数は、1 つの電話番号につき 1 日あたり 10 件です。 日は UTC タイム ゾーンに従って計算されることに注意してください。 
  
  ![通知設定](./media/notification-settings.png "通知設定")  
  
3. 完了したら [**保存**] をクリックします。  
  
##  <a name="a-nameiptagsandrangesa-set-ip-ranges"></a><a name="IPtagsandRanges"></a> IP 範囲の設定  
物理的なオフィスの IP アドレスなど、既知の IP アドレスを簡単に識別するには、タグを適切に分類できるように IP アドレスの範囲を設定し、またログやアラートの表示や調査の方法をカスタマイズする必要があります。   
IP アドレス範囲の各グループは、IP カテゴリのプリセットのリストに基づいて分類したり、独自に作成した IP タグを付与したりできます。 さらに、この設定を使用して、公開されている geo ロケーション情報を内部ネットワークの情報に基づいて上書きすることができます。  
  
IPv4 と IPv6 がサポートされています。  
  
メニュー バーで設定アイコン ![設定アイコン](./media/settings-icon.png "設定アイコン") をクリックし、**[IP アドレス範囲]** を選択します。 [**+ IP アドレス範囲の追加**] をクリックし、次の項目を設定します。  
  
> [!NOTE]  
>  場所と登録された ISP は、既定値が上書きされます。   
> しかし、IP タグのデータは上書きされず、アクティビティに追加されます。  
  
1.  IP 範囲の**名前を指定**します。 この名前はアクティビティ ログでは表示されず、IP 範囲の管理にのみ使用されます。  
  
     IP 範囲を IP カテゴリに含めるには、ドロップダウン メニューからカテゴリを選択します。  
  
2.  構成する **IP アドレス範囲**を入力し、[+] ボタンをクリックします。 IP アドレスとサブネットは、192.168.1.0/32 のようなネットワーク プレフィックス表記 (CIDR 表記とも呼ばれます) を使用して、必要な数だけ追加できます。  
  
3.  これらのアドレスの**場所**または組織 (ISP) を上書きする場合は、新しい値を入力します。 たとえば、アイルランドで公開されているように思われる IP アドレスが米国内で保有されていることがわかっている場合は、この設定を上書きできます。  
  
4.  **登録された ISP**を入力します。 これでアクティビティのデータが上書きされます。  
  
5.  これらの IP アドレスからアクティビティを**タグ付け**するには、タグを入力します。 ボックスに単語を入力するとタグが作成されます。 タグを構成した後でも、リストから IP 範囲を選択すると簡単に IP 範囲を追加できます。 各範囲には、IP タグを必要な数だけ追加できます。 IP タグは、ポリシーを作成するときに使用できます。  ユーザーが構成する IP タグに加え、Cloud App Security には構成できない組み込みタグがあります。 [[IP tags filter]](activity-filters.md) (IP タグ フィルター) でタグのリストを表示することができます。  
  
6.  **IP カテゴリ**は、関心のある IP アドレスからアクティビティを簡単に認識するために使用されます。 カテゴリはポータルで使用できますが、匿名プロキシと Tor の 2 つの IP タグを含む [危険] カテゴリ以外について、それぞれのカテゴリにどの IP アドレスが含まれるかを決定するにはユーザー構成が必要です。  
  
     次の IP のカテゴリを使用できます。  
  
    -   **管理**: 管理者の IP アドレスがすべて含まれます。  
  
    -   **内部**: 内部ネットワーク、支社のオフィス、および、Wi-Fi のローミング アドレスの IP アドレスがすべて含まれます。  
  
    -   **危険**: 危険と考えられる任意の IP アドレスです。 これには、過去に見られた不審な IP アドレスや競合他社のネットワークの IP アドレスがあります。  
  
    -   **VPN**: リモート ワーカーが使用している任意の IP アドレスです。  
  
    -   **プロキシ クラウド**: クラウドで使用されているプロキシの IP アドレスです。  
  
7.  完了したら [**作成**] をクリックします。  
  
     ![新しい IP アドレス範囲](./media/newipaddress-range.png "新しい IP アドレス範囲")  
  
##  <a name="a-nameadallommailsettingsa-personalize-your-experience"></a><a name="Adallom_mailsettings"></a> エクスペリエンスの個人設定  
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
         

  
3.  [**テンプレートのアップロード**] をクリックして、作成したファイルを選択します。  
  
     次に、[**テスト メールの送信**] をクリックしてテスト メールを自分自身に送信し、作成したテンプレートの例を確認します。  
     電子メールは、ポータルへのログインに使用されたアカウントに送信されます。 テスト メールでは、メタデータ フィールド、テンプレート、電子メールの件名、電子メール本文のタイトルと内容を確認できます。  
  
## <a name="single-sign-on"></a>シングル サインオン  
Cloud App Security は Azure Active Directory と組み合わせて認証、プロビジョニング、およびライセンス認証に関連するアクティビティを行います。 シングル サインオンの管理方法の詳細については、「[Azure Active Directory のフェデレーションの互換性リスト:シングル サインオンの実装に使用できるサードパーティ ID プロバイダー](https://msdn.microsoft.com/library/azure/jj679342.aspx)」をご覧ください。  


> [!NOTE] 
> ExpressRoute を使用している場合は、Cloud App Security は Azure に展開され、[ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/) に完全に統合されます。 検出ログのアップロードを含む、Cloud App Security アプリとのすべての通信、および Cloud App Security に送信されるトラフィックは、ExpressRoute の**パブリック ピアリング**経由でルーティングされるため、待機時間、パフォーマンス、およびセキュリティが改善されます。 お客様側で設定を行う必要はありません。  
    パブリック ピアリングの詳細については、「[ExpressRoute 回線とルーティング ドメイン](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/)」を参照してください。  
    
## <a name="see-also"></a>参照  
[Cloud Discovery のセットアップ](set-up-cloud-discovery.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  


<!--HONumber=Dec16_HO4-->


