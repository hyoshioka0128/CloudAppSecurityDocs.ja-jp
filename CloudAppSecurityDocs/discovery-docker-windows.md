---
title: "Windows の Docker を使用して継続的なレポートのために自動ログ アップロードを構成する | Microsoft Docs"
description: "このトピックでは、Windows の Docker を使って Cloud App Security で継続的なレポートの自動ログ アップロードを構成するプロセスについて説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/6/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 308c06b3-f58b-4a21-86f6-8f87823a893a
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 87bff98075e9ec170442f5611828c79bf7bd43b6
ms.sourcegitcommit: ccee5664f5c49d5bae3748021d5b20dcf637d317
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2017
---
# <a name="set-up-and-configure-the-automatic-log-collector-docker-on-windows-server-2016"></a>Windows Server 2016 で自動ログ コレクター Docker を設定および構成する

> [!NOTE]
> この機能はテナントに段階的にロールアウトされています。 プレビューに参加したい場合は、サポートにお問い合わせください。

## <a name="technical-requirements"></a>技術要件

-   OS: Windows sever 2016 または Windows 10

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

1.  自動アップロードの設定ページに移動します。<br></br> Cloud App Security ポータルで、設定アイコン [設定アイコン](./media/settings-icon.png) をクリックしてから **[ログ コレクター]** をクリックします。

2.  ログをアップロードするファイアウォールまたはプロキシそれぞれに対応するデータ ソースを作成します。

    ![Windows 1](./media/windows1.png)

    」を参照します。 [**データ ソースの追加**] をクリックします。

    b. プロキシまたはファイアウォールの [**名前**] を付けます。

    c. [**ソース**] リストからアプライアンスを選択します。 一覧に明示されていないネットワーク アプライアンスを処理するために **[カスタム ログ形式]** を選ぶ場合、構成方法の詳細については「[カスタム ログ パーサーの使用](custom-log-parser.md)」を参照してください。

    d. 予想されるログ形式のサンプルとログを比較します。 ログ ファイルの形式がこのサンプルと一致しない場合は、データ ソースを [**その他**] として追加する必要があります。

    e. **[レシーバーの種類]** を、**[FTP]**、**[FTPS]**、**[Syslog – UDP]**、**[Syslog – TCP]**、または **[Syslog – TLS]** に設定します。

    > [!NOTE]
    > 多くの場合、セキュリティで保護された転送プロトコル (FTPS、Syslog – TLS) と統合するには、ファイアウォール/プロキシの追加設定が必要です。

    f. ネットワークのトラフィックを検出するために使用できるログの取得先であるファイアウォールおよびプロキシそれぞれに対して、この手順を繰り返します。

3.  画面上部の [**ログ コレクター**] タブに移動します。

    」を参照します。 [**ログ コレクターを追加**] をクリックします。

    b. ログ コレクターに [**名前**] を付けます。

    c. Docker の展開に使うコンピューターの**ホスト IP アドレス**を入力します。

    d. コレクターに接続するすべての**データ ソース**を選び、**[更新]** をクリックして構成を保存します。次の展開手順を参照してください。

    ![Windows 2](./media/windows2.png)

    > [!NOTE]
    > - 1 つのログ コレクターで複数のデータ ソースを処理できます。

    > -   Cloud App Security と通信するようにログ コレクターを構成するときに情報が必要になるため、画面の内容をコピーします。 Syslog を選択した場合、この情報には、Syslog リスナーがリッスンするポートに関する情報が含まれます。

4.  展開の詳細が表示されます。

    ![Windows3](./media/windows3.png)

5.  ダイアログから実行コマンドを**コピー**します。 クリップボードにコピー アイコン [クリップボードにコピー アイコン](./media/copy-icon.png) を使えます。

6.  予想されるデータ ソース構成を**エクスポート**します。 この構成では、アプライアンスでログのエクスポートを設定する方法を記述します。

    ![Windows4](./media/windows4.png)

### <a name="step-2--on-premises-deployment-of-your-machine"></a>ステップ 2 – コンピューターのオンプレミスの展開

