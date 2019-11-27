---
title: Azure Advanced Threat Protection を Cloud App Security と統合する
description: この記事では、ハイブリッドリスク検出のために Cloud App Security で Azure Advanced Threat Protection インサイトを活用する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/20/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5636c6a0aa51d17847560a122248e625137840cb
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460932"
---
# <a name="azure-advanced-threat-protection-integration"></a>Azure Advanced Threat Protection の統合

*適用対象: Microsoft Cloud App Security*

Microsoft Cloud App Security は Azure Advanced Threat Protection (Azure ATP) と統合されており、ハイブリッド環境 (クラウドアプリとオンプレミスの両方) でユーザーエンティティ行動分析 (UEBA) を提供します。詳細については、「[チュートリアル: 危険なユーザーの調査](tutorial-ueba.md)」を参照してください。 Azure ATP で提供される機械学習と行動分析の詳細については、「 [Azure ATP とは](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)

## <a name="prerequisites"></a>必須コンポーネント

ハイブリッド環境全体で完全なユーザー調査を実行するためには、次が必要です。

- ご自身の Active Directory インスタンスに接続されている Azure ATP の有効なライセンス
- Azure ATP と Microsoft Cloud App Security 間の統合を有効にするには、グローバル管理者である必要があります
- Azure ATP がない場合は、今すぐ試してみてください

>[!NOTE]
>Microsoft Cloud App Security のサブスクリプションを持っていない場合でも、Cloud App Security ポータルを使用して Azure ATP の洞察を得ることができます。

## <a name="enable-azure-advanced-threat-protection"></a>Azure Advanced Threat Protection を有効にする

Azure ATP との Cloud App Security 統合を有効にするには:

1. Cloud App Security の設定歯車で、 **[設定]** を選択します。

   ![[設定] メニュー](media/azip-system-settings.png)

1. **[脅威保護]** で、 **[Azure ATP]** を選択します。

    ![azure advanced threat protection を有効にする](media/aatp-integration.png)

1. **[アラートとアクティビティを含むデータを Azure ATP を Cloud App Security に接続]** する を選択し、 **[保存]** をクリックします。

> [!NOTE]
> 統合が有効になるまで、最大で12時間かかることがあります。

Azure Advanced Threat Protection 統合を有効にすると、組織内のすべてのユーザーに対してオンプレミスのアクティビティを表示できるようになります。 また、クラウドとオンプレミスの環境でアラートと疑わしいアクティビティを組み合わせることにより、ユーザーに関する高度な洞察も得られます。

## <a name="disable-azure-advanced-threat-protection"></a>Azure Advanced Threat Protection を無効にする

Azure ATP との Cloud App Security 統合を無効にするには:

1. Cloud App Security の設定歯車で、 **[設定]** を選択します。

1. **[脅威保護]** で、 **[Azure ATP]** を選択します。

1. **[アラートとアクティビティを含む Azure ATP データを Cloud App Security に接続]** する をオフにし、 **[保存]** をクリックします。

> [!NOTE]
> 既存の azure ATP データは Cloud App Security 保持ポリシーに従って保持されますが、Id セキュリティの状況評価は削除されます。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
