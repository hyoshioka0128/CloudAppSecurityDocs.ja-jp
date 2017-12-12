---
title: "継続的なレポートのために自動ログ アップロードを構成する | Microsoft Docs"
description: "このトピックでは、Azure で Ubuntu の Docker を使って Cloud App Security で継続的なレポートの自動ログ アップロードを構成するプロセスについて説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 29/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 9c51b888-54c0-4132-9c00-a929e42e7792
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ce0a16c3f02c4a39b36766c532ea4e50868c3425
ms.sourcegitcommit: 2e89f41bc2581859a24d55b700dcd89e70e730a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2017
---
# <a name="set-up-and-configuration-on-ubuntu"></a>Ubuntu でのセットアップと構成


## <a name="technical-requirements"></a>技術要件

-   OS: Ubuntu 14.04 以降 (Ubuntu 17.10 をサポートする Docker の安定バージョンはありません)

-   ディスク領域: 250 GB

-   CPU: 2

-   RAM: 4 GB

-   [ネットワーク要件](network-requirements#log-collector)で説明されているとおりにファイアウォールを設定する

## <a name="log-collector-performance"></a>ログ コレクターのパフォーマンス

ログ コレクターは、1 時間あたり最大 50 GB の容量のログを処理できます。 ログ収集プロセスの主なボトルネックは次のとおりです。

-   ネットワーク帯域幅 - ネットワーク帯域幅によって、ログのアップロード速度が決まります。

-   IT 部門によって割り当てられた仮想マシンの I/O パフォーマンス - ログ コレクターのディスクにログが書き込まれる速度が決まります。 ログ コレクターには、ログの収集速度を監視して、アップロード速度と比較する安全メカニズムが組み込まれています。 輻輳の場合、ログ コレクターは、ログ ファイルの削除を開始します。 全体的に 1 時間あたり 50 GB を超える状況であったら、複数のログ コレクターにトラフィックを分割することをお勧めします。

## <a name="set-up-and-configuration"></a>セットアップと構成  

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>ステップ 1: Web ポータルの構成: データ ソースを定義し、それをログ コレクターにリンクする

1.  自動アップロードの設定ページに移動します。  <br></br>Cloud App Security ポータルで、設定アイコン ![設定アイコン](./media/settings-icon.png) をクリックしてから **[ログ コレクター]** をクリックします。

2.  ログをアップロードするファイアウォールまたはプロキシそれぞれに対応するデータ ソースを作成します。

    ![ubuntu1](./media/ubuntu1.png)

    」を参照します。 **[データ ソースの追加]** をクリックします。

    b. プロキシまたはファイアウォールの **[名前]** を付けます。

    c. **[ソース]** リストからアプライアンスを選択します。 一覧に明示されていないネットワーク アプライアンスを処理するために **[カスタム ログ形式]** を選ぶ場合、構成方法の詳細については「[カスタム ログ パーサーの使用](custom-log-parser.md)」を参照してください。

    d. 予想されるログ形式のサンプルとログを比較します。 ログ ファイルの形式がこのサンプルと一致しない場合は、データ ソースを **[その他]** として追加する必要があります。

    e. **[レシーバーの種類]** を、**[FTP]**、**[FTPS]**、**[Syslog – UDP]**、**[Syslog – TCP]**、または **[Syslog – TLS]** に設定します。
    >[!NOTE]
    >多くの場合、セキュリティで保護された転送プロトコル (FTPS、Syslog – TLS) と統合するには、ファイアウォール/プロキシの追加設定が必要です。

    f. ネットワークのトラフィックを検出するために使用できるログの取得先であるファイアウォールおよびプロキシそれぞれに対して、この手順を繰り返します。

3.  画面上部の **[ログ コレクター]** タブに移動します。

    」を参照します。 **[ログ コレクターを追加]** をクリックします。

    b. ログ コレクターに **[名前]** を付けます。

    c. Docker の展開に使うコンピューターの**ホスト IP アドレス**を入力します。

    d. コレクターに接続するすべての**データ ソース**を選び、**[更新]** をクリックして構成を保存します。次の展開手順を参照してください。

    ![ubuntu2](./media/ubuntu2.png)

    >  [!NOTE]
    > - 1 つのログ コレクターで複数のデータ ソースを処理できます。
    >- Cloud App Security と通信するようにログ コレクターを構成するときに情報が必要になるため、画面の内容をコピーします。 Syslog を選択した場合、この情報には、Syslog リスナーがリッスンするポートに関する情報が含まれます。

4.  展開の詳細が表示されます。 ダイアログから実行コマンドを**コピー**します。 クリップボードにコピー アイコン ![クリップボードにコピー アイコン](./media/copy-icon.png) を使えます。

6.  予想されるデータ ソース構成を**エクスポート**します。 この構成では、アプライアンスでログのエクスポートを設定する方法を記述します。

   ![ログ コレクターを作成する](./media/windows7.png)

### <a name="step-2--deployment-of-your-machine-in-azure"></a>ステップ 2 – Azure でのマシンの展開

> [!NOTE]
> 次の手順は、Ubuntu での展開について説明したものです。 他のプラットフォームの展開手順は若干異なります。


1.  Azure 環境内で新しい Ubuntu マシンを作成します。 
2.  マシンが起動したら、次の手順でポートを開きます。
    1.  マシン ビューで、**[ネットワーク]** に移動して、関連するインターフェイスをダブルクリックして選択します。
    2.  **[ネットワーク セキュリティ グループ]** に移動して、関連するネットワーク セキュリティ グループを選択します。
    3.  **[受信セキュリティ規則]** に移動して **[追加]** をクリックします。
      
      ![Ubuntu Azure](./media/ubuntu-azure.png)
    
    4. 次の規則を追加します (**詳細設定**モード)。

    |名前|宛先ポートの範囲|プロトコル|ソース|Destination|
    |----|----|----|----|----|
    |caslogcollector_ftp|21|TCP|<ご使用のアプライアンスの IP アドレスのサブネット>|Any|
    |caslogcollector_ftp_passive|20000-20099|TCP|<ご使用のアプライアンスの IP アドレスのサブネット>|Any|
    |caslogcollector_syslogs_tcp|601-700|TCP|<ご使用のアプライアンスの IP アドレスのサブネット>|Any|
    |caslogcollector_syslogs_udp|514-600|UDP|<ご使用のアプライアンスの IP アドレスのサブネット>|Any|
      
    
      ![Ubuntu Azure の規則](./media/inbound-rule.png)

3.  マシンに戻って、**[接続]** をクリックし、マシン上のターミナルを開きます。

4.  `sudo -i` を使ってルート権限に変更します。

5.  [ソフトウェア ライセンス条項](https://go.microsoft.com/fwlink/?linkid=862492)に同意したら、古いバージョンをアンインストールし、次のコマンドを実行して Docker CE をインストールします。
        
        curl -o /tmp/MCASInstallDocker.sh https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh && chmod +x /tmp/MCASInstallDocker.sh; /tmp/MCASInstallDocker.sh

      ![Ubuntu Azure のコマンド](./media/ubuntu-azure-command.png)

6. Cloud App Security ポータルの **[Create new log collector] \(新しいログ コレクターの作成\)** ウィンドウで、ホスト マシンでコレクター構成をインポートするコマンドをコピーします。

      ![Ubuntu Azure](./media/windows7.png)

7. ログ コレクターを展開するコマンドを実行します。
     
        (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter

     ![Ubuntu プロキシ](./media/ubuntu-proxy.png)

8. コマンド `Docker logs <collector_name>` を実行して、ログ コレクターが正しく動作していることを確認します。 ”**Finished successfully!**” という結果を受け取ります。

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
[Cloud Discovery の Docker の展開に関するトラブルシューティング](troubleshoot-docker.md)
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください](http://support.microsoft.com/oas/default.aspx?prid=16031)  
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます](https://premier.microsoft.com/)

