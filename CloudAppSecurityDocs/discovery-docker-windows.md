---
title: Windows の Docker を使用して Cloud App Security の継続的レポートをロールアウトする | Microsoft Docs
description: この記事では、オンプレミス サーバーの Windows で Docker を使用して、Cloud App Security で継続的レポートの自動ログ アップロードを構成するプロセスについて説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/16/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: ff73a393-da43-4954-8b02-38d2a48d39b3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 37eed2eb11dfd3f77a1cf26281af6d867c9e9c4d
ms.sourcegitcommit: 9f322632666636de12ac332349130d7961dbbb81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2019
ms.locfileid: "54059466"
---
# <a name="docker-on-windows-on-premises"></a>オンプレミスの Windows の Docker

*適用対象:Microsoft Cloud App Security*

Windows で Docker を使用して Cloud App Security の継続的レポート用に自動ログ アップロードを構成することができます。

## <a name="technical-requirements"></a>技術要件

- OS:Windows 10 (Fall Creators Update) および Windows Server バージョン 1709 以降 

- ディスク領域:250 GB

- CPU:2 で保護されたプロセスとして起動されました

- RAM:4 GB

- [ネットワーク要件](network-requirements.md#log-collector)で説明されているとおりにファイアウォールを設定する

## <a name="log-collector-performance"></a>ログ コレクターのパフォーマンス

ログ コレクターは、1 時間あたり最大 50 GB の容量のログを処理できます。 ログ収集プロセスの主なボトルネックは次のとおりです。

- ネットワーク帯域幅 - ネットワーク帯域幅によって、ログのアップロード速度が決まります。

- 仮想マシンの I/O パフォーマンス - ログ コレクターのディスクにログが書き込まれる速度が決まります。 ログ コレクターには、ログの収集速度を監視して、アップロード速度と比較する安全メカニズムが組み込まれています。 輻輳の場合、ログ コレクターは、ログ ファイルの削除を開始します。 1 時間あたり 50 GB を超えるのが普通である場合は、複数のログ コレクターにトラフィックを分割することをお勧めします。

## <a name="set-up-and-configuration"></a>セットアップと構成  

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>ステップ 1: Web ポータルの構成: データ ソースを定義し、それをログ コレクターにリンクする

1. **[自動ログ アップロード]** 設定ページに移動します。 

     」を参照します。 Cloud App Security ポータルで、設定アイコンをクリックした後、**[ログ コレクター]** をクリックします。

      ![設定アイコン](./media/settings-icon.png)

2. ログをアップロードするファイアウォールまたはプロキシそれぞれに対応するデータ ソースを作成します。

     」を参照します。 **[データ ソースの追加]** をクリックします。

      ![データ ソースを追加する](./media/add-data-source.png)
          
     b. プロキシまたはファイアウォールの **[名前]** を付けます。
      
      ![ubuntu1](./media/ubuntu1.png)

     c. **[ソース]** リストからアプライアンスを選択します。 一覧に表示されていないネットワーク アプライアンスを使用するために **[カスタム ログ形式]** を選ぶ場合、構成方法の詳細については[カスタム ログ パーサーの使用](custom-log-parser.md)に関するページをご覧ください。

     d. 予想されるログ形式のサンプルとログを比較します。 ログ ファイルの形式がこのサンプルと一致しない場合は、データ ソースを **[その他]** として追加する必要があります。

     e. **[レシーバーの種類]** を、**[FTP]**、**[FTPS]**、**[Syslog – UDP]**、**[Syslog – TCP]**、または **[Syslog – TLS]** に設定します。
     
     >[!NOTE]
     >多くの場合、セキュリティで保護された転送プロトコル (FTPS、Syslog – TLS) と統合するには、ファイアウォール/プロキシの追加設定が必要です。

      f. ネットワークのトラフィックを検出するために使用できるログの取得先であるファイアウォールおよびプロキシそれぞれに対して、この手順を繰り返します。 ネットワーク デバイスごとに専用のデータ ソースを設定することをお勧めします。これにより、次のことができるようになります。
     - 調査目的で、各デバイスの状態を個別に監視する。
     - 各デバイスが異なるユーザー セグメントで使用されている場合、デバイスごとに Shadow IT Discovery を調べる。

3. 画面上部の **[ログ コレクター]** タブに移動します。

   」を参照します。 **[ログ コレクターを追加]** をクリックします。

   b. ログ コレクターに **[名前]** を付けます。

   c. Docker の展開に使用するコンピューターの **[ホスト IP アドレス]** を入力します。 ホスト名を解決する DNS サーバー (または同等の機能) がある場合、ホスト IP アドレスをコンピューター名で置換できます。

   d. コレクターに接続するすべての**データ ソース**を選び、**[更新]** をクリックして構成を保存します。次の展開手順を参照してください。

   ![ubuntu2](./media/ubuntu2.png)

   > [!NOTE]
   > - 1 つのログ コレクターで複数のデータ ソースを処理できます。
   > - Cloud App Security と通信するようにログ コレクターを構成するときに情報が必要になるため、画面の内容をコピーします。 Syslog を選択した場合、この情報には、Syslog リスナーがリッスンするポートに関する情報が含まれます。

4. 展開の詳細が表示されます。 ダイアログから実行コマンドを**コピー**します。 [クリップボードにコピー] アイコンを使用できます。 ![クリップボードにコピー アイコン](./media/copy-icon.png)。 これは後で必要になります。

5. 予想されるデータ ソース構成を**エクスポート**します。 この構成では、アプライアンスでログのエクスポートを設定する方法を記述します。

   ![ログ コレクターを作成する](./media/windows7.png)

### <a name="step-2--on-premises-deployment-of-your-machine"></a>ステップ 2 – コンピューターのオンプレミスの展開
次の手順は、Windows での展開について説明したものです。 他のプラットフォームの展開手順は若干異なります。

1. 管理者として Windows コンピューターで PowerShell ターミナルを開きます。

2. Windows Docker インストーラーをダウンロードするには、次のコマンドを使用します。<br>
 `Invoke-WebRequest https://adaprodconsole.blob.core.windows.net/public-files/LogCollectorInstaller.ps1 -OutFile (Join-Path $Env:Temp LogCollectorInstaller.ps1)`
<br>インストーラーが Microsoft によって署名されていることを検証する場合は、[インストーラーの署名の検証](#validate-signature)に関するページを参照してください。

3. PowerShell スクリプトの実行を有効にするには、`Set-ExecutionPolicy RemoteSigned` を実行します。

4. 実行: `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)`<br>
これにより、Docker クライアントがご使用のコンピューターにインストールされます。 ログ コレクター コンテナーのインストール中に、コンピューターが 2 回再起動され、もう一度ログインする必要があります。

5. 再起動のたびに、インストーラーを保存したディレクトリから、次を再実行します: `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)`<br>  

6. インストールが完了する前に、先ほどコピーした実行コマンドを貼り付ける必要があります。

7. コレクターの構成をインポートすることにより、ホスト マシンにコレクター イメージを展開します。 ポータルで生成された実行コマンドをコピーすることで、構成をインポートします。 プロキシを構成する必要がある場合は、プロキシ IP アドレスとポート番号を追加します。 たとえば、プロキシの詳細が 192.168.10.1:8080 の場合は、次のように実行コマンドを更新します。

           (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter

   ![ログ コレクターを作成する](./media/windows7.png)
8. 次のコマンドで、コレクターが正しく動作していることを確認します: `docker logs <collector_name>`

次のメッセージが表示されるはずです: **"Finished successfully!" (正常に終了しました)**

  ![ubuntu8](./media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>ステップ 3 - ネットワーク機器のオンプレミス構成

ネットワーク ファイアウォールとプロキシを、ダイアログの指示に従って FTP ディレクトリの専用 Syslog ポートにログが定期的にエクスポートされるように構成します。 たとえば、次のように入力します。

    BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>ステップ 4 - Cloud App Security ポータルで正常に展開されたことを確認する

 **[ログ コレクター]** の表でコレクターの状態を確認し、状態が **[接続済み]** であることを確認します。  **[作成済み]** の場合は、ログ コレクターの接続と解析が完了していない可能性があります。

 ![ubuntu9](./media/ubuntu9.png)

**ガバナンス ログ**に移動して、ログがポータルに定期的にアップロードされていることを確認することもできます。

展開中に問題が発生した場合は、「 [クラウド検出のトラブル シューティング](troubleshooting-cloud-discovery.md)」をご覧ください。

### 省略可能 - カスタムの継続的レポートを作成する<a name="continuous-reports"></a>

ログが Cloud App Security にアップロードされていること、およびレポートが生成されることを確認します。 検証の後、カスタム レポートを作成します。 Azure Active Directory ユーザー グループに基づいて、カスタム検出レポートを作成できます。 たとえば、マーケティング部門のクラウドの使用状況を確認する場合、ユーザー グループのインポート機能を使用してマーケティング グループをインポートします。 次に、このグループに対するカスタム レポートを作成します。 また、IP アドレス タグや IP アドレスの範囲に基づいてレポートをカスタマイズすることもできます。

1. Cloud App Security ポータルの設定歯車アイコンで、Cloud Discovery の設定を選択して、**[継続的レポート]** を選択します。 
2. **[レポートの作成]** ボタンをクリックし、フィールドに入力します。
3. **[フィルター]** では、データ ソース、[インポートされたユーザー グループ](user-groups.md)、または [IP アドレスのタグと範囲](ip-tags.md)を指定してフィルターすることができます。 

![カスタムの継続的レポート](./media/custom-continuous-report.png)

### 省略可能: インストーラーの署名の検証 <a name="validate-signature"></a>

Docker のインストーラーが Microsoft によって署名されていることを確認するには:
1. ファイルを右クリックし、**[プロパティ]** を選択します。
2. **[デジタル署名]** をクリックして、**[This digital signature is OK]\(このデジタル署名は問題ありません\)** となっていることを確認します。  
3. **[署名者名]** で **Microsoft Corporation** が唯一のエントリであることを確認します。  

![デジタル署名が有効](./media/digital-signature-successful.png)

デジタル署名が有効でない場合は、**[このデジタル署名は有効ではありません]** と表示されます。

![デジタル署名が無効](./media/digital-signature-unsuccessful.png)

## <a name="next-steps"></a>次の手順

[Cloud Discovery の Docker の展開に関するトラブルシューティング](troubleshoot-docker.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)