>[!NOTE]
>次の手順は、Windows Server での展開について説明したものです。 他のプラットフォームの展開手順は若干異なります。

1.  [最新の安定した Docker for Windows](https://docs.docker.com/docker-for-windows/install/\#download-docker-for-windows) を**ダウンロード**します。
    
2.  InstallDocker.msi インストーラーを**実行**します。

3.  Windows コンピューターで PowerShell ターミナルを開きます。

4.  次のコマンドを使って Docker Hub に**接続**します。`docker login -u caslogcollector`

5.  パスワード `C0llector3nthusiast` を使います。

    ![windows5](./media/windows5.png)

6.  次のコマンドを使って Docker Hub からコレクター イメージを**プル**します。`docker pull microsoft/caslogcollector`

    ![windows6](./media/windows6.png)

7.  ポータルで生成された実行コマンドを使って、コレクター イメージを展開します。

    ![windows8](./media/windows8.png)

    >[!NOTE]
    >プロキシを構成する必要がある場合は、プロキシ IP アドレスとポートを追加します。 たとえば、プロキシの詳細が 192.168.10.1:8080 の場合は、次のように実行コマンドを更新します。  
 `   docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e
    "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e
    "TOKEN=41f8f442c9a30519a058dd3bb9a19c79eb67f34a8816270dc4a384493988863a" -e
    "CONSOLE=tenant2.eu1-rs.adallom.com" -e "COLLECTOR=MyLogCollector" --security-opt
    apparmor:unconfined --cap-add=SYS_ADMIN -dt microsoft/caslogcollector starter`

    ![windows9](./media/windows9.png)

9.  次のコマンドを実行して、コレクターが正しく動作していることを確認します。`docker logs <collector_name>`

"**Finished successfully!**" というメッセージが表示される必要があります。
  ![windows10](./media/windows10.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>ステップ 3: ネットワーク機器のオンプレミス構成

ネットワーク ファイアウォールとプロキシを、ダイアログの指示に従って FTP ディレクトリの専用 Syslog ポートにログが定期的にエクスポートされるように構成します。以下に例を示します。

        BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>ステップ 4 - Cloud App Security ポータルで正常に展開されたことを確認する

**[ログ コレクター]** の表でコレクターの状態をチェックし、状態が **[接続済み]** であることを確認します。 **[作成済み]** の場合、ログ コレクターの接続と解析が完了していない可能性があります。

![windows11](./media/windows11.png)

**ガバナンス ログ**に移動して、ログがポータルに定期的にアップロードされていることを確認することもできます。

展開中に問題が発生した場合は、「[クラウド検出のトラブルシューティング](troubleshooting-cloud-discovery.md)」を参照してください。

## <a name="optional---create-custom-continuous-reports"></a>省略可能 - カスタムの継続的レポートを作成する

ログが Cloud App Security にアップロードされ、レポートが生成されていることを確認したら、カスタム レポートを作成できます。 Azure Active Directory ユーザー グループに基づいて、カスタム検出レポートを作成できるようになりました。 たとえば、マーケティング部門のクラウドの使用状況を確認したい場合は、ユーザー グループのインポート機能を使用してマーケティング グループをインポートして、このグループにカスタム レポートを作成できます。 また、IP アドレス タグや IP アドレスの範囲に基づいてレポートをカスタマイズすることもできます。

1. Cloud App Security ポータルの設定の歯車アイコンをクリックし、**[Cloud Discovery の設定]** を選択し、**[継続的レポートの管理]** を選択します。 
2. **[レポートの作成]** ボタンをクリックし、フィールドに入力します。
3. **[フィルター]** では、データ ソース、[インポートされたユーザー グループ](user-groups.md)、または [IP アドレスのタグと範囲](ip-tags.md)を指定してフィルターすることができます。 

![カスタムの継続的レポート](./media/custom-continuous-report.png)

## <a name="see-also"></a>関連項目
 
[Cloud Discovery のスナップショット レポートを作成する](create-snapshot-cloud-discovery-reports.md)

[継続的なレポートのために自動ログ アップロードを構成する](configure-automatic-log-upload-for-continuous-reports.md)

[Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)

