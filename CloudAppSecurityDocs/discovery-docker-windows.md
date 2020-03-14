---
title: Windows 上の Docker を使用して Cloud App Security の継続的レポートをロールアウトする |Microsoft Docs
description: この記事では、オンプレミスサーバーの Windows 上の Docker を使用して Cloud App Security で継続的なレポートの自動ログアップロードを構成するプロセスについて説明します。
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
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285586"
---
# <a name="docker-on-windows-on-premises"></a>オンプレミスの Windows 上の Docker

*適用対象: Microsoft Cloud App Security*

Windows 上の Docker を使用して Cloud App Security で継続的なレポートの自動ログアップロードを構成することができます。

## <a name="prerequisites"></a>前提条件

* OS: **windows 10** (作成者の更新プログラム)、windows server**バージョン1709以降**(SAC)、または**windows server 2019 (LTSC)**

* ディスク領域: 250 GB

* CPU: 2

* RAM: 4 GB

* 「[ネットワーク要件](network-requirements.md#log-collector)」で説明されているように、ファイアウォールを設定します。

* オペレーティングシステムの仮想化を Hyper-v で有効にする必要がある

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

* ネットワーク帯域幅-ネットワーク帯域幅によって、ログのアップロード速度が決まります。

* 仮想マシンの i/o パフォーマンス-ログコレクターのディスクにログが書き込まれる速度を決定します。 ログ コレクターには、ログの収集速度を監視して、アップロード速度と比較する安全メカニズムが組み込まれています。 輻輳の場合、ログ コレクターは、ログ ファイルの削除を開始します。 通常、セットアップが1時間あたり 50 GB を超える場合は、複数のログコレクター間でトラフィックを分割することをお勧めします。

## <a name="set-up-and-configuration"></a>セットアップと構成

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>ステップ 1 – Web ポータルの構成: データ ソースを定義し、それをログ コレクターにリンクする

1. [ログの**自動アップロード**の設定] ページに進んでください。

    1. Cloud App Security ポータルで、設定 アイコンをクリックし、**ログコレクター** をクリックします。

    ![設定アイコン](media/settings-icon.png)

1. ログをアップロードするファイアウォールまたはプロキシごとに、対応するデータソースを作成します。

    1. **[データ ソースの追加]** をクリックします。  
    データソース](media/add-data-source.png) を追加 ![には
    1. プロキシまたはファイアウォールの **[名前]** を付けます。  
    ![ubuntu1](media/ubuntu1.png)
    1. **[ソース]** リストからアプライアンスを選択します。 一覧表示されていないネットワークアプライアンスを操作するために **[カスタムログ形式]** を選択した場合は、「[カスタムログパーサーを使用](custom-log-parser.md)した構成手順」を参照してください。
    1. 予想されるログ形式のサンプルとログを比較します。 ログファイルの形式がこのサンプルと一致しない場合は、データソースを **[その他]** として追加する必要があります。
    1. **[レシーバーの種類]** に **[FTP]** 、 **[FTPS]** 、 **[Syslog – UDP]** 、 **[Syslog – TCP]** 、 **[Syslog – TLS]** のいずれかを設定します。

    > [!NOTE]
    > 多くの場合、セキュリティで保護された転送プロトコル (FTPS および Syslog – TLS) と統合するには、追加の設定またはファイアウォールやプロキシが必要です。

    f. ネットワークのトラフィックを検出するために使用できるログの取得先であるファイアウォールおよびプロキシそれぞれに対して、この手順を繰り返します。 次のことを可能にするために、ネットワークデバイスごとに専用のデータソースを設定することをお勧めします。

    * 調査のために、各デバイスの状態を個別に監視します。
    * 各デバイスが別のユーザーセグメントによって使用されている場合は、デバイスごとに Shadow IT Discovery を探索します。

1. 画面上部の **[ログ コレクター]** タブに移動します。

    1. **[ログ コレクターを追加]** をクリックします。
    1. ログ コレクターに **[名前]** を付けます。
    1. Docker のデプロイに使用するマシンの**ホスト IP アドレス**を入力します。 ホスト名を解決する DNS サーバー (またはそれと同等のもの) がある場合は、ホスト IP アドレスをコンピューター名に置き換えることができます。
    1. コレクターに接続するすべての**データソース**を選択し、 **[更新]** をクリックして構成を保存します。
    ![ubuntu2](media/ubuntu2.png)

1. 詳細な展開情報が表示されます。 ダイアログ ボックスから実行コマンドを**コピー**します。 クリップボードにコピーアイコン、![クリップボードにコピー アイコン](media/copy-icon.png)を使用できます。 これは後で必要になります。

1. 予想されるデータ ソースの構成を**エクスポート**します。 この構成は、アプライアンスでログのエクスポートをどのように設定するかを示しています。

    ![ログコレクターの作成](media/windows7.png)

    > [!NOTE]
    >
    > * 1 つのログ コレクターで複数のデータ ソースを処理できます。
    > * Cloud App Security と通信するようにログ コレクターを構成するときに情報が必要になるため、画面の内容をコピーします。 Syslog を選択した場合、この情報には、Syslog リスナーがリッスンするポートに関する情報が含まれます。
    > * FTP を使用して初めてログデータを送信するユーザーについては、FTP ユーザーのパスワードを変更することをお勧めします。 詳細については、「 [FTP パスワードの変更](log-collector-ftp.md#changing-the-ftp-password)」を参照してください。

### <a name="step-2--on-premises-deployment-of-your-machine"></a>ステップ 2 – マシンのオンプレミス展開

次の手順では、Windows での展開について説明します。 その他のプラットフォームの展開手順は、少し異なります。

1. Windows コンピューターで管理者として PowerShell ターミナルを開きます。

1. 次のコマンドを実行して、Windows Docker インストーラーの PowerShell スクリプトファイルをダウンロードします。 `Invoke-WebRequest https://adaprodconsole.blob.core.windows.net/public-files/LogCollectorInstaller.ps1 -OutFile (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

    インストーラーが Microsoft によって署名されていることを確認するには、「[インストーラー署名の検証](#validate-signature)」を参照してください。

1. PowerShell スクリプトの実行を有効にするには、`Set-ExecutionPolicy RemoteSigned` を実行します

1. 実行: `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)` します。これにより、Docker クライアントがコンピューターにインストールされます。 ログコレクターコンテナーがインストールされている間、コンピューターが2回再起動され、再度ログインする必要があります。 **Docker クライアントが Linux コンテナーを使用するように設定されていることを確認します。**

1. 再起動が完了したら、コンピューターの管理者として PowerShell ターミナルを開き、次のように再実行します。 `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

1. インストールが完了する前に、前の手順でコピーした [実行] コマンドを貼り付ける必要があります。

1. コレクターの構成をインポートして、ホストコンピューターにコレクターイメージをデプロイします。 ポータルで生成された run コマンドをコピーして、構成をインポートします。 プロキシを構成する必要がある場合は、プロキシ IP アドレスとポート番号を追加します。 たとえば、プロキシの詳細が 192.168.10.1:8080 の場合、実行コマンドは次のように更新されます。

    ```console
    (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter
    ```

    ![ログコレクターの作成](media/windows7.png)

1. 次のコマンドを使用して、コレクターが適切に実行されていることを確認します。 `docker logs <collector_name>`

"**正常に完了しました**" のメッセージが表示されます。

![ubuntu8](media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>手順 3-ネットワークアプライアンスのオンプレミス構成

ダイアログの指示に従って、FTP ディレクトリの専用 Syslog ポートにログを定期的にエクスポートするように、ネットワークファイアウォールとプロキシを構成します。 例 :

```console
BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\
```

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>手順 4-Cloud App Security ポータルで正常にデプロイされたことを確認する

**[ログ コレクター]** の表でコレクターの状態をチェックし、状態が **[接続済み]** であることを確認します。 **作成され**ている場合は、ログコレクターの接続と解析が完了していない可能性があります。

![ubuntu9](media/ubuntu9.png)

**[ガバナンス ログ]** に移動して、ログがポータルに定期的にアップロードされていることを確認することもできます。

デプロイ中に問題が発生した場合は、「 [Cloud Discovery のトラブルシューティング](troubleshooting-cloud-discovery.md)」を参照してください。

### 省略可能-カスタムの継続的レポートを作成する<a name="continuous-reports"></a>

ログが Cloud App Security にアップロードされていること、およびそのレポートが生成されていることを確認します。 検証後、カスタムレポートを作成します。 Azure Active Directory ユーザーグループに基づいて、カスタムの探索レポートを作成できます。 たとえば、マーケティング部門のクラウドの使用を確認する場合は、ユーザーグループのインポート機能を使用してマーケティンググループをインポートします。 次に、このグループのカスタムレポートを作成します。 また、IP アドレス タグや IP アドレスの範囲に基づいてレポートをカスタマイズすることもできます。

1. Cloud App Security ポータルの設定歯車で、Cloud Discovery の設定 を選択し、**継続的なレポート** を選択します。
1. **[レポートの作成]** ボタンをクリックし、フィールドに入力します。
1. **[フィルター]** では、データ ソース、[インポートされたユーザー グループ](user-groups.md)、または [IP アドレスのタグと範囲](ip-tags.md)を指定してフィルターすることができます。

    ![カスタムの継続的レポート](media/custom-continuous-report.png)

### 省略可能-インストーラー署名の検証<a name="validate-signature"></a>

Docker インストーラーが Microsoft によって署名されていることを確認するには、次のようにします。

1. ファイルを右クリックし、 **[プロパティ]** を選択します。
1. [**デジタル**署名] をクリックし、**このデジタル署名が OK**であることを確認します。
1. [**署名者名] の**下に、 **[Microsoft Corporation]** が唯一のエントリとして表示されていることを確認します。

    ![有効なデジタル署名](media/digital-signature-successful.png)

デジタル署名が有効でない場合は、次の**デジタル署名が無効**であると考えられます。

![デジタル署名が無効です](media/digital-signature-unsuccessful.png)

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [ログコレクターの FTP 構成](log-collector-ftp.md)

[!INCLUDE [Open support ticket](includes/support.md)]
