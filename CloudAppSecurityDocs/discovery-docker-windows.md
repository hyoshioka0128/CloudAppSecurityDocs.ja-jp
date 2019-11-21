---
title: Windows の Docker を使用して Cloud App Security の継続的レポートをロールアウトする | Microsoft Docs
description: この記事では、オンプレミス サーバーの Windows で Docker を使用して、Cloud App Security で継続的レポートの自動ログ アップロードを構成するプロセスについて説明します。
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
ms.openlocfilehash: b22d84e2d640a596dda11e13d416f7fec558d377
ms.sourcegitcommit: aa227a88d09eff15953d10663386f85ff68095b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74203471"
---
# <a name="docker-on-windows-on-premises"></a>オンプレミスの Windows の Docker

*適用対象: Microsoft Cloud App Security*

Windows で Docker を使用して Cloud App Security の継続的レポート用に自動ログ アップロードを構成することができます。

## <a name="prerequisites"></a>必要条件

* OS: **Windows 10** (fall creators update) or Windows Server **version 1709+**

* ディスク領域: 250 GB

* CPU: 2

* RAM: 4 GB

* [ネットワーク要件](network-requirements.md#log-collector)で説明されているとおりにファイアウォールを設定する

* Hyper-V でオペレーティング システム上の仮想化を有効にすることが必要

> [!IMPORTANT]
> A user must be signed in for Docker to collect logs. We recommend advising your Docker user's to disconnect without signing out.

> [!NOTE]
> If you have an existing log collector and want to remove it before deploying it again, or if you simply want to remove it, run the following commands:
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
    ![Add a data source](media/add-data-source.png)
    1. プロキシまたはファイアウォールの **[名前]** を付けます。  
    ![ubuntu1](media/ubuntu1.png)
    1. **[ソース]** リストからアプライアンスを選択します。 一覧に表示されていないネットワーク アプライアンスを使用するために **[カスタム ログ形式]** を選ぶ場合、構成方法の詳細については[カスタム ログ パーサーの使用](custom-log-parser.md)に関するページをご覧ください。
    1. 予想されるログ形式のサンプルとログを比較します。 ログ ファイルの形式がこのサンプルと一致しない場合は、データ ソースを **[その他]** として追加する必要があります。
    1. **[レシーバーの種類]** を、 **[FTP]** 、 **[FTPS]** 、 **[Syslog – UDP]** 、 **[Syslog – TCP]** 、または **[Syslog – TLS]** に設定します。

    > [!NOTE]
    > 多くの場合、セキュリティで保護された転送プロトコル (FTPS、Syslog – TLS) と統合するには、ファイアウォール/プロキシの追加設定が必要です。

    f. ネットワークのトラフィックを検出するために使用できるログの取得先であるファイアウォールおよびプロキシそれぞれに対して、この手順を繰り返します。 ネットワーク デバイスごとに専用のデータ ソースを設定することをお勧めします。これにより、次のことができるようになります。

    * 調査目的で、各デバイスの状態を個別に監視する。
    * 各デバイスが異なるユーザー セグメントで使用されている場合、デバイスごとに Shadow IT Discovery を調べる。

1. 画面上部の **[ログ コレクター]** タブに移動します。

    1. **[ログ コレクターを追加]** をクリックします。
    1. ログ コレクターに **[名前]** を付けます。
    1. Docker の展開に使用するコンピューターの **[ホスト IP アドレス]** を入力します。 ホスト名を解決する DNS サーバー (または同等の機能) がある場合、ホスト IP アドレスをコンピューター名で置換できます。
    1. Select all **Data sources** that you want to connect to the collector, and click **Update** to save the configuration.
    ![ubuntu2](media/ubuntu2.png)

1. 展開の詳細が表示されます。 ダイアログから実行コマンドを**コピー**します。 You can use the copy to clipboard icon, ![copy to clipboard icon](media/copy-icon.png). これは後で必要になります。

1. 予想されるデータ ソース構成を**エクスポート**します。 この構成では、アプライアンスでログのエクスポートを設定する方法を記述します。

    ![ログ コレクターを作成する](media/windows7.png)

    > [!NOTE]
    >
    > * 1 つのログ コレクターで複数のデータ ソースを処理できます。
    > * Cloud App Security と通信するようにログ コレクターを構成するときに情報が必要になるため、画面の内容をコピーします。 Syslog を選択した場合、この情報には、Syslog リスナーがリッスンするポートに関する情報が含まれます。
    > * For users sending log data via FTP for the first time, we recommend changing the password for the FTP user. For more information, see [Changing the FTP password](log-collector-ftp.md#changing-the-ftp-password).

### <a name="step-2--on-premises-deployment-of-your-machine"></a>ステップ 2 – コンピューターのオンプレミスの展開

次の手順は、Windows での展開について説明したものです。 他のプラットフォームの展開手順は若干異なります。

1. 管理者として Windows コンピューターで PowerShell ターミナルを開きます。

1. Run the following command to download the Windows Docker installer PowerShell script file: `Invoke-WebRequest https://adaprodconsole.blob.core.windows.net/public-files/LogCollectorInstaller.ps1 -OutFile (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

    To validate that the installer is signed by Microsoft, see [Validate installer signature](#validate-signature)

1. To enable PowerShell script execution, run `Set-ExecutionPolicy RemoteSigned`

1. Run: `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)` This installs the Docker client on your machine. ログ コレクター コンテナーのインストール中に、コンピューターが 2 回再起動され、もう一度ログインする必要があります。 **Make sure the Docker client is set to use Linux containers.**

1. After each restart, open a PowerShell terminal as an administrator on your machine, re-run: `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

1. インストールが完了する前に、先ほどコピーした実行コマンドを貼り付ける必要があります。

1. コレクターの構成をインポートすることにより、ホスト マシンにコレクター イメージを展開します。 ポータルで生成された実行コマンドをコピーすることで、構成をインポートします。 プロキシを構成する必要がある場合は、プロキシ IP アドレスとポート番号を追加します。 たとえば、プロキシの詳細が 192.168.10.1:8080 の場合は、次のように実行コマンドを更新します。

    ```console
    (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter
    ```

    ![ログ コレクターを作成する](media/windows7.png)

1. 次のコマンドで、コレクターが正しく動作していることを確認します: `docker logs <collector_name>`

"**Finished successfully!** " というメッセージが表示される必要があります。

![ubuntu8](media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>ステップ 3: ネットワーク機器のオンプレミス構成

ネットワーク ファイアウォールとプロキシを、ダイアログの指示に従って FTP ディレクトリの専用 Syslog ポートにログが定期的にエクスポートされるように構成します。 たとえば、次のようになります。

```console
BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\
```

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>ステップ 4 - Cloud App Security ポータルで正常に展開されたことを確認する

**[ログ コレクター]** の表でコレクターの状態をチェックし、状態が **[接続済み]** であることを確認します。 **[作成済み]** の場合は、ログ コレクターの接続と解析が完了していない可能性があります。

![ubuntu9](media/ubuntu9.png)

**ガバナンス ログ**に移動して、ログがポータルに定期的にアップロードされていることを確認することもできます。

展開中に問題が発生した場合は、「[Troubleshooting Cloud Discovery](troubleshooting-cloud-discovery.md)」(Cloud Discovery のトラブルシューティング) を参照してください。

### 省略可能 - カスタムの継続的レポートを作成する<a name="continuous-reports"></a>

ログが Cloud App Security にアップロードされていること、およびレポートが生成されることを確認します。 検証の後、カスタム レポートを作成します。 Azure Active Directory ユーザー グループに基づいて、カスタム検出レポートを作成できます。 たとえば、マーケティング部門のクラウドの使用状況を確認する場合、ユーザー グループのインポート機能を使用してマーケティング グループをインポートします。 次に、このグループに対するカスタム レポートを作成します。 また、IP アドレス タグや IP アドレスの範囲に基づいてレポートをカスタマイズすることもできます。

1. Cloud App Security ポータルの設定歯車アイコンで、Cloud Discovery の設定を選択して、 **[継続的レポート]** を選択します。
1. **[レポートの作成]** ボタンをクリックし、フィールドに入力します。
1. **[フィルター]** では、データ ソース、[インポートされたユーザー グループ](user-groups.md)、または [IP アドレスのタグと範囲](ip-tags.md)を指定してフィルターすることができます。

    ![カスタムの継続的レポート](media/custom-continuous-report.png)

### 省略可能: インストーラーの署名の検証 <a name="validate-signature"></a>

Docker のインストーラーが Microsoft によって署名されていることを確認するには:

1. ファイルを右クリックし、 **[プロパティ]** を選択します。
1. **[デジタル署名]** をクリックして、 **[This digital signature is OK]\(このデジタル署名は問題ありません\)** となっていることを確認します。
1. **[署名者名]** で **Microsoft Corporation** が唯一のエントリであることを確認します。

    ![デジタル署名が有効](media/digital-signature-successful.png)

デジタル署名が有効でない場合は、 **[このデジタル署名は有効ではありません]** と表示されます。

![デジタル署名が無効](media/digital-signature-unsuccessful.png)

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Log collector FTP configuration](log-collector-ftp.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)
