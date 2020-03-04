---
title: Cloud App Security と Zscaler の統合
description: この記事では、Microsoft Cloud App Security と Zscaler を統合して、シームレスな Cloud Discovery と、承認されていないアプリの自動ブロックを実現する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/03/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: bc418943f4825c7433401f271d710333066039cc
ms.sourcegitcommit: 5a0ea6fe5b90aafadb90da25854dabc4cf05d5fc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2020
ms.locfileid: "78238373"
---
# <a name="integrate-cloud-app-security-with-zscaler"></a>Cloud App Security と Zscaler の統合

*適用対象: Microsoft Cloud App Security*

Cloud App Security と Zscaler の両方を使用する場合は、2つの製品を統合して、セキュリティ Cloud Discovery のエクスペリエンスを向上させることができます。 Zscaler は、スタンドアロンクラウドプロキシとして、組織のトラフィックを監視して、トランザクションをブロックするポリシーを設定できます。 Cloud App Security と Zscaler は、次の機能を備えています。

- Cloud Discovery のシームレスなデプロイ-Zscaler を使用してトラフィックをプロキシし、それを Cloud App Security に送信することで、Cloud Discovery を有効にするために、ネットワークエンドポイントにログコレクターをインストールする必要がなくなります。
- Zscaler のブロック機能は、Cloud App Security で承認されていないものとして設定したアプリに自動的に適用されます。
- Zscaler ポータルで直接表示できる、200をリードするクラウドアプリの Cloud App Security のリスク評価を使用して、Zscaler portal を強化します。

## <a name="prerequisites"></a>前提条件

- Microsoft Cloud App Security 用の有効なライセンス
- Zscaler Cloud 5.6 の有効なライセンス
- アクティブな Zscaler NSS サブスクリプション

## <a name="deployment"></a>展開

1. Zscaler ポータルで、 [Microsoft Cloud App Security との Zscaler パートナー統合](https://help.zscaler.com/zia/configuring-mcas-integration)を完了するための手順を実行します。
2. Cloud App Security portal で、次の統合手順を実行します。
    1. 設定歯車をクリックし、 **[Cloud Discovery の設定]** を選択します。
    2. **[自動ログアップロード]** タブをクリックし、 **[データソースの追加]** をクリックします。
    3. **[データソースの追加]** ページで、次の設定を入力します。

        - 名前 = NSS
        - Source = Zscaler QRadar LEEF
        - レシーバーの種類 = Syslog-UDP

        ![データソース Zscaler](media/data-source-zscaler.png)

        > [!NOTE]
        > データソースの名前が、Cloud App Security NSS フィードの作成時に使用したフィード名と同じであることを確認します。 詳細については、「 [NSS フィード Cloud App Security の追加](https://help.zscaler.com/zia/adding-mcas-nss-feeds)」を参照してください。

    4. [**予想されるログファイルのサンプルを表示**する] をクリックします。 次に、 **[サンプルログのダウンロード]** をクリックしてサンプルの検出ログを表示し、ログが一致していることを確認します。<br />

3. ネットワークで検出されたクラウドアプリを調査します。 詳細および調査手順については、「 [Cloud Discovery の操作](working-with-cloud-discovery-data.md)」を参照してください。

4. Cloud App Security で未承認として設定したアプリは、2時間ごとに Zscaler によって ping され、Zscaler によって自動的にブロックされます。 却下アプリの詳細については、「[承認/却下 an app](governance-discovery.md#BKMK_SanctionApp)」を参照してください。

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
