---
title: "継続的なレポートのために自動ログ アップロードを構成する | Microsoft Docs"
description: "このトピックでは、Ubuntu の Docker を使って Cloud App Security で継続的なレポートの自動ログ アップロードを構成するプロセスについて説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/6/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cc29a6cb-1c03-4148-8afd-3ad47003a1e3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: dba7c5cf9a5160e4bd6be4a236f8e64ac4a412e2
ms.sourcegitcommit: d012fc1a099773bd9e9dc61906faab68dae0e996
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2017
---
# <a name="set-up-and-configuration-on-ubuntu"></a>Ubuntu でのセットアップと構成

> [!NOTE]
> この機能はテナントに段階的にロールアウトされています。 プレビューに参加したい場合は、サポートにお問い合わせください。

## <a name="technical-requirements"></a>技術要件

-   OS: Ubuntu 14.04 以降

-   ディスク領域: 250 GB

-   CPU: 2

-   RAM: 4 GB

-   ファイアウォールの設定:

    -   ログ コレクターが着信 FTP および Syslog トラフィックを受信できる。

    -   ログ コレクターがポート 443 でポータル (contoso.cloudappsecurity.com など) への発信トラフィックを開始できる。

## <a name="log-collector-performance"></a>ログ コレクターのパフォーマンス

ログ コレクターは、1 時間あたり最大 50 GB の容量のログを処理できます。 ログ収集プロセスの主なボトルネックは次のとおりです。

-   ネットワーク帯域幅 - ネットワーク帯域幅によって、ログのアップロード速度が決まります。

-   IT 部門によって割り当てられた仮想マシンの I/O パフォーマンス - ログ コレクターのディスクにログが書き込まれる速度が決まります。 ログ コレクターには、ログの収集速度を監視して、アップロード速度と比較する安全メカニズムが組み込まれています。 輻輳の場合、ログ コレクターは、ログ ファイルの削除を開始します。 全体的に 1 時間あたり 50 GB を超える状況であったら、複数のログ コレクターにトラフィックを分割することをお勧めします。

## <a name="set-up-and-configuration"></a>セットアップと構成  

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>ステップ 1: Web ポータルの構成: データ ソースを定義し、それをログ コレクターにリンクする

1.  自動アップロードの設定ページに移動します。  <br></br>Cloud App Security ポータルで、設定アイコン ![設定アイコン](./media/settings-icon.png) をクリックしてから **[ログ コレクター]** をクリックします。

2.  ログをアップロードするファイアウォールまたはプロキシそれぞれに対応するデータ ソースを作成します。

    ![ubuntu1](./media/ubuntu1.png)

    」を参照します。 [**データ ソースの追加**] をクリックします。

    b. プロキシまたはファイアウォールの [**名前**] を付けます。

    c. [**ソース**] リストからアプライアンスを選択します。 一覧に明示されていないネットワーク アプライアンスを処理するために **[カスタム ログ形式]** を選ぶ場合、構成方法の詳細については「[カスタム ログ パーサーの使用](custom-log-parser.md)」を参照してください。

    d. 予想されるログ形式のサンプルとログを比較します。 ログ ファイルの形式がこのサンプルと一致しない場合は、データ ソースを [**その他**] として追加する必要があります。

    e. **[レシーバーの種類]** を、**[FTP]**、**[FTPS]**、**[Syslog – UDP]**、**[Syslog – TCP]**、または **[Syslog – TLS]** に設定します。
    >[!NOTE]
    >多くの場合、セキュリティで保護された転送プロトコル (FTPS、Syslog – TLS) と統合するには、ファイアウォール/プロキシの追加設定が必要です。

    f. ネットワークのトラフィックを検出するために使用できるログの取得先であるファイアウォールおよびプロキシそれぞれに対して、この手順を繰り返します。

3.  画面上部の [**ログ コレクター**] タブに移動します。

    」を参照します。 [**ログ コレクターを追加**] をクリックします。

    b. ログ コレクターに [**名前**] を付けます。

    c. Docker の展開に使うコンピューターの**ホスト IP アドレス**を入力します。

    d. コレクターに接続するすべての**データ ソース**を選び、**[更新]** をクリックして構成を保存します。次の展開手順を参照してください。

    ![ubuntu2](./media/ubuntu2.png)

    >  [!NOTE]
    > - 1 つのログ コレクターで複数のデータ ソースを処理できます。
    >- Cloud App Security と通信するようにログ コレクターを構成するときに情報が必要になるため、画面の内容をコピーします。 Syslog を選択した場合、この情報には、Syslog リスナーがリッスンするポートに関する情報が含まれます。

