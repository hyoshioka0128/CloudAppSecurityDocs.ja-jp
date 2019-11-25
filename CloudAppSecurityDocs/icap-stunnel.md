---
title: Cloud App Security の安全な ICAP による外部 DLP 統合
description: この記事では、Cloud App Security と stunnel セットアップで ICAP 接続を構成するために必要な手順について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9656f6c6-7dd4-4c4c-a0eb-f22afce78071
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 26046b25636523aab8494dcb122660d94e3182b9
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460730"
---
# <a name="external-dlp-integration"></a>外部 DLP 統合

*適用対象: Microsoft Cloud App Security*

Microsoft Cloud App Security は既存の DLP ソリューションと統合し、コントロールをクラウドに拡張できます。同時に、オンプレミスとクラウドを問わず、アクティビティ全体で一貫性のある統合ポリシーが維持されます。 このプラットフォームは、REST API や ICAP など、使いやすいインターフェイスをエクスポートします。Symantec Data Loss Prevention (以前の Vontu Data Loss Prevention) や Forcepoint DLP など、コンテンツ分類システムと統合できます。 

統合は標準 ICAP プロトコルを使用して行われます。これは [RFC 3507](https://tools.ietf.org/html/rfc3507) に説明のある http 型のプロトコルです。 ICAP のデータ転送を守るために、DLP ソリューションと Cloud App Security の間に安全な SSL トンネル (stunnel) を構築する必要があります。 stunnel を構築することで、DLP サーバーと Cloud App Security の間で送信されるデータが TLS で暗号化されます。 

本ガイドでは、Cloud App Security と stunnel セットアップで ICAP 接続を構成し、通信を保護するために必要な手順について説明します。


## <a name="architecture"></a>アーキテクチャ
Cloud App Security はクラウド環境をスキャンします。ファイル ポリシー構成に基づき、内部 DLP エンジンと外部 DLP のいずれを利用してファイルをスキャンするのかを決定します。 外部 DLP スキャンが適用される場合、ファイルは安全なトンネルを経由して顧客環境に送信され、顧客環境で ICAP アプライアンスに中継され、DLP 判定が行われます (許可またはブロック)。 応答は stunnel 経由で Cloud App Security に返されます。このとき、ポリシーを利用し、通知、隔離、共有コントロールなど、後続のアクションが決定されます。

![stunnel アーキテクチャ](./media/icap-architecture-stunnel.png)

Cloud App Security は Azure で実行されます。Azure での展開により高いパフォーマンスが一時停止されます。 ただし、他のクラウドやオンプレミスでの展開など、他の選択肢もあります。 他の環境で展開する場合、待機時間が長く、スループットが低いため、パフォーマンスが低下することがあります。 トラフィックを暗号化するために、ICAP サーバーと stunnel を同じネットワークに展開する必要があります。

## <a name="prerequisites"></a>必要条件
Cloud App Security で stunnel 経由でデータを ICAP サーバーに送信するには、Cloud App Security で使用される外部 IP アドレスに DMZ ファイアウォールを開きます。このとき、動的ソース ポート番号を使用します。 

1.  ソース アドレス: [「前提条件」の「アプリを接続する」](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md#prerequisites)を参照
2.  ソース TCP ポート: 動的
3.  宛先アドレス: 後続の手順で構成する外部 ICAP サーバーに接続されている stunnel の 1 または 2 つの IP アドレス
4.  宛先 TCP ポート: ネットワークに定義されている宛先 TCP ポート

> [!NOTE] 
> 既定では、stunnel ポート番号は 11344 に設定されます。 これは必要に応じて別のポートに変更できますが、新しいポート番号を必ず書き留めてください。次の手順で入力する必要があります。

## <a name="step-1--set-up-icap-server"></a>手順 1: ICAP サーバーを設定する

ICAP サーバーを設定します。ポート番号を書き留め、 **[モード]** を **[ブロック]** に設定します。 ブロック モードでは、分類判定を Cloud App Security に戻すように ICAP サーバーが設定されます。

このセットアップを行う方法については、外部 DLP 製品のマニュアルを参照してください。 例については、「[付録 A: ForcePoint ICAP サーバー セットアップ](#forcepoint)」および「[付録 B: Symantec 展開ガイド](#symantec)」をご覧ください。

## <a name="step-2--set-up-your-stunnel-server"></a>手順 2: stunnel サーバーを設定する 

この手順では、ICAP サーバーに接続される stunnel を設定します。 

>[!NOTE]
> この手順は強く推奨されますが、任意です。テスト ワークロードでは省略できます。 

### <a name="install-stunnel-on-a-server"></a>サーバーに stunnel をインストールする

**必要条件**

- **サーバー** - Windows Server または Linux サーバー (メジャー ディストリビューション)。

stunnel インストール対応のサーバーの種類については、[stunnel Web サイト](https://www.stunnel.org/index.html)をご覧ください。 Linux を使用している場合、Linux ディストリビューション マネージャーでインストールできます。

#### <a name="install-stunnel-on-windows"></a>Windows に stunnel をインストールする

1. [最新の Windows Server インストールをダウンロードします](https://www.stunnel.org/downloads.html) (このアプリケーションは最近のあらゆる版の Windows Server で可能になっています)。
   (既定のインストール)

2. インストール中に、新しい自己署名証明書を作成しないでください。 証明書は後の手順で作成します。

3. **[Start server after installation]\(インストール後にサーバーを起動する\)** をクリックします。

4. 次のいずれかの方法で証明書を作成します。

   - 証明書管理サーバーを使用して、ICAP サーバー上で SSL 証明書を作成します。 その後、stunnel インストール用に用意したサーバーにキーをコピーします。
   - あるいは、stunnel サーバーで、次の OpenSSL コマンドを利用して秘密キーと自己署名証明書を生成します。 次の変数を置き換えます。
     - **key.pem** を秘密キーの名前に変更
     - **cert.pem** を証明書の名前に変更
     - **stunnel-key** を新しく作成したキーの名前に変更

5. stunnel インストール パスの下で、config ディレクトリを開きます。 既定では、c:\Program Files (x86)\stunnel\config\ です。
6. 管理者アクセス許可で次のコマンド ラインを実行します。     `..\bin\openssl.exe genrsa -out key.pem 2048 `
      
     ` ..\bin\openssl.exe  req -new -x509 -config ".\openssl.cnf" -key key.pem -out .\cert.pem -days 1095`

7. cert.pem と key.pem を連結し、ファイルに保存します。 `type cert.pem key.pem >> stunnel-key.pem`

8. [公開キーをダウンロードし](https://adaprodconsole.blob.core.windows.net/icap/publicCert.pem)、**C:\Program Files (x86)\stunnel\config\MCASca.pem** に保存します。

9. Windows ファイアウォールでポートを開くための次の規則を追加します。

       rem Open TCP Port 11344 inbound and outbound
       netsh advfirewall firewall add rule name="Secure ICAP TCP Port 11344" dir=in action=allow protocol=TCP localport=11344
       netsh advfirewall firewall add rule name="Secure ICAP TCP Port 11344" dir=out action=allow protocol=TCP localport=11344

10. `c:\Program Files (x86)\stunnel\bin\stunnel.exe` を実行し、stunnel アプリケーションを開きます。 

11. **[構成]** をクリックし、 **[構成の編集]** をクリックします。

    ![Windows Server 構成を編集する](./media/stunnel-windows.png)
 
12. ファイルを開き、次のサーバー構成行を貼り付けます。 **DLP Server IP** は ICAP サーバーの IP アドレスです。**stunnel-key** は前の手順で作成したキーです。**MCASCAfile** は Cloud App Security stunnel クライアントの公開証明書です。 サンプルがあればそれを削除し (例では Gmail テキストを確認できます)、次のテキストをファイルにコピーします。

        [microsoft-Cloud App Security]
        accept = 0.0.0.0:11344
        connect = **ICAP Server IP**:1344
        cert = C:\Program Files (x86)\stunnel\config\**stunnel-key**.pem
        CAfile = C:\Program Files (x86)\stunnel\config\**MCASCAfile**.pem
        TIMEOUTclose = 0
        client = no
13. ファイルを保存し、 **[構成の再読み込み]** をクリックします。

14. 予想どおり動作していることを確認するには、コマンド プロンプトから次を実行します。 `netstat -nao  | findstr 11344`
 

#### <a name="install-stunnel-on-ubuntu"></a>Ubuntu に stunnel をインストールする

次の例は Ubuntu サーバー インストールに基づきます。ルート ユーザーとしてサインインしています。他のサーバーの場合、並列コマンドを使用します。 

用意したサーバーで、最新版の stunnel をダウンロードしてインストールします。 Ubuntu サーバーで次のコマンドを実行して、stunnel と OpenSSL の両方をインストールします。

    apt-get update
    apt-get install openssl -y
    apt-get install stunnel4 -y

コンソールから次のコマンドを実行し、stunnel がインストールされていることを確認します。 バージョン番号と構成オプションの一覧が表示されるはずです。

    stunnel-version

### <a name="generate-certificates"></a>証明書を生成する

ICAP サーバーと Cloud App Security では、stunnel 全体でのサーバーの暗号化と認証に秘密キーと公開証明書が使用されます。 stunnel をバックグラウンド サービスとして実行できるように、パス フレーズなしで秘密キーを作成してください。 また、ファイルのアクセス許可を、stunnel 所有者は**読み取り可能**に、その他のユーザーは**なし**に設定してください。

次のいずれかの方法で証明書を作成できます。
- 証明書管理サーバーを使用して、ICAP サーバー上で SSL 証明書を作成します。 その後、stunnel インストール用に用意したサーバーにキーをコピーします。 
- あるいは、stunnel サーバーで、次の OpenSSL コマンドを利用して秘密キーと自己署名証明書を生成します。 次の変数を置き換えます。
    - **“key.pem”** を秘密キーの名前に変更
    - **“cert.pem”** を証明書の名前に変更
    - **“stunnel-key”** を新しく作成したキーの名前に変更
       
            openssl genrsa -out key.pem 2048
            openssl req -new -x509 -key key.pem -out cert.pem -days 1095
            cat key.pem cert.pem >> /etc/ssl/private/stunnel-key.pem

### <a name="download-the-cloud-app-security-stunnel-client-public-key"></a>Cloud App Security stunnel クライアントの公開キーをダウンロードする

から公開キーをダウンロードして、 https://adaprodconsole.blob.core.windows.net/icap/publicCert.pem **/etc/ssl/certs/MCASCAfile.pem** に保存します

### <a name="configure-stunnel"></a>stunnel を構成する 

stunnel 構成は stunnel.conf ファイルで設定されます。

1. 次のディレクトリで stunnel.conf ファイルを作成します。 **vim /etc/stunnel/stunnel.conf**

2. ファイルを開き、次のサーバー構成行を貼り付けます。  **ICAP Server IP** は ICAP サーバーの IP アドレスです。**stunnel-key** は前の手順で作成したキーです。**MCASCAfile** は Cloud App Security stunnel の公開証明書です。

        [microsoft-Cloud App Security]
        accept = 0.0.0.0:11344
        connect = **ICAP Server IP**:1344
        cert = /etc/ssl/private/**stunnel-key**.pem
        CAfile = /etc/ssl/certs/**MCASCAfile**.pem
        TIMEOUTclose = 1
        client = no


### <a name="update-your-ip-table"></a>IP テーブルを更新する
次のルート ルールで IP アドレス表を更新します。
   
    iptables -I INPUT -p tcp --dport 11344 -j ACCEPT

IP 表の更新を永続にするには、次のコマンドを使用します。

     sudo apt-get install iptables-persistent
     sudo /sbin/iptables-save > /etc/iptables/rules.v4
 

### <a name="run-stunnel"></a>stunnel を実行する
1. stunnel サーバーで、次のコマンドを実行します。

        vim /etc/default/stunnel4

2. 変数 ENABLED を 1 に変更します。

        ENABLED=1

3. サービスを再起動し、構成を有効にします。

        /etc/init.d/stunnel4 restart

4. 次のコマンドを実行し、stunnel が正しく動作していることを確認します。

        ps -A | grep stunnel

    次のコマンドを実行し、正しいポートで待機していることを確認します。

        netstat -anp | grep 11344

5. stunnel サーバーが展開されたネットワークが前述のネットワーク前提条件に一致していることを確認します。 これは、Cloud App Security から入ってくる接続がサーバーに届くための前提条件です。

プロセスが終わらない場合、[stunnel マニュアル](https://www.stunnel.org/docs.html)を参照して問題を解決してください。


## <a name="step-3--connect-to-cloud-app-security"></a>手順 3:  Cloud App Security に接続する

1. Cloud App Security の **[設定]** で、 **[セキュリティ拡張機能]** を選択し、 **[外部 DLP]** タブを選択します。

2. プラス記号をクリックし、新しい接続を追加します。 

3. **[Add new external DLP]\(新しい外部 DLP の追加\)** ウィザードに **[接続名]** を入力します (たとえば、「My Forcepoint connector」と入力します)。この名前はコネクタの識別に利用されます。

4. **[接続の種類]** を選択します。
    - **Symantec Vontu** – Vontu DLP アプライアンスにカスタマイズした統合を使用します。
    - **Forcepoint DLP** – Forcepoint DLP アプライアンスにカスタマイズした統合を使用します。
    - **Generic ICAP – REQMOD** - [要求変更](https://tools.ietf.org/html/rfc3507)を使用する他の DLP アプライアンスを使用します。
    - **Generic ICAP – RESPMOD** - [応答変更](https://tools.ietf.org/html/rfc3507)を使用する他の DLP アプライアンスを使用します。
    ![Cloud App Security ICAP 接続](./media/icap-wizard1.png)

5. stunnel に接続するために前の手順で生成したパブリック証明書 "cert.pem" を参照して選択します。 **[次へ]** をクリックします。

   > [!NOTE]
   > **[Use secure ICAP]\(安全な ICAP を使用する\)** ボックスを選択し、stunnel ゲートウェイを暗号化することが推奨されます。 テストが目的の場合、または stunnel サーバーがない場合は、このボックスをオフにして、DLP サーバーと直接統合します。 

5. **[サーバー構成]** 画面で、手順 2 で設定した stunnel サーバーの **[IP アドレス]** と **[ポート]** を指定します。 負荷分散が目的の場合は、追加のサーバーの **[IP アドレス]** と **[ポート]** を構成できます。 指定する IP アドレスは、サーバーの外部静的 IP アドレスになります。

   ![Cloud App Security ICAP 接続](./media/icap-wizard2.png)
6. **[次へ]** をクリックします。 Cloud App Security により、構成したサーバーへの接続がテストされます。 エラーが発生した場合、マニュアルとネットワーク設定を見直してください。 正常に接続されたら、 **[終了]** をクリックします。

7. 次に、この外部 DLP サーバーにトラフィックを送るために、 **[コンテンツ検査方法]** で**ファイル ポリシー**を作成するときに、先ほど作成した接続を選択します。 ファイル ポリシーの作成方法については[こちら](data-protection-policies.md)をご覧ください。


## 付録 A: ForcePoint ICAP サーバー セットアップ <a name="forcepoint"></a>

ForcePoint で、次の手順でアプライアンスを設定します。

1.  DLP アプライアンスで、 **[展開]**  >  **[システム モジュール]** の順に移動します。 

    ![ICAP 展開](./media/icap-system-modules.png)

2.  **[全般]** タブで **[ICAP サーバー]** が **[有効]** になっていること、 **[ポート]** が **[1344]** に設定されていることを確認します。 また、 **[Allow connection to this ICAP Server from the following IP addresses]\(次の IP アドレスからこの ICAP サーバーへの接続を許可する\)** で **[任意の IP アドレス]** を選択します。
 
    ![ICAP 構成](./media/icap-ip-address.png)

3.  HTTP/HTTPS タブで、 **[モード]** を **[ブロック]** に設定します。
 
    ![ICAP ブロック](./media/icap-blocking.png)
 

## 付録 B: Symantec 展開ガイド <a name="symantec"></a>

サポートされている Symantec DLP のバージョンは、11 以降です。 

前述のように、Cloud App Security テナントが存在するのと同じ Azure データセンターに検出サーバーを展開する必要があります。 検出サーバーは、専用の IPSec トンネルを通して適用サーバーと同期します。 
 
### <a name="detection-server-installation"></a>検出サーバーのインストール 
Cloud App Security によって使われる検出サーバーは、Web サーバーの標準的な Network Prevent です。 いくつかの構成オプションを変更する必要があります。
1. **[Trial Mode]\(トライアル モード\)** を無効にします。
   1. **[System]\(システム\)**  >  **[Servers and Detectors]\(サーバーとディテクター\)** で、ICAP ターゲットをクリックします。 
    
      ![ICAP ターゲット](./media/icap-target.png)
    
   2. **[Configure]\(構成\)** をクリックします。 
    
      ![ICAP ターゲットを構成する](./media/configure-icap-target.png)
    
   3. **[Trial Mode]\(トライアル モード\)** を無効にします。
    
      ![トライアル モードを無効にする](./media/icap-disable-trial-mode.png)
    
2. **[ICAP]**  >  **[Response Filtering]\(応答フィルタリング\)** で、 **[Ignore Responses Smaller Than]\(次の値より小さい応答を無視する\)** の値を 1 に変更します。


3. そして、 **[Inspect Content Type]\(コンテンツ タイプを調べる\)</em>** のリストに "application/\*" を追加します。
     ![コンテンツ タイプを調べる](./media/icap-inspect-content-type.png)

4. **[Save]\(保存\)** をクリックします。


### <a name="policy-configuration"></a>ポリシーの構成
Cloud App Security は Symantec DLP に含まれるすべての検出ルール タイプをシームレスにサポートするので、既存のルールを変更する必要はありません。 ただし、完全な統合を可能にするために既存と新規のすべてのポリシーに適用する必要がある構成の変更があります。 特定の応答ルールに加えて、すべてのポリシーでこの変更を行います。 

構成の変更を Vontu に追加します。

1.  **[Manage]\(管理\)**  >  **[Policies]\(ポリシー\)**  >  **[Response Rules]\(応答ルール\)** に移動し、 **[Add Response Rule]\(応答ルールの追加\)** をクリックします。
    
    ![応答ルールを追加する](./media/icap-add-response-rule.png)

2.  **[Automated Response]\(自動応答\)** が選ばれていることを確認し、 **[Next]\(次へ\)** をクリックします。

    ![自動応答](./media/icap-automated-response.png)

3. ルール名を入力します (例: **Block HTTP/HTTPS**)。 **[Actions]\(アクション\)** で **[Block HTTP/HTTPS]\(HTTP/HTTPS をブロック\)** を選び、 **[Save]\(保存\)** をクリックします。

    ![http をブロック](./media/icap-block-http.png)

作成したルールをすべての既存ポリシーに追加します。

1. [Policy]\(ポリシー\) で **[Response]\(応答\)** タブに移動します。

2. **[Response rule]\(応答ルール\)** ドロップダウンから、上で作成した応答ブロック ルールを選びます。

3. ポリシーを保存します。
   
    ![トライアル モードを無効にする](./media/icap-add-policy.png)

既存のすべてのポリシーにこのルールを追加する必要があります。

>[!NOTE]
> Symantec vontu を使用して Dropbox のファイルをスキャンした場合、ファイルは CAS によって自動的に http://misc/filename から始まる URL で表示されます。このプレースホルダー URL は、実際にはどこにもつながっておらず、ログ目的で使用されます。


## <a name="next-steps"></a>次のステップ 
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  
