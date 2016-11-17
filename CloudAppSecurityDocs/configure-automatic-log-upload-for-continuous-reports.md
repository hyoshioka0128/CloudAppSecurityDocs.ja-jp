---
title: "継続的なレポートのために自動ログ アップロードを構成する | Microsoft Docs"
description: "このトピックでは、Cloud Discovery の自動レポートを作成するためにログをアップロードする方法に関する情報を提供します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c4123272-4111-4445-b6bd-2a1efd3e0c5c
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 400741713d40422a3b1c7680663a572d18e9c692
ms.openlocfilehash: 046cc96c15f76e4196c60f9864c835f4e6595dfa


---

# <a name="configure-automatic-log-upload-for-continuous-reports"></a>継続的なレポートのために自動ログ アップロードを構成する
自動ログ ファイル収集を設定する前に、ログが予期されるログの種類と一致していることを検証し、Cloud App Security で特定のファイルを解析できることを確認します。 

## <a name="technical-requirements"></a>技術要件
- ハイパーバイザー: HyperV または VMware
- ディスク領域: 250 GB
- CPU: 2
- RAM: 4 GB 
- ファイアウォールの設定: 
- ログ コレクターが着信 FTP および Syslog トラフィックを受信できる
- ログ コレクターがポート 443 でポータル (contoso.cloudappsecurity.com など) への発信トラフィックを開始できる

  
## <a name="set-up-automatic-log-file-collection"></a>自動ログ ファイル収集の設定  
  
ログ コレクターを使用すると、ネットワークからのログのアップロードを簡単に自動化することができます。 ログ コレクターをネットワーク上で実行すると、Syslog または FTP でログを受け取ります。 各ログは自動的に処理および圧縮されてから、ポータルに送信されます。 FTP ログは、ファイルのログ コレクターへの FTP 転送が完了した後で Cloud App Security にアップロードされ、Syslog については、ログ コレクターは 20 分ごとに受信したログをディスクに書き込んでから、Cloud App Security にファイルをアップロードします。  ログ コレクターの仮想マシンは Hyper-V (VHD 形式) と VMware ハイパーバイザー (OVF 形式) で使用でき、250 GB のディスク領域、2 つの CPU と 4 GB の RAM が必要になります。 
     
ログ コレクター VHD イメージをダウンロードして、Azure サーバーで実行することができます。  
  
2.  自動アップロードの設定ページに移動します。  
    Cloud App Security ポータルで、設定アイコン ![設定アイコン](./media/settings-icon.png "settings icon") をクリックしてから **[Cloud Discovery 設定]** をクリックし、次に **[ログを自動的にアップロード]** タブを選択します。  
  
3.  ログをアップロードするファイアウォールまたはプロキシそれぞれに対応するデータ ソースを作成します。  
  
    1.  [**データ ソースの追加**] をクリックします。  
  
    2.  プロキシまたはファイアウォールの [**名前**] を付けます。  
  
    3.  [**ソース**] リストからアプライアンスを選択します。  
  
    4.  予想されるログ形式のサンプルとログを比較します。 ログ ファイルの形式がこのサンプルと一致しない場合は、データ ソースを [**その他**] として追加する必要があります。  
  
    5.  [**レシーバーの種類**] を [**FTP**] または [**Syslog**] のいずれかに設定します。  
  
          [**Syslog**] の場合、[**UDP**] または [**TCP**] を選択します。  
  
    6.  ネットワークのトラフィックを検出するために使用できるログの取得先であるファイアウォールおよびプロキシそれぞれに対して、この手順を繰り返します。  
  
4.  画面上部の [**ログ コレクター**] タブに移動します。  
  
    1.  [**ログ コレクターを追加**] をクリックします。  
  
    2.  ログ コレクターに [**名前**] を付けます。  
  
    3.  コレクターに接続するすべての [**データ ソース**] を選択してから、[**更新**] をクリックします。  
  
         > [!NOTE] 
       > Cloud App Security と通信するようにログ コレクターを構成するときに情報が必要になるため、画面の内容をコピーします。 Syslog を選択した場合、この情報には、Syslog リスナーがリッスンするポートに関する情報が含まれます。
         
![検出データ ソース](./media/discovery-data-sources.png)
> [!NOTE] 
         > 1 つのログ コレクターで複数のデータ ソースを処理できます。
  
4.  Hyper-V または VMWare をクリックして新しいログ コレクター仮想マシンを**ダウンロード**し、ポータルで受け取ったパスワードを使用してファイルを解凍します。  
  
## <a name="set-up-your-virtual-machine-in-hyperv"></a>Hyper-V で仮想マシンを設定するには、以下のようにします。  
  
1.  Hyper-V マネージャーを開きます。  
  
2.  [**新規**] を選択してから [**仮想マシン**] を選択し、[**次へ**] をクリックします。  
 
![Hyper-V 仮想マシンの検出](./media/discovery-hyperv-virtual-machine.png "discovery hyperv virtual machine")  
  