4.  展開の詳細が表示されます。

 ![ubuntu3](./media/ubuntu3.png)

5.  ダイアログから実行コマンドを**コピー**します。 クリップボードにコピー アイコン ![クリップボードにコピー アイコン](./media/copy-icon.png) を使えます。

6.  予想されるデータ ソース構成を**エクスポート**します。 この構成では、アプライアンスでログのエクスポートを設定する方法を記述します。

  ![ubuntu4](./media/ubuntu4.png)

### <a name="step-2--on-premises-deployment-of-your-machine"></a>ステップ 2 – コンピューターのオンプレミスの展開

> [!Note]
> 次の手順は、Ubuntu での展開について説明したものです。 他のプラットフォームの展開手順は若干異なります。

1.  Ubuntu コンピューターでターミナルを開きます。

2.  コマンド `sudo -i` を使ってルート権限に変更します。

3.  古いバージョンをアンインストールし、次のコマンドを実行して Docker CE をインストールします。

    `curl -o /tmp/MCASInstallDocker.sh
    https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh
    && chmod +x /tmp/MCASInstallDocker.sh; sudo /tmp/MCASInstallDocker.sh`

    ![ubuntu5](./media/ubuntu5.png)

4.  ポータルで生成された実行コマンドを使って、コレクター イメージを展開します。

    ![ubuntu6](./media/ubuntu6.png)

    >[!NOTE]
    >プロキシを構成する必要がある場合は、プロキシ IP アドレスとポートを追加します。 たとえば、プロキシの詳細が 192.168.10.1:8080 の場合は、次のように実行コマンドを更新します。<br></br>
     `sudo docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e
    "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e
    "TOKEN=41f8f442c9a30519a058dd3bb9a19c79eb67f34a8816270dc4a384493988863a" -e
    "CONSOLE=tenant2.eu1-rs.adallom.com" -e "COLLECTOR=MyLogCollector" --security-opt
    apparmor:unconfined --cap-add=SYS_ADMIN -dt microsoft/caslogcollector starter`

    ![ubuntu7](./media/ubuntu7.png)

5.  次のコマンドを実行して、コレクターが正しく動作していることを確認します。`docker logs \<collector_name\>`

"**Finished successfully!**" というメッセージが表示される必要があります。

  ![ubuntu8](./media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>ステップ 3 - ネットワーク機器のオンプレミス構成

ネットワーク ファイアウォールとプロキシを、ダイアログの指示に従って FTP ディレクトリの専用 Syslog ポートにログが定期的にエクスポートされるように構成します。以下に例を示します。

    BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>ステップ 4 - Cloud App Security ポータルで正常に展開されたことを確認する

**[ログ コレクター]** の表でコレクターの状態をチェックし、状態が **[接続済み]** であることを確認します。 **[作成済み]** の場合、ログ コレクターの接続と解析が完了していない可能性があります。

 ![ubuntu9](./media/ubuntu9.png)

**ガバナンス ログ**に移動して、ログがポータルに定期的にアップロードされていることを確認することもできます。

展開中に問題が発生した場合は、「[クラウド検出のトラブルシューティング](troubleshooting-cloud-discovery.md)」を参照してください。

### <a name="optional---create-custom-continuous-reports"></a>省略可能 - カスタムの継続的レポートを作成する

ログが Cloud App Security にアップロードされ、レポートが生成されていることを確認したら、カスタム レポートを作成できます。 Azure Active Directory ユーザー グループに基づいて、カスタム検出レポートを作成できるようになりました。 たとえば、マーケティング部門のクラウドの使用状況を確認したい場合は、ユーザー グループのインポート機能を使用してマーケティング グループをインポートして、このグループにカスタム レポートを作成できます。 また、IP アドレス タグや IP アドレスの範囲に基づいてレポートをカスタマイズすることもできます。

1. Cloud App Security ポータルの設定の歯車アイコンをクリックし、**[Cloud Discovery の設定]** を選択し、**[継続的レポートの管理]** を選択します。 
2. **[レポートの作成]** ボタンをクリックし、フィールドに入力します。
3. **[フィルター]** では、データ ソース、[インポートされたユーザー グループ](user-groups.md)、または [IP アドレスのタグと範囲](ip-tags.md)を指定してフィルターすることができます。 

![カスタムの継続的レポート](./media/custom-continuous-report.png)

## <a name="see-also"></a>参照
[Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)  
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください](http://support.microsoft.com/oas/default.aspx?prid=16031)  
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます](https://premier.microsoft.com/)

