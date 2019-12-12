---
title: 継続的なレポートのために自動ログ アップロードを構成する - Cloud App Security | Microsoft ドキュメント
description: この記事では、Cloud Discovery の自動レポートを作成するためにログをアップロードする方法に関する情報を提供します。
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
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b718641a17860bf3edb8ffc5f78c07b805b38bab
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74720089"
---
# <a name="configure-automatic-log-upload-for-continuous-reports-on-a-virtual-appliance---deprecated"></a>仮想アプライアンスでの継続的なレポートのために自動ログ アップロードを構成する - 非推奨

*適用対象: Microsoft Cloud App Security*

> [!WARNING]
> 柔軟性の高い展開を実現するために、[Docker](discovery-docker.md) を使用してログのアップロードを構成することをお勧めします。

## <a name="prerequisites"></a>必要条件

- ハイパーバイザー: Hyper-V または VMware
- ディスク領域: 250 GB
- CPU: 2
- RAM: 4 GB
- [ネットワーク要件](network-requirements.md#log-collector)で説明されているとおりにファイアウォールを設定する

## <a name="log-collector-performance"></a>ログ コレクターのパフォーマンス

ログ コレクターは、1 時間あたり最大 50 GB の容量のログを処理できます。
ログ収集プロセスの主なボトルネックは次のとおりです。

- ネットワーク帯域幅 - ネットワーク帯域幅によって、ログのアップロード速度が決まります。
- 仮想マシンの I/O パフォーマンス - ログ コレクターのディスクにログが書き込まれる速度が決まります。
ログ コレクターには、ログの収集速度を監視して、アップロード速度と比較する安全メカニズムが組み込まれています。 輻輳の場合、ログ コレクターは、ログ ファイルの削除を開始します。 全体的に 1 時間あたり 50 GB を超える状況であったら、複数のログ コレクターにトラフィックを分割することをお勧めします。

## <a name="set-up-and-configuration"></a>セットアップと構成

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>ステップ 1: Web ポータルの構成: データ ソースを定義し、それをログ コレクターにリンクする

1. 自動アップロードの設定ページにアクセスします。 Cloud App Security ポータルで、設定アイコン![設定アイコン](media/settings-icon.png "設定アイコン")をクリックし、その後に **[ログコレクター]** をクリックします。

2. ログをアップロードするファイアウォールまたはプロキシそれぞれに対応するデータ ソースを作成します。

   に設定する必要があります。 **[データ ソースの追加]** をクリックします。

   b. プロキシまたはファイアウォールの **[名前]** を付けます。

   c. **[ソース]** リストからアプライアンスを選択します。 一覧に表示されていないネットワーク アプライアンスを使用するために **[カスタム ログ形式]** を選ぶ場合、構成方法の詳細については[カスタム ログ パーサーの使用](custom-log-parser.md)に関するページをご覧ください。

   d. 予想されるログ形式のサンプルとログを比較します。 ログ ファイルの形式がこのサンプルと一致しない場合は、データ ソースを **[その他]** として追加する必要があります。

   e. **[レシーバーの種類]** を **[FTP]** または **[Syslog]** のいずれかに設定します。 **[Syslog]** の場合、 **[UDP]** 、 **[TCP]** 、または **[TLS]** を選択します。

   f. **[追加]** をクリックして、データ ソースを保存します。 ネットワークのトラフィックを検出するために使用できるログの取得先であるファイアウォールおよびプロキシそれぞれに対して、この手順を繰り返します。

3. 画面上部の **[ログ コレクター]** タブに移動します。

    に設定する必要があります。 **[ログ コレクターを追加]** をクリックします。

    b. ログ コレクターに**名前**を付けます。

    c. コレクターに接続するすべての**データ ソース**を選択します。 **[更新]** をクリックして構成を保存し、アクセス トークンを生成します。

    ![検出データ ソース](media/discovery-data-sources.png)

    > [!NOTE]
    > - 1 つのログ コレクターで複数のデータ ソースを処理できます。
    > - Cloud App Security と通信するようログ コレクターを構成するときに情報を使用するため、画面の内容をコピーします。 Syslog を選択した場合、この情報には、Syslog リスナーがリッスンするポートに関する情報が含まれます。
4. [エンド ユーザー ライセンス条項](https://go.microsoft.com/fwlink/?linkid=862492)に同意したら、Hyper-V または VMWare をクリックして、新しいログ コレクター仮想マシンを**ダウンロード**します。 その後、ポータルで受け取ったパスワードを使用して、ファイルを解凍します。

### <a name="step-2--on-premises-deployment-of-the-virtual-machine-and-network-configuration"></a>ステップ 2: 仮想マシンのオンプレミス展開とネットワークの構成

> [!NOTE]
> 次の手順は、Hyper-V での展開について説明したものです。 VM のハイパーバイザーを展開する手順は若干異なります。

1. Hyper-V マネージャーを開きます。

2. **[新規]** を選択してから **[仮想マシン]** を選択し、 **[次へ]** をクリックします。

    ![Hyper-v 仮想マシンの検出](media/discovery-hyperv-virtual-machine.png)

3. 仮想マシンに、たとえば CloudAppSecurityLogCollector01.という **[名前]** を付けてから **[次へ]** をクリックします。

4. **[生成 1]** を選択してから **[次へ]** をクリックします。

5. **[起動メモリ]** を **[4096 MB]** に変更します。

6. この仮想マシンの **[Use Dynamic Memory (動的メモリを使用)]** をオンにしてから、 **[次へ]** をクリックします。

7. 可能であれば、ネットワークの **[接続]** を選択してから **[次へ]** をクリックします。

8. **[Use an existing virtual hard disk]** \(既存の仮想ハード ディスクを使用する\) を選択します。 ダウンロードした ZIP ファイルに含まれる **.vhd** ファイルを選択します。

9. **[次へ]** 、 **[完了]** の順にクリックします。 マシンが Hyper-V 環境に追加されます。

10. **[仮想マシン]** の表でこのマシンをクリックしてから、 **[スタート]** をクリックします。

11. ログ コレクター仮想マシンに接続し、DHCP アドレスが割り当てられていることを確認します。その場合、仮想マシンをクリックして **[接続]** を選択します。 サインイン プロンプトが表示されます。 IP アドレスを表示する場合は、ターミナル/SSH ツールを使用して仮想マシンに接続できます。  IP アドレスが表示されない場合は、ログ コレクターを作成したときにコピーした資格情報を使用し、Hyper-V/VMWare 接続ツールでサインインします。 次のコマンドを実行して、パスワードを変更し、ネットワーク構成ユーティリティを使用して仮想マシンを構成することができます。 `sudo network_config`
    > [!NOTE]
    > 仮想マシンは、DHCP サーバーから IP アドレスを取得するように事前に構成されています。 静的 IP アドレス、既定のゲートウェイ、ホスト名、DNS サーバーおよび NTPS を構成する必要がある場合は、**network_config** ユーティリティを使用することも、手動で変更することもできます。

この時点で、ログ コレクターはネットワークに接続されているため、Cloud App Security ポータルにアクセスできるようになります。

### <a name="step-3--on-premises-configuration-of-the-log-collection"></a>ステップ 3: ログ収集のオンプレミス構成

初めてログ コレクターにサインインし、ポータルからログ コレクターの構成をインポートする場合は、次のようにします。

1. ポータルで提供された対話型の管理者資格情報を使用して SSH 経由でログ コレクターにサインインします。 (コンソールに初めてログインする場合は、パスワードを変更してからもう一度サインインする必要があります。 ターミナル セッションを使用している場合は、ターミナル セッションの再起動が必要になることがあります。 )です。
2. ログ コレクターの作成時に提供されたアクセス トークンを使用して、コレクターの構成ユーティリティを実行します。 `sudo collector_config <access token>`
3. たとえば、`contoso.portal.cloudappsecurity.com` のようなコンソールのドメインを入力します。これは、Cloud App Security ポータルへのログイン後に表示される URL から入手できます。
4. 構成するログ コレクターの名前を入力します。たとえば、上図の場合、「**CloudAppSecurityLogCollector01**」または「**NewYork**」と入力します。
5. 次のように、ポータルからログ コレクターの構成をインポートします。

    に設定する必要があります。 ポータルで提供された対話型の管理者資格情報を使用して SSH 経由でログ コレクターにサインインします。

    b. 次のコマンドで提供されたアクセス トークンを使用して、コレクターの構成ユーティリティを実行します。`sudo collector_config \<access token>`

    c. たとえば、次に示すようなコンソールのドメインを入力します。`contoso.portal.cloudappsecurity.com`

    d. 構成するログコレクターの名前を入力します (例: `CloudAppSecurityLogCollector01`

### <a name="step-4---on-premises-configuration-of-your-network-appliances"></a>ステップ 4: ネットワーク機器のオンプレミス構成

ネットワーク ファイアウォールとプロキシを、ダイアログの指示に従って FTP ディレクトリの専用 Syslog ポートにログが定期的にエクスポートされるように構成します。以下に例を示します。

`London Zscaler - Destination path: 614`

BlueCoat_HQ-宛先パス: \<< machine_name > > \ BlueCoat_HQ \

### <a name="step-5---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>ステップ 5: Cloud App Security ポータルで正常に展開されたことを確認する

**[ログ コレクター]** の表でコレクターの状態をチェックし、状態が **[接続済み]** であることを確認します。 **[作成済み]** の場合、ログ コレクターの接続と解析が完了していない可能性があります。

![ログ コレクターの状態](media/log-collector-status.png)

ガバナンス ログに移動して、ログがポータルに定期的にアップロードされていることを確認します。

展開中に問題が発生した場合は、「[Troubleshooting Cloud Discovery](troubleshooting-cloud-discovery.md)」(Cloud Discovery のトラブルシューティング) を参照してください。

### <a name="optional---create-custom-continuous-reports"></a>省略可能 - カスタムの継続的レポートを作成する

ログが Cloud App Security にアップロードされ、レポートが生成されていることを確認したら、カスタム レポートを作成できます。 Azure Active Directory ユーザー グループに基づいて、カスタム検出レポートを作成できるようになりました。 たとえば、マーケティング部門のクラウドの使用状況を確認したい場合は、ユーザー グループのインポート機能を使用してマーケティング グループをインポートして、このグループにカスタム レポートを作成できます。 また、IP アドレス タグや IP アドレスの範囲に基づいてレポートをカスタマイズすることもできます。

1. Cloud App Security ポータルで設定の歯車アイコンをクリックし、 **[Cloud Discovery settings]\(Cloud Discovery の設定\)** を選択し、 **[継続的レポート]** を選択します。
2. **[レポートの作成]** ボタンをクリックし、フィールドに入力します。
3. **[フィルター]** では、データ ソース、[インポートされたユーザー グループ](user-groups.md)、または [IP アドレスのタグと範囲](ip-tags.md)を指定してフィルターすることができます。

> [!NOTE]
> すべてのカスタム レポートは、圧縮されていないデータで最大 1 GB までに制限されます。 1 GB を超えるデータがある場合は、最初の 1 GB のデータがレポートにエクスポートされます。

![カスタムの継続的レポート](media/custom-continuous-report.png)

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)

[!INCLUDE [Open support ticket](includes/support.md)]
