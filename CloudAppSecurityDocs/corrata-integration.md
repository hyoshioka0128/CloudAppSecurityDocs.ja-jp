---
title: Cloud App Security と Corrata の統合
description: この記事では、Microsoft Cloud App Security と Corrata を統合して、シームレスな Cloud Discovery と、承認されていないアプリの自動ブロックを実現する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 05/17/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: borisk
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ddffc53b0ccf1b6073ea056b883947805d8ad92c
ms.sourcegitcommit: 27f5fecfb32c28c150d22546bfd3c7f7b9d254e5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/18/2020
ms.locfileid: "83546133"
---
# <a name="integrate-cloud-app-security-with-corrata"></a>Cloud App Security と Corrata の統合

*適用対象:Microsoft Cloud App Security*

Cloud App Security と Corrata の両方を使用する場合は、2つの製品を統合して、モバイルアプリで使用するセキュリティ Cloud Discovery のエクスペリエンスを向上させることができます。 Corrata は、ローカルのモバイルゲートウェイとして、モバイルデバイスからの組織のトラフィックを監視して、トランザクションをブロックするポリシーを設定できるようにします。 Cloud App Security と Corrata は、次の機能を備えています。

- Cloud Discovery のシームレスなデプロイ-Corrata を使用してモバイルデバイスのトラフィックを収集し、それを Cloud App Security に送信します。 これにより、Cloud Discovery を有効にするためにネットワーク エンドポイントにログ コレクターをインストールする必要がなくなります。
- Corrata のブロック機能は、Cloud App Security で承認されていないものとして設定したアプリに自動的に適用されます。
- 最先端のクラウドアプリに対する Cloud App Security のリスク評価を使用して Corrata portal を強化します。これは、Corrata ポータルで直接表示できます。

## <a name="prerequisites"></a>前提条件

- Microsoft Cloud App Security の有効なライセンス
- Corrata Cloud の有効なライセンス

## <a name="deployment"></a>展開

1. Corrata ポータルで、 [Microsoft Cloud App Security との Corrata パートナー統合](https://corrata.com/microsoft-mcas-onboarding)を完了するための手順を実行します。
2. Cloud App Security ポータルで、次の統合の手順を行います。
    1. 設定の歯車アイコンをクリックして、**[Cloud Discovery 設定]** を選択します。
    2. **[ログの自動アップロード]** タブをクリックした後、**[データ ソースの追加]** をクリックします。
    3. **[データ ソースの追加]** ページで、次の設定を入力します。

        - 名前 = Corrata
        - ソース = Corrata
        - 受信者の種類 = FTP

        ![データソース Corrata](media/data-source-corrata.png)

    4. **[期待されるログ ファイルのサンプルを表示]** をクリックします。 次に **[サンプル ログのダウンロード]** をクリックして、サンプルの検出ログを表示し、自身のログと一致していることを確認します。

3. ネットワーク上で検出されたクラウド アプリを調査します。 詳しい情報と調査手順については、「[Working with Cloud Discovery](working-with-cloud-discovery-data.md)」(Cloud Discovery での作業) をご覧ください。

4. Cloud App Security で未承認として設定したアプリは、Corrata によって ping され、Corrata によって自動的にブロックされます。 承認されていないアプリについて詳しくは、「[アプリの承認/非承認](governance-discovery.md#BKMK_SanctionApp)」をご覧ください。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
