---
title: Azure Advanced Threat Protection を Cloud App Security と統合する
description: この記事では、ハイブリッドリスク検出のために Cloud App Security で Azure Advanced Threat Protection インサイトを活用する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/19/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0605d54b8af24b2b060e96788349e2cfe45abaac
ms.sourcegitcommit: 661228206512c6c8dcb30fdce59b2c038cf2fe69
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2020
ms.locfileid: "78204279"
---
# <a name="azure-advanced-threat-protection-integration"></a>Azure Advanced Threat Protection の統合

*適用対象 Microsoft Cloud App Security:* git Microsoft Cloud App Security を Azure Advanced Threat Protection (Azure ATP) と統合することにより、クラウドアプリとオンプレミスの両方でハイブリッド環境全体にユーザーエンティティ行動分析 (UEBA) を提供します。詳細については、「[チュートリアル: 危険なユーザーの調査](tutorial-ueba.md)」を参照してください。 Azure ATP によって提供される機械学習と行動分析の詳細については、「 [Azure ATP とは](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)」を参照してください。

## <a name="prerequisites"></a>[前提条件]

ハイブリッド環境全体で完全なユーザー調査を実行するためには、次が必要です。

- ご自身の Active Directory インスタンスに接続されている Azure ATP の有効なライセンス
- Azure ATP との統合を有効にするには、Azure Active Directory のグローバル管理者である必要があり Cloud App Security

> [!NOTE]
>
> - Microsoft Cloud App Security のサブスクリプションがない場合でも、Cloud App Security を使用して Azure ATP の洞察を得ることができます。
> - Azure ATP 管理者は、Cloud App Security にアクセスするための新しいアクセス許可が必要になる場合があります。 Cloud App Security に対するアクセス許可を割り当てる方法については、「[管理者アクセスの管理](manage-admins.md)」を参照してください。

## <a name="enable-azure-atp"></a>Azure ATP を有効にする

Azure ATP との Cloud App Security 統合を有効にするには:

1. Cloud App Security の設定歯車で、 **[設定]** を選択します。

    ![[設定] メニュー](media/azip-system-settings.png)

1. **[脅威保護]** で、 **[Azure ATP]** を選択します。

    ![azure advanced threat protection を有効にする](media/aatp-integration.png)

1. **[Azure ATP データ統合を有効にする]** を選択し、 **[保存]** をクリックします。

> [!NOTE]
> 統合が有効になるまで、最大で12時間かかることがあります。

Azure ATP 統合を有効にすると、組織内のすべてのユーザーに対してオンプレミスのアクティビティを表示できるようになります。 また、クラウドとオンプレミスの環境でアラートと疑わしいアクティビティを組み合わせることにより、ユーザーに関する高度な洞察も得られます。 また、[Cloud App Security ポリシー] ページに Azure ATP のポリシーが表示されます。 Azure ATP ポリシーの一覧については、「[セキュリティの警告](https://docs.microsoft.com/azure-advanced-threat-protection/suspicious-activity-guide)」を参照してください。

また、 **Azure ATP 構成**リンクを使用して、Cloud App Security に関連する Azure ATP 設定を構成する必要があります。 これらの設定の詳細については、次の情報を参照してください。

- [Azure ATP センサーの構成](/azure-advanced-threat-protection/install-atp-step5)
- [ディレクトリサービスアカウントの構成](/azure-advanced-threat-protection/install-atp-step2)
- [VPN 用に radius アカウンティングを構成する](/azure-advanced-threat-protection/install-atp-step6-vpn)
- [ヘルスセンターへのアクセス Azure ATP](/azure-advanced-threat-protection/atp-health-center)

## <a name="disable-azure-atp"></a>Azure ATP を無効にする

Azure ATP との Cloud App Security 統合を無効にするには:

1. Cloud App Security の設定歯車で、 **[設定]** を選択します。

1. **[脅威保護]** で、 **[Azure ATP]** を選択します。

1. **[アラートとアクティビティを含む Azure ATP データを Cloud App Security に接続]** する をオフにし、 **[保存]** をクリックします。

> [!NOTE]
> 統合が無効になっている場合、既存の azure ATP データは Cloud App Security 保持ポリシーに従って保持されますが、[Id セキュリティの評価] セクションは削除されます。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
