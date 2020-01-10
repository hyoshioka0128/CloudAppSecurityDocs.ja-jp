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
ms.openlocfilehash: 9122a5c5cdde5f2a1ed02946970825b75155acc2
ms.sourcegitcommit: fb0d93ca2469a7941a098ae3b5564e7fc327e89f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777120"
---
# <a name="docker-on-windows-on-premises"></a>オンプレミスの Windows の Docker

*適用対象: Microsoft Cloud App Security*

Windows で Docker を使用して Cloud App Security の継続的レポート用に自動ログ アップロードを構成することができます。

## <a name="prerequisites"></a>[前提条件]

* OS: **windows 10** (作成者の更新プログラム)、windows server**バージョン1709以降**(SAC)、または**windows server 2019 (LTSC)**

* ディスク領域: 250 GB

* CPU: 2

* RAM: 4 GB

* [ネットワーク要件](network-requirements.md#log-collector)で説明されているとおりにファイアウォールを設定する

* Hyper-V でオペレーティング システム上の仮想化を有効にすることが必要

> [!IMPORTANT]
> ログを収集するには、ユーザーが Docker 用にサインインしている必要があります。 サインインしなくても、接続を切断するように Docker ユーザーに通知することをお勧めします。

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

    > [!NOTE]
    > 多くの場合、セキュリティで保護された転送プロトコル (FTPS、Syslog – TLS) と統合するには、ファイアウォール/プロキシの追加設定が必要です。

    f. ネットワークのトラフィックを検出するために使用できるログの取得先であるファイアウォールおよびプロキシそれぞれに対して、この手順を繰り返します。 ネットワーク デバイスごとに専用のデータ ソースを設定することをお勧めします。これにより、次のことができるようになります。

    * 調査目的で、各デバイスの状態を個別に監視する。
    * 各デバイスが異なるユーザー セグメントで使用されている場合、デバイスごとに Shadow IT Discovery を調べる。

1. 画面上部の **[ログ コレクター]** タブに移動します。

    1. **[ログ コレクターを追加]** をクリックします。
    1. ログ コレクターに **[名前]** を付けます。
    1. Docker の展開に使用するコンピューターの **[ホスト IP アドレス]** を入力します。 ホスト名を解決する DNS サーバー (または同等の機能) がある場合、ホスト IP アドレスをコンピューター名で置換できます。
    1. コレクターに接続するすべての**データソース**を選択し、 **[更新]** をクリックして構成を保存します。
    ![ubuntu2](media/ubuntu2.png)

1. 展開の詳細が表示されます。 ダイアログから実行コマンドを**コピー**します。 クリップボードにコピーアイコン、![クリップボードにコピー アイコン](media/copy-icon.png)を使用できます。 これは後で必要になります。

1. 予想されるデータ ソース構成を**エクスポート**します。 この構成では、アプライアンスでログのエクスポートを設定する方法を記述します。

    ![ログ コレクターを作成する](media/windows7.png)

    > [!NOTE]
    >
    > * 1 つのログ コレクターで複数のデータ ソースを処理できます。
    > * Cloud App Security と通信するようにログ コレクターを構成するときに情報が必要になるため、画面の内容をコピーします。 Syslog を選択した場合、この情報には、Syslog リスナーがリッスンするポートに関する情報が含まれます。
    > * FTP を使用して初めてログデータを送信するユーザーについては、FTP ユーザーのパスワードを変更することをお勧めします。 詳細については、「 [FTP パスワードの変更](log-collector-ftp.md#changing-the-ftp-password)」を参照してください。

### <a name="step-2--on-premises-deployment-of-your-machine"></a>ステップ 2 – コンピューターのオンプレミスの展開

次の手順は、Windows での展開について説明したものです。 他のプラットフォームの展開手順は若干異なります。

1. 管理者として Windows コンピューターで PowerShell ターミナルを開きます。

1. 次のコマンドを実行して、Windows Docker インストーラーの PowerShell スクリプトファイルをダウンロードします。 `Invoke-WebRequest https://adaprodconsole.blob.core.windows.net/public-files/LogCollectorInstaller.ps1 -OutFile (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

    インストーラーが Microsoft によって署名されていることを確認するには、「[インストーラー署名の検証](#validate-signature)」を参照してください。

1. PowerShell スクリプトの実行を有効にするには、`Set-ExecutionPolicy RemoteSigned` を実行します

1. 実行: `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)` します。これにより、Docker クライアントがコンピューターにインストールされます。 ログ コレクター コンテナーのインストール中に、コンピューターが 2 回再起動され、もう一度ログインする必要があります。 **Docker クライアントが Linux コンテナーを使用するように設定されていることを確認します。**

1. 再起動が完了したら、コンピューターの管理者として PowerShell ターミナルを開き、次のように再実行します。 `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

1. インストールが完了する前に、先ほどコピーした実行コマンドを貼り付ける必要があります。

1. コレクターの構成をインポートすることにより、ホスト マシンにコレクター イメージを展開します。 ポータルで生成された実行コマンドをコピーすることで、構成をインポートします。 プロキシを構成する必要がある場合は、プロキシ IP アドレスとポート番号を追加します。 たとえば、プロキシの詳細が 192.168.10.1:8080 の場合は、次のように実行コマンドを更新します。

    ```console
    (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter
    ```

    ![ログ コレクターを作成する](media/windows7.png)

1. 次のコマンドで、コレクターが正しく動作していることを確認します: `docker logs <collector_name>`

"**Finished successfully!** " というメッセージが表示される必要があります。

![ubuntu8](media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>ステップ 3 - ネットワーク機器のオンプレミス構成

ネットワーク ファイアウォールとプロキシを、ダイアログの指示に従って FTP ディレクトリの専用 Syslog ポートにログが定期的にエクスポートされるように構成します。 たとえば次のようになります。

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

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [ログコレクターの FTP 構成](log-collector-ftp.md)

[!INCLUDE [Open support ticket](includes/support.md)]
