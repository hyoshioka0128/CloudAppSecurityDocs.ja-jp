---
title: Cloud App Security AWS | のセキュリティ構成に関する推奨事項を取得するMicrosoft Docs
description: この記事では、アマゾンウェブサービスと統合することによって Cloud App Security のセキュリティ構成の推奨事項を取得する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/1/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fa4fe701de12753d754f0b5dcc9605a1ea4d0ac8
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74721033"
---
# <a name="security-configuration-for-aws"></a>AWS のセキュリティ構成

*適用対象: Microsoft Cloud App Security*

Microsoft Cloud App Security は、アマゾンウェブサービス環境のセキュリティ構成評価を提供します。 この評価では、AWS の Internet Security (CI) のベンチマークに基づいて、基本的なセキュリティの推奨事項を提供します。

## <a name="prerequisites"></a>必要条件

- AWS Security Hub は、すべての AWS アカウントリージョンに対して設定する必要があります。 詳細については、「 [AWS Security Hub](https://go.microsoft.com/fwlink/?linkid=2100208)のセットアップ」を参照してください。
    > [!NOTE]
    > 初めてセキュリティハブを有効にする場合、初期データが使用可能になるまでに数時間かかることがあります。
- アマゾンウェブサービスが Cloud App Security に接続されている必要があります。 詳細については、「 [CONNECT AWS to Microsoft Cloud App Security](connect-aws-to-microsoft-cloud-app-security.md)」を参照してください。

## <a name="how-to-view-aws-security-recommendation"></a>AWS のセキュリティに関する推奨事項を表示する方法

1. Cloud App Security で、を参照して > **セキュリティ構成**を**調査**し、 **[アマゾンウェブサービス]** タブを選択します。
    - Microsoft Cloud App Security が提供するのは、上位 50 個のサブスクリプションに向けた推奨事項のみです。
    - 変更が有効になるまでに、最大 15 分かかる場合があります。

    ![セキュリティ構成メニュー](media/security-configuration-menu.png)

1. 種類、リソース、およびアカウントごとに、推奨事項をフィルター処理できます。 さらに、Azure Security Center でセキュリティ構成のアイコン ![ASC アイコン](media/asc-icon.png) 詳細については、「Amazon Security Hub (推奨事項)」を参照してください。

    ![セキュリティ構成](media/security-configuration-aws.png)

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
