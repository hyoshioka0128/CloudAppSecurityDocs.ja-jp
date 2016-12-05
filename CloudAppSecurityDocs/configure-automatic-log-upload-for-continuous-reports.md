---
title: "継続的なレポートのために自動ログ アップロードを構成する | Microsoft Docs"
description: "このトピックでは、Cloud Discovery の自動レポートを作成するためにログをアップロードする方法に関する情報を提供します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/08/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c4123272-4111-4445-b6bd-2a1efd3e0c5c
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7901bb58f70949873fb3c423ae7951a67f7cd671
ms.openlocfilehash: 96575cfc6bc3d736b40503049816ccc191fbf3e8


---

# <a name="configure-automatic-log-upload-for-continuous-reports"></a>継続的なレポートのために自動ログ アップロードを構成する
ログ コレクターを使用すると、ネットワークからのログのアップロードを簡単に自動化することができます。 ログ コレクターをネットワーク上で実行すると、Syslog または FTP でログを受け取ります。 各ログは自動的に処理および圧縮されてから、ポータルに送信されます。 FTP ログは、ファイルのログ コレクターへの FTP 転送が完了した後で Cloud App Security にアップロードされ、Syslog については、ログ コレクターは 20 分ごとに受信したログをディスクに書き込んでから、Cloud App Security にファイルをアップロードします。

自動ログ ファイル収集を設定する前に、ログが予期されるログの種類と一致していることを検証し、Cloud App Security で特定のファイルを解析できることを確認します。 

## <a name="technical-requirements"></a>技術要件
- ハイパーバイザー: HyperV または VMware
- ディスク領域: 250 GB
- CPU: 2
- RAM: 4 GB 
- ファイアウォールの設定: 
- ログ コレクターが着信 FTP および Syslog トラフィックを受信できる
- ログ コレクターがポート 443 でポータル (contoso.cloudappsecurity.com など) への発信トラフィックを開始できる

  
## <a name="log-collector-performance"></a>ログ コレクターのパフォーマンス
ログ コレクターは、1 時間あたり最大 50 GB の容量のログを処理できます。
ログ収集プロセスの主なボトルネックは次のとおりです。
- ネットワーク帯域幅 - ネットワーク帯域幅によって、ログのアップロード速度が決まります。
- IT 部門によって割り当てられた仮想マシンの I/O パフォーマンス - ログ コレクターのディスクにログが書き込まれる速度が決まります。
ログ コレクターには、ログの収集速度を監視して、アップロード速度と比較する安全メカニズムが組み込まれています。 輻輳の場合、ログ コレクターは、ログ ファイルの削除を開始します。 全体的に 1 時間あたり 50 GB を超える状況であったら、複数のログ コレクターにトラフィックを分割することをお勧めします。

## <a name="set-up-and-configuration"></a>セットアップと構成  
  
### <a name="step-1-web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>ステップ 1 – Web ポータルの構成: データ ソースを定義し、それをログ コレクターにリンクする  
  
1.  自動アップロードの設定ページに移動します。  
    Cloud App Security ポータルで、設定アイコン ![設定アイコン](./media/settings-icon.png "settings icon") をクリックしてから **[ログ コレクター]** をクリックします。  
  
3.  ログをアップロードするファイアウォールまたはプロキシそれぞれに対応するデータ ソースを作成します。  
  
    」を参照します。  [**データ ソースの追加**] をクリックします。  
  
    b.  プロキシまたはファイアウォールの [**名前**] を付けます。  
  
    c.  [**ソース**] リストからアプライアンスを選択します。  
  
    d.  予想されるログ形式のサンプルとログを比較します。 ログ ファイルの形式がこのサンプルと一致しない場合は、データ ソースを [**その他**] として追加する必要があります。  
  
    e.  [**レシーバーの種類**] を [**FTP**] または [**Syslog**] のいずれかに設定します。  [**Syslog**] の場合、[**UDP**] または [**TCP**] を選択します。  
  
    f.  ネットワークのトラフィックを検出するために使用できるログの取得先であるファイアウォールおよびプロキシそれぞれに対して、この手順を繰り返します。  
  
4.  画面上部の [**ログ コレクター**] タブに移動します。  
  
    」を参照します。  [**ログ コレクターを追加**] をクリックします。  
  
    b.  ログ コレクターに [**名前**] を付けます。  
  
    c.  コレクターに接続するすべての**データ ソース**を選択し、[**更新**] をクリックして構成を保存し、アクセス トークンを生成します。  
![データ ソースの検出](./media/discovery-data-sources.png)
  
  > [!NOTE] 
  > - 1 つのログ コレクターで複数のデータ ソースを処理できます。
  > - Cloud App Security と通信するようにログ コレクターを構成するときに情報が必要になるため、画面の内容をコピーします。 Syslog を選択した場合、この情報には、Syslog リスナーがリッスンするポートに関する情報が含まれます。
4.  Hyper-V または VMWare をクリックして新しいログ コレクター仮想マシンを**ダウンロード**し、ポータルで受け取ったパスワードを使用してファイルを解凍します。  
  
### <a name="step-2-on-premises-deployment-of-the-virtual-machine-and-network-configuration"></a>ステップ 2: 仮想マシンのオンプレミス展開とネットワークの構成   