3.  仮想マシンに、たとえば CloudAppSecurityLogCollector01.という [**名前**] を付けてから [**次へ**] をクリックします。  
  
4.  [**生成 1**] を選択してから [**次へ**] をクリックします。  
  
5.  [**起動メモリ**] を [**4096 MB**] に変更します。  
        
6. この仮想マシンの [**Use Dynamic Memory (動的メモリを使用) **]をオンにしてから、[**次へ**] をクリックします。  
  
7.  可能であれば、ネットワークの [**接続**] を選択してから [**次へ**] をクリックします。  
  
8.  [**Use an existing virtual hard disk (既存の仮想ハード ディスクを使用する)**] を選択し、ダウンロードした Zip ファイルに含まれる .**vhd** ファイルを選択します。  
  
9.  **[次へ]** 、 **[完了]**の順にクリックします。  
    マシンが Hyper-V 環境に追加されます。  
  
9. [**仮想マシン**] の表でこのマシンをクリックしてから、[**スタート**] をクリックします。   
  
10. ログ コレクター仮想マシンに接続し、DHCP アドレスが割り当てられていることを確認します。その場合、仮想マシンをクリックして **[接続]** を選択します。 ログイン プロンプトが表示されます。 IP アドレスを表示する場合は、ターミナル/SSH ツールを使用して仮想マシンに接続できます。  IP アドレスが表示されない場合は、前のステップでログ コレクターを作成したときにコピーした資格情報を使用し、Hyper-V/VMWare 接続ツールでログインします。 パスワードを変更し、次のコマンドを実行して仮想マシンを構成することができます。
```
sudo network_config
```
> [!NOTE]
> 仮想マシンは、DHCP サーバーから IP アドレスを取得するように事前に構成されています。 静的 IP アドレス、既定のゲートウェイ、ホスト名、DNS サーバーおよび NTPS を構成する必要がある場合は、**network_config** ユーティリティを使用することも、手動で変更することもできます。


この時点で、ログ コレクターはネットワークに接続されているため、Cloud App Security ポータルにアクセスできるようになります。  

## <a name="log-in-and-import"></a>ログインとインポート 
初めてログ コレクターにログインし、ポータルからログ コレクターの構成をインポートする場合は、次のようにします。 

1.  ポータルで提供された対話型の管理者資格情報を使用して SSH 経由でログ コレクターにログインします。 (コンソールに初めてログインする場合は、パスワードを変更してから再度ログインする必要があります。 ターミナル セッションを使用している場合は、ターミナル セッションの再起動が必要になることがあります。 )
2.  ログ コレクターの作成時に提供されたアクセス トークンを使用して、コレクターの構成ユーティリティを実行します。 

```
sudo collector_config <access token>
```
3. たとえば、次に示すようなコンソールのドメインを入力します。

```
contoso.portal.cloudappsecurity.com
```

これは、Cloud App Security ポータルへのログイン後に表示される URL から入手できます。 

4. 構成するログ コレクターの名前をを入力します。たとえば、上図の場合、「**CloudAppSecurityLogCollector01**」または「**NewYork**」と入力します。
5.  次のように、ポータルからログ コレクターの構成をインポートします。  
  
      」を参照します。  ポータルで提供された対話型の管理者資格情報を使用して SSH 経由でログ コレクターにログインします。  
  
      b.  取得したアクセス トークンをコマンド **sudo collector_config \<access token>** で使用して、コレクターの構成ユーティリティを実行します。  
  
             Enter your console domain, for example:  
  
             **contoso.portal.cloudappsecurity.com ** 
  
             Enter the name of the log collector you want to configure, for example:  
  
             **CloudAppSecurityLogCollector01**  
  
6.  ネットワーク ファイアウォールとプロキシを、ダイアログの指示に従って FTP ディレクトリの専用 Syslog ポートにログが定期的にエクスポートされるように構成します。以下に例を示します。  
  
     `London Zscaler - Destination path: 614`  
  
     `SF Blue Coat - Destination path: \\CloudAppSecurityCollector01\BlueCoat\`  
  
7.  ガバナンス ログを使用すると、ログがポータルに定期的にアップロードされていることを確認できます。  
  
## <a name="log-collector-performance"></a>ログ コレクターのパフォーマンス
ログ コレクターは、1 時間あたり最大 50 GB の容量のログを処理できます。

ログ収集プロセスの主なボトルネックは次のとおりです。
* ネットワーク帯域幅 - ネットワーク帯域幅によって、ログのアップロード速度が決まります。
* IT 部門によって割り当てられた仮想マシンの I/O パフォーマンス - ログ コレクターのディスクにログが書き込まれる速度が決まります。

ログ コレクターには、ログの収集速度を監視して、アップロード速度と比較する安全メカニズムが組み込まれています。 輻輳の場合、ログ コレクターは、ログ ファイルの削除を開始します。 全体的に 1 時間あたり 50 GB を超える状況であったら、複数のログ コレクターにトラフィックを分割することをお勧めします。

## <a name="see-also"></a>参照  
[Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
    
      
  


<!--HONumber=Oct16_HO5-->


