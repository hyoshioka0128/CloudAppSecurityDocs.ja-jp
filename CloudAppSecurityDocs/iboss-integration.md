---
title: Cloud App Security を iboss と統合する
description: この記事では、シームレスな Cloud Discovery と承認されていないアプリの自動ブロックのために Microsoft Cloud App Security と iboss Secure Cloud Gateway を統合する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 2/2/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f60f4ec7dc9ff241cc4d4ba45bca9a50a2e50a00
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74719961"
---
# <a name="integrate-cloud-app-security-with-iboss"></a>Cloud App Security を iboss と統合する

*適用対象: Microsoft Cloud App Security*

Cloud App Security と iboss の両方を使用する場合、2 つの製品を統合することでセキュリティの Cloud Discovery エクスペリエンスを強化することができます。 iboss は、組織のトラフィックを監視し、トランザクションをブロックするポリシーを設定することができる、スタンドアロンのセキュリティで保護されたクラウド ゲートウェイです。 Cloud App Security と iboss を同時に使用することで、次の機能が提供されます。

- Cloud Discovery のシームレスなデプロイ - iboss を使用してトラフィックをプロキシ経由にさせ、Cloud App Security に送信します。 これにより、Cloud Discovery を有効にするためにネットワーク エンドポイントにログ コレクターをインストールする必要がなくなります。
- iboss のブロック機能は、Cloud App Security で "承認されていない" として設定したアプリに自動的に適用されます。
- Cloud App Security の、組織内の上位 100 個のクラウド アプリのリスク評価を使用して、iboss 管理ポータルを強化します。これは、iboss の管理ポータルで直接表示できます。

## <a name="prerequisites"></a>必要条件

- Microsoft Cloud App Security の有効なライセンス
- iboss Secure Cloud Gateway (リリース 9.1.100.0 以降) の有効なライセンス

## <a name="deployment"></a>展開

1. Cloud App Security ポータルで、次の統合の手順を実行します。
    1. 設定の歯車アイコンをクリックして、 **[Cloud Discovery 設定]** を選択します。
    2. **[ログの自動アップロード]** タブを選択した後、 **[データ ソースの追加]** を選択します。
    3. **[データ ソースの追加]** ページで、次の設定を入力します。

        - 名前 = iboss
        - ソース = iboss Secure Cloud Gateway
        - レシーバーの種類 = Syslog - UDP

        ![データ ソース iboss](media/iboss-integration.png)

    4. **[期待されるログ ファイルのサンプルを表示]** をクリックします。 次に **[サンプル ログのダウンロード]** をクリックして、サンプルの検出ログを表示し、自身のログと一致していることを確認します。<br />

1. ネットワーク上で検出されたクラウド アプリを調査します。 詳しい情報と調査手順については、「[Working with Cloud Discovery](working-with-cloud-discovery-data.md)」(Cloud Discovery での作業) をご覧ください。

1. Cloud App Security で承認されていないと設定したすべてのアプリは、10 分ごとに iboss によって ping され、iboss によって自動的にブロックされます。 承認されていないアプリについて詳しくは、「[アプリの承認/非承認](governance-discovery.md#BKMK_SanctionApp)」をご覧ください。

1. Microsoft Cloud App Security にトラフィック ログを送信するように iboss を構成するには、iboss のサポートにお問い合わせください。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