> [!NOTE] 
> 次の手順は、Hyper-V での展開について説明したものです。 VM のハイパーバイザーを展開する手順は若干異なります。  

1.  Hyper-V マネージャーを開きます。  
  
2.  [**新規**] を選択してから [**仮想マシン**] を選択し、[**次へ**] をクリックします。  
 ![Hyper-V 仮想マシンの検出](./media/discovery-hyperv-virtual-machine.png "discovery hyperv virtual machine")  
  
3.  仮想マシンに、たとえば CloudAppSecurityLogCollector01. という [**名前**] を付けてから [**次へ**] をクリックします。  
  
4.  [**生成 1**] を選択してから [**次へ**] をクリックします。  
  
5.  [**起動メモリ**] を [**4096 MB**] に変更します。  
        
6. この仮想マシンの [**Use Dynamic Memory (動的メモリを使用) **] をオンにしてから、[**次へ**] をクリックします。  
  
7.  可能であれば、ネットワークの [**接続**] を選択してから [**次へ**] をクリックします。  
  
8.  [**Use an existing virtual hard disk (既存の仮想ハード ディスクを使用する)**] を選択し、ダウンロードした Zip ファイルに含まれる .**vhd** ファイルを選択します。  
  
9.  **[次へ]**、**[完了]**の順にクリックします。  
    マシンが Hyper-V 環境に追加されます。  
  
9. [**仮想マシン**] の表でこのマシンをクリックしてから、[**スタート**] をクリックします。   
  
10. ログ コレクター仮想マシンに接続し、DHCP アドレスが割り当てられていることを確認します。その場合、仮想マシンをクリックして **[接続]** を選択します。 ログイン プロンプトが表示されます。 IP アドレスを表示する場合は、ターミナル/SSH ツールを使用して仮想マシンに接続できます。  IP アドレスが表示されない場合は、前のステップでログ コレクターを作成したときにコピーした資格情報を使用し、Hyper-V/VMWare 接続ツールでログインします。 次のコマンドを実行することで、パスワードを変更し、ネットワーク構成ユーティリティを使用して、仮想マシンを構成することができます。
```
sudo network_config
```
> [!NOTE]
> 仮想マシンは、DHCP サーバーから IP アドレスを取得するように事前に構成されています。 静的 IP アドレス、既定のゲートウェイ、ホスト名、DNS サーバーおよび NTPS を構成する必要がある場合は、**network_config** ユーティリティを使用することも、手動で変更することもできます。


この時点で、ログ コレクターはネットワークに接続されているため、Cloud App Security ポータルにアクセスできるようになります。  

### <a name="step-3-on-premises-configuration-of-the-log-collection"></a>ステップ 3: ログ収集のオンプレミス構成 
初めてログ コレクターにログインし、ポータルからログ コレクターの構成をインポートする場合は、次のようにします。 

1.  ポータルで提供された対話型の管理者資格情報を使用して SSH 経由でログ コレクターにログインします。 (コンソールに初めてログインする場合は、パスワードを変更してから再度ログインする必要があります。 ターミナル セッションを使用している場合は、ターミナル セッションの再起動が必要になることがあります。 )
2.  ログ コレクターの作成時に提供されたアクセス トークンを使用して、コレクターの構成ユーティリティを実行します。```sudo collector_config <access token> ```
3. たとえば、次に示すようなコンソールのドメインを入力します。```contoso.portal.cloudappsecurity.com```これは、Cloud App Security ポータルへのログイン後に表示される URL から入手できます。 

4. 構成するログ コレクターの名前を入力します。たとえば、上図の場合、「**CloudAppSecurityLogCollector01**」または「**NewYork**」と入力します。

5.  次のように、ポータルからログ コレクターの構成をインポートします。  
  
      」を参照します。  ポータルで提供された対話型の管理者資格情報を使用して SSH 経由でログ コレクターにログインします。  
  
      b.  次のコマンドで提供されたアクセス トークンを使用して、コレクターの構成ユーティリティを実行します。```sudo collector_config \<access token>```  
     
      c.  たとえば、次に示すようなコンソールのドメインを入力します。``` contoso.portal.cloudappsecurity.com ```
  
      d. たとえば、構成するログ コレクターに次のような名前を入力します。``` CloudAppSecurityLogCollector01  ```

### <a name="step-4---on-premises-configuration-of-your-network-appliances"></a>ステップ 4: ネットワーク機器のオンプレミス構成

ネットワーク ファイアウォールとプロキシを、ダイアログの指示に従って FTP ディレクトリの専用 Syslog ポートにログが定期的にエクスポートされるように構成します。以下に例を示します。  
  
     `London Zscaler - Destination path: 614`  
  
     `SF Blue Coat - Destination path: \\CloudAppSecurityCollector01\BlueCoat\`  
  
### <a name="step-5---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>ステップ 5: Cloud App Security ポータルで正常に展開されたことを確認する

ガバナンス ログに移動して、ログがポータルに定期的にアップロードされていることを確認します。  
  
展開中に問題が発生した場合は、「[クラウド検出のトラブルシューティング](troubleshooting-cloud-discovery.md)」を参照してください。



## <a name="see-also"></a>参照  
[Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
    
      
  


<!--HONumber=Nov16_HO5-->


