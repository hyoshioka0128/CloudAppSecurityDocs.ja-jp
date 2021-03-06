---
title: Azure での Docker を使用した自動ログ アップロードを構成する
description: この記事では、Azure での Ubuntu または RHEL 上で Docker を使用して、Cloud App Security の継続的レポート用にログの自動アップロードを構成するプロセスについて説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/19/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 1c058f817e4fffa4f40060ad0bc865bb6798e771
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74460812"
---
# <a name="set-up-and-configuration-on-ubuntu-or-rhel-in-azure"></a>Azure での Ubuntu または RHEL 上での設定および構成

*適用対象: Microsoft Cloud App Security*

Azure での Ubuntu または Red Hat Enterprise Linux (RHEL) 上で Docker を使用して、Cloud App Security の継続的レポート用にログの自動アップロードを構成することができます。 この記事では、自動ログ アップロードを設定する方法について説明します。

## <a name="prerequisites"></a>必要条件

* OS: Ubuntu 14.04 および 16.04 (新しいバージョンの場合は、サポートにお問い合わせください)、RHEL 7.2 以上、または CentOS 7.2 以上

* ディスク領域: 250 GB

* CPU: 2

* RAM: 4 GB

* [ネットワーク要件](network-requirements.md#log-collector)で説明されているとおりにファイアウォールを設定する

> [!NOTE]
> 既存のログコレクターがあり、それを再度配置する前に削除する場合、または単に削除する場合は、次のコマンドを実行します。
>
> ```console
> docker stop <collector_name>
> docker rm <collector_name>
> ```

## <a name="log-collector-performance"></a>ログ コレクターのパフォーマンス

ログ コレクターは、1 時間あたり最大 50 GB の容量のログを処理できます。 ログ収集プロセスの主なボトルネックは次のとおりです。

* ネットワーク帯域幅 - ネットワーク帯域幅によって、ログのアップロード速度が決まります。

* 仮想マシンの I/O パフォーマンス - ログ コレクターのディスクにログが書き込まれる速度が決まります。 ログ コレクターには、ログの収集速度を監視して、アップロード速度と比較する安全メカニズムが組み込まれています。 輻輳の場合、ログ コレクターは、ログ ファイルの削除を開始します。 1 時間あたり 50 GB を超えるのが普通である場合は、複数のログ コレクターにトラフィックを分割することをお勧めします。

## <a name="set-up-and-configuration"></a>セットアップと構成  

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>ステップ 1: Web ポータルの構成: データ ソースを定義し、それをログ コレクターにリンクする

1. **[自動ログ アップロード]** 設定ページに移動します。

    1. Cloud App Security ポータルで、設定アイコンをクリックした後、 **[ログ コレクター]** をクリックします。

    ![設定アイコン](media/settings-icon.png)

1. ログをアップロードするファイアウォールまたはプロキシそれぞれに対応するデータ ソースを作成します。

    1. **[データ ソースの追加]** をクリックします。  
    データソース](media/add-data-source.png) を追加 ![には
    1. プロキシまたはファイアウォールの **[名前]** を付けます。  
      ![ubuntu1](media/ubuntu1.png)
    1. **[ソース]** リストからアプライアンスを選択します。 一覧に表示されていないネットワーク アプライアンスを使用するために **[カスタム ログ形式]** を選ぶ場合、構成方法の詳細については[カスタム ログ パーサーの使用](custom-log-parser.md)に関するページをご覧ください。
    1. 予想されるログ形式のサンプルとログを比較します。 ログ ファイルの形式がこのサンプルと一致しない場合は、データ ソースを **[その他]** として追加する必要があります。
    1. **[レシーバーの種類]** を、 **[FTP]** 、 **[FTPS]** 、 **[Syslog – UDP]** 、 **[Syslog – TCP]** 、または **[Syslog – TLS]** に設定します。

    >[!NOTE]
    >多くの場合、セキュリティで保護された転送プロトコル (FTPS、Syslog – TLS) と統合するには、ファイアウォール/プロキシの追加設定が必要です。

    f. ネットワークのトラフィックを検出するために使用できるログの取得先であるファイアウォールおよびプロキシそれぞれに対して、この手順を繰り返します。 ネットワーク デバイスごとに専用のデータ ソースを設定することをお勧めします。これにより、次のことができるようになります。

    * 調査目的で、各デバイスの状態を個別に監視する。
    * 各デバイスが異なるユーザー セグメントで使用されている場合、デバイスごとに Shadow IT Discovery を調べる。

1. 画面上部の **[ログ コレクター]** タブに移動します。

    1. **[ログ コレクターを追加]** をクリックします。
    1. ログ コレクターに **[名前]** を付けます。
    1. Docker の展開に使用するコンピューターの **[ホスト IP アドレス]** を入力します。 ホスト名を解決する DNS サーバー (または同等の機能) がある場合、ホスト IP アドレスをコンピューター名で置換できます。
    1. コレクターに接続するすべての**データソース**を選択し、 **[更新]** をクリックして構成を保存します。  
    ![ubuntu2](media/ubuntu2.png)

1. 展開の詳細が表示されます。 ダイアログから実行コマンドを**コピー**します。 [クリップボードにコピー] アイコンを使用できます。 ![クリップボードにコピー アイコン](media/copy-icon.png)

1. 予想されるデータ ソース構成を**エクスポート**します。 この構成では、アプライアンスでログのエクスポートを設定する方法を記述します。

    ![ログ コレクターを作成する](media/windows7.png)

    > [!NOTE]
    >
    > * 1 つのログ コレクターで複数のデータ ソースを処理できます。
    > * Cloud App Security と通信するようにログ コレクターを構成するときに情報が必要になるため、画面の内容をコピーします。 Syslog を選択した場合、この情報には、Syslog リスナーがリッスンするポートに関する情報が含まれます。
    > * FTP を使用して初めてログデータを送信するユーザーについては、FTP ユーザーのパスワードを変更することをお勧めします。 詳細については、「 [FTP パスワードの変更](log-collector-ftp.md#changing-the-ftp-password)」を参照してください。

### <a name="step-2--deployment-of-your-machine-in-azure"></a>ステップ 2 – Azure でのマシンの展開

> [!NOTE]
> 次の手順は、Ubuntu での展開について説明したものです。 他のプラットフォームの展開手順は若干異なります。

1. Azure 環境内で新しい Ubuntu マシンを作成します。
1. マシンが起動したら、次の手順でポートを開きます。

    1. マシン ビューで、 **[ネットワーク]** に移動して、関連するインターフェイスをダブルクリックして選択します。
    1. **[ネットワーク セキュリティ グループ]** に移動して、関連するネットワーク セキュリティ グループを選択します。
    1. **[受信セキュリティ規則]** にアクセスし、 **[追加]** をクリックして、![Ubuntu Azure](media/ubuntu-azure.png)
    1. 次の規則を追加します (**詳細設定**モード)。

    |名前|宛先ポートの範囲|プロトコル|ソース|Destination|
    |----|----|----|----|----|
    |caslogcollector_ftp|21|TCP|<ご使用のアプライアンスの IP アドレスのサブネット>|Any|
    |caslogcollector_ftp_passive|20000-20099|TCP|<ご使用のアプライアンスの IP アドレスのサブネット>|Any|
    |caslogcollector_syslogs_tcp|601-700|TCP|<ご使用のアプライアンスの IP アドレスのサブネット>|Any|
    |caslogcollector_syslogs_udp|514-600|UDP|<ご使用のアプライアンスの IP アドレスのサブネット>|Any|

    ![Ubuntu Azure の規則](media/inbound-rule.png)

1. マシンに戻って、 **[接続]** をクリックし、マシン上のターミナルを開きます。

1. `sudo -i` を使ってルート権限に変更します。

1. [ソフトウェア ライセンス条項](https://go.microsoft.com/fwlink/?linkid=862492)に同意したら、古いバージョンをアンインストールし、次のコマンドを実行して Docker CE をインストールします。

    ```bash
    curl -o /tmp/MCASInstallDocker.sh https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh && chmod +x /tmp/MCASInstallDocker.sh; /tmp/MCASInstallDocker.sh
    ```

    ![Ubuntu Azure のコマンド](media/ubuntu-azure-command.png)

1. Cloud App Security ポータルの **[Create new log collector] \(新しいログ コレクターの作成\)** ウィンドウで、ホスト マシンでコレクター構成をインポートするコマンドをコピーします。

    ![Ubuntu Azure](media/windows7.png)

1. ログ コレクターを展開するコマンドを実行します。

    ```bash
    (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter
    ```

    ![Ubuntu プロキシ](media/ubuntu-proxy.png)

1. コマンド `Docker logs <collector_name>` を実行して、ログ コレクターが正しく動作していることを確認します。 ”**Finished successfully!** ” という結果を受け取ります。

    ![ubuntu8](media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>ステップ 3: ネットワーク機器のオンプレミス構成

ネットワーク ファイアウォールとプロキシを、ダイアログの指示に従って FTP ディレクトリの専用 Syslog ポートにログが定期的にエクスポートされるように構成します。 たとえば、次のようになります。

```bash
BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\
```

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>ステップ 4 - Cloud App Security ポータルで正常に展開されたことを確認する

**[ログ コレクター]** の表でコレクターの状態をチェックし、状態が **[接続済み]** であることを確認します。 **[作成済み]** の場合は、ログ コレクターの接続と解析が完了していない可能性があります。

![ubuntu9](media/ubuntu9.png)

**ガバナンス ログ**に移動して、ログがポータルに定期的にアップロードされていることを確認することもできます。

展開中に問題が発生した場合は、「[Troubleshooting Cloud Discovery](troubleshooting-cloud-discovery.md)」(Cloud Discovery のトラブルシューティング) を参照してください。

### <a name="optional---create-custom-continuous-reports"></a>省略可能 - カスタムの継続的レポートを作成する

ログが Cloud App Security にアップロードされていること、およびレポートが生成されることを確認します。 検証の後、カスタム レポートを作成します。 Azure Active Directory ユーザー グループに基づいて、カスタム検出レポートを作成できます。 たとえば、マーケティング部門のクラウドの使用状況を確認する場合、ユーザー グループのインポート機能を使用してマーケティング グループをインポートします。 次に、このグループに対するカスタム レポートを作成します。 また、IP アドレス タグや IP アドレスの範囲に基づいてレポートをカスタマイズすることもできます。

1. Cloud App Security ポータルの設定歯車アイコンで、Cloud Discovery の設定を選択して、 **[継続的レポート]** を選択します。 
1. **[レポートの作成]** ボタンをクリックし、フィールドに入力します。
1. **[フィルター]** では、データ ソース、[インポートされたユーザー グループ](user-groups.md)、または [IP アドレスのタグと範囲](ip-tags.md)を指定してフィルターすることができます。 

     ![カスタムの継続的レポート](media/custom-continuous-report.png)

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [ログコレクターの FTP 構成](log-collector-ftp.md)

[!INCLUDE [Open support ticket](includes/support.md)]
