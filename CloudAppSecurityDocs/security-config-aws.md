---
title: Cloud App Security AWS | のセキュリティ構成に関する推奨事項を取得するMicrosoft Docs
description: この記事では、アマゾンウェブサービスと統合することによって Cloud App Security のセキュリティ構成の推奨事項を取得する方法について説明します。
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 8/1/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c6d8f8af-867b-43ab-adee-f06520577fe7
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5464ad83485068d41e6930c31b057d2530622d85
ms.sourcegitcommit: 3fe4489cbb2c7d7e8f26aa358511e9f738596e98
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2019
ms.locfileid: "69013252"
---
# <a name="security-configuration-for-aws"></a>AWS のセキュリティ構成

*適用対象:Microsoft Cloud App Security*

Microsoft Cloud App Security は、アマゾンウェブサービス環境のセキュリティ構成評価を提供します。 この評価では、AWS の Internet Security (CI) のベンチマークに基づいて、基本的なセキュリティの推奨事項を提供します。

## <a name="prerequisites"></a>必須コンポーネント

- AWS Security Hub は、すべての AWS アカウントリージョンに対して設定する必要があります。 詳細については、「 [AWS Security Hub](https://go.microsoft.com/fwlink/?linkid=2100208)のセットアップ」を参照してください。
    > [!NOTE]
    > 初めてセキュリティハブを有効にする場合、初期データが使用可能になるまでに数時間かかることがあります。
- アマゾンウェブサービスが Cloud App Security に接続されている必要があります。 詳細については、「 [CONNECT AWS to Microsoft Cloud App Security](connect-aws-to-microsoft-cloud-app-security.md)」を参照してください。

## <a name="how-to-view-aws-security-recommendation"></a>AWS のセキュリティに関する推奨事項を表示する方法

1. Cloud App Security で、[**セキュリティ構成**の**調査** > ] を参照し、 **[アマゾンウェブサービス]** タブを選択します。
    - Microsoft Cloud App Security が提供するのは、上位 50 個のサブスクリプションに向けた推奨事項のみです。
    - 変更が有効になるまでに、最大 15 分かかる場合があります。

     ![セキュリティ構成メニュー](media/security-configuration-menu.png)

1. 種類、リソース、およびアカウントごとに、推奨事項をフィルター処理できます。 さらに、Azure Security Center でセキュリティ構成のアイコン ![ASC アイコン](./media/asc-icon.png) 詳細については、「Amazon Security Hub (推奨事項)」を参照してください。

   ![セキュリティ構成](media/security-configuration-aws.png)

## <a name="next-steps"></a>次の手順 
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
