---
title: "継続的なレポートのために自動ログ アップロードを構成する | Microsoft Docs"
description: "このトピックでは、Ubuntu の Docker を使用して、Cloud App Security での継続的なレポートのために、自動ログ アップロードを構成する手順について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/16/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cc29a6cb-1c03-4148-8afd-3ad47003a1e3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e32eebc75355e8016fcdb62a1b113431db346c31
ms.sourcegitcommit: ae4c8226f6037c5eb286eb27142d6bbb397609e9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2017
---
# <a name="set-up-and-configuration-on-ubuntu"></a>Ubuntu のセットアップと構成

## <a name="technical-requirements"></a>技術要件

-   OS: Ubuntu 14.04 以降

-   ディスク領域: 250 GB

-   CPU: 2

-   RAM: 4 GB

-   ファイアウォールの設定:

    -   ログ コレクターが着信 FTP および Syslog トラフィックを受信できる

    -   ログ コレクターがポート 443 でポータル (contoso.cloudappsecurity.com など) への発信トラフィックを開始できる

## <a name="log-collector-performance"></a>ログ コレクターのパフォーマンス

ログ コレクターは、1 時間あたり最大 50 GB の容量のログを処理できます。 ログ収集プロセスの主なボトルネックは次のとおりです。

-   ネットワーク帯域幅 - ネットワーク帯域幅によって、ログのアップロード速度が決まります。

-   IT 部門によって割り当てられた仮想マシンの I/O パフォーマンス - ログ コレクターのディスクにログが書き込まれる速度が決まります。 ログ コレクターには、ログの収集速度を監視して、アップロード速度と比較する安全メカニズムが組み込まれています。 輻輳の場合、ログ コレクターは、ログ ファイルの削除を開始します。 全体的に 1 時間あたり 50 GB を超える状況であれば、複数のログ コレクターにトラフィックを分割することをお勧めします。

## <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>ステップ 1 – Web ポータルの構成: データ ソースを定義し、それをログ コレクターにリンクする

1.  自動アップロードの設定ページに移動します。  <br></br>Cloud App Security ポータルで、設定アイコン ![設定アイコン](./media/settings-icon.png) をクリックしてから [**ログ コレクター**] をクリックします。

2.  ログをアップロードするファイアウォールまたはプロキシそれぞれに対応するデータ ソースを作成します。

    ![ubuntu1](./media/ubuntu1.png)

    a. [**データ ソースの追加**] をクリックします。

    b. プロキシまたはファイアウォールの [**名前**] を付けます。

    c. [**ソース**] リストからアプライアンスを選択します。

    d. 予想されるログ形式のサンプルとログを比較します。 ログ ファイルの形式がこのサンプルと一致しない場合は、データ ソースを [**その他**] として追加する必要があります。

    e. [**レシーバーの種類**] に [**FTP**]、[**FTPS**]、[**Syslog – UDP**]、[**Syslog – TCP**]、[**Syslog – TLS**] のいずれかを設定します。
    >[!NOTE]
    >多くの場合、セキュリティで保護された転送プロトコル (FTPS および Syslog – TLS) と統合するには、追加の設定またはファイアウォールやプロキシが必要です。

    f. ネットワークのトラフィックを検出するために使用できるログの取得先であるファイアウォールおよびプロキシそれぞれに対して、この手順を繰り返します。

3.  画面上部の [**ログ コレクター**] タブに移動します。

    a. [**ログ コレクターを追加**] をクリックします。

    b. ログ コレクターに [**名前**] を付けます。

    c. Docker の展開に使用するマシンの**ホスト IP アドレス**を入力します。

    d. コレクターに接続するすべての**データ ソース**を選択し、[**更新**] をクリックして構成を保存し、次の展開手順を確認します。

    ![ubuntu2](./media/ubuntu2.png)

    >  [!NOTE]
    > - 1 つのログ コレクターで複数のデータ ソースを処理できます。
    >- Cloud App Security と通信するようにログ コレクターを構成するときに情報が必要になるため、画面の内容をコピーします。 Syslog を選択した場合、この情報には、Syslog リスナーがリッスンするポートに関する情報が含まれます。

4.  詳細な展開情報が表示されます。

 ![ubuntu3](./media/ubuntu3.png)

5.  ダイアログ ボックスから実行コマンドを**コピー**します。 クリップボードにコピー アイコン ![クリップボードにコピー アイコン](./media/copy-icon.png) を使用できます。

6.  予想されるデータ ソースの構成を**エクスポート**します。 この構成は、アプライアンスでログのエクスポートをどのように設定するかを示しています。

  ![ubuntu4](./media/ubuntu4.png)

## <a name="step-2--on-premises-deployment-of-your-machine"></a>ステップ 2 – マシンのオンプレミス展開

> [!Note]
> 次のステップは、Ubuntu での展開を説明しています。 その他のプラットフォームの展開手順は、少し異なります。

1.  Ubuntu マシンでターミナルを開きます。

2.  次のコマンドを使用して、ルート権限に変更します: `Sudo - i`

3.  次のコマンドを実行して、古いバージョンをアンインストールし、Docker CE をインストールします。

    `curl -o /tmp/MCASInstallDocker.sh
    https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh
    && chmod +x /tmp/MCASInstallDocker.sh; sudo /tmp/MCASInstallDocker.sh`

    ![ubuntu5](./media/ubuntu5.png)

4.  ポータルで生成された実行コマンドを使用して、コレクター イメージを展開します。

    ![ubuntu6](./media/ubuntu6.png)

    >[!NOTE]
    >プロキシを構成する必要がある場合、プロキシ IP アドレスとポートを追加します。 たとえば、プロキシの詳細が 192.168.10.1:8080 の場合、実行コマンドは次のように更新されます。<br></br>
     `Sudo docker run --name casCollector -p 21:21 -p 20000-20099:20000-20099 -e
    "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e
    "TOKEN=41f8f442c9a30519a058dd3bb9a19c79eb67f34a8816270dc4a384493988863a" -e
    "CONSOLE=tenant2.eu1-rs.adallom.com" -e "COLLECTOR=casCollector" --security-opt
    apparmor:unconfined --cap-add=SYS_ADMIN -dt microsoft/caslogcollector starter`

    ![ubuntu7](./media/ubuntu7.png)

5.  次のコマンドを実行して、コレクターが正常に実行されていることを確認します: `Docker logs \<collector_name\>`

"**正常に完了しました**" のメッセージが表示されます。

  ![ubuntu8](./media/ubuntu8.png)

## <a name="step-4---on-premises-configuration-of-your-network-appliances"></a>ステップ 4: ネットワーク機器のオンプレミス構成

ネットワーク ファイアウォールとプロキシを、ダイアログの指示に従って FTP ディレクトリの専用 Syslog ポートにログが定期的にエクスポートされるように構成します。以下に例を示します。

    BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\

## <a name="step-5---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>ステップ 5: Cloud App Security ポータルで正常に展開されたことを確認する

**[ログ コレクター]** の表でコレクターの状態をチェックし、状態が **[接続済み]** であることを確認します。 **[作成済み]** の場合、ログ コレクターの接続と解析が完了していない可能性があります。

 ![ubuntu9](./media/ubuntu9.png)

[**ガバナンス ログ**] に移動して、ログがポータルに定期的にアップロードされていることを確認することもできます。

展開中に問題が発生した場合は、「[クラウド検出のトラブルシューティング](troubleshooting-cloud-discovery.md)」を参照してください。

## <a name="see-also"></a>関連項目
[Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)  
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)  
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)

