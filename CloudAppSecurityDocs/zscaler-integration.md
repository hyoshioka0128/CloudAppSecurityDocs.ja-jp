---
title: シームレスなクラウドの検出と承認されたアプリの自動ブロックのために Cloud App Security を Zscaler と統合する | Microsoft Docs
description: シームレスな Cloud Discovery と承認されたアプリの自動ブロックのために Cloud App Security を Zscaler と統合します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/28/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 8abeab8e-3b7a-46a7-bbec-9aaf26f778a8
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: bb408b5422e2b9ed4eb0ab5287a67a929ec680c0
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44142733"
---
*適用対象: Microsoft Cloud App Security*

# <a name="integrate-cloud-app-security-with-zscaler"></a>Cloud App Security を Zscaler と統合する

Cloud App Security と Zscaler の両方を使用する場合、2 つの製品を統合することでセキュリティの Cloud Discovery エクスペリエンスを強化することができます。 Zscaler は、スタンドアロン クラウド プロキシとして、組織のトラフィックを監視します。これによりトランザクションをブロックするためのポリシーの設定が可能になります。 Cloud App Security と Zscaler を同時に使用することで、次の機能が提供されます。

- Cloud Discovery のシームレスな展開 - Zscaler を使用してトラフィックをプロキシし Cloud App Security に送信することで、ネットワーク エンドポイントにログ コレクターをインストールして Cloud Discovery を有効にする必要がなくなります。
- Zscaler のブロック機能は、Cloud App Security で "承認されていない" として設定したアプリに自動的に適用されます。
- Cloud App Security のリスク評価を使用して Zscaler のポータルが強化されます。200 の主要なクラウド アプリに対するリスク評価を、Zscaler のポータルで直接表示できます。
    

## <a name="prerequisites"></a>前提条件

- Microsoft Cloud App Security の有効なライセンス
- Zscaler Cloud 5.6 の有効なライセンス
- Zscaler NSS のアクティブなサブスクリプション 

## <a name="deployment"></a>展開

1. Zscaler のポータルで、[Zscaler パートナーの Microsoft Cloud App Security との統合](https://help.zscaler.com/zia/configuring-mcas-integration)を完了するために必要な手順を実行します。
2. Cloud App Security ポータルで、次の統合の手順を実行します。
    1. 設定の歯車アイコンをクリックして、**[Cloud Discovery 設定]** を選択します。 
    2. **[ログの自動アップロード]** タブをクリックした後、**[データ ソースの追加]** をクリックします。
    3. **[データ ソースの追加]** ページで、次の設定を入力します。
        - 名前 = NSS
        - ソース = Zscaler QRadar LEEF
        - レシーバーの種類 = Syslog - UDP

          ![データ ソースの zscaler](./media/data-source-zscaler.png)

    4. **[期待されるログ ファイルのサンプルを表示]** をクリックします。 次に **[サンプル ログのダウンロード]** をクリックして、サンプルの検出ログを表示し、自身のログと一致していることを確認します。<br>
    
3. ネットワーク上で検出されたクラウド アプリの調査について、さらなる情報と調査手順については、「[Cloud Discovery での作業](working-with-cloud-discovery-data.md)」をご覧ください。
 
4. Cloud App Security で "承認されていない" として設定したすべてのアプリは、2 時間ごとに Zscaler によって ping され、Zscaler によって自動的にブロックされます。 承認されていないアプリについて詳しくは、「[アプリの承認/非承認](governance-discovery.md#govern-discovered-apps)」をご覧ください。
    
    
    
    
    

 
## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  