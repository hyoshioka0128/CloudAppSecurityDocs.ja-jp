---
title: Azure Active Directory Identity Protection を Cloud App Security と統合する
description: この記事では、ハイブリッドリスク検出のために Cloud App Security で Id 保護アラートを活用する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/24/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f5603102aa393c676b82fc179094526933e93f68
ms.sourcegitcommit: 2cf3c78a1b45a5b6ca534fdd12fd97afc51726e3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2020
ms.locfileid: "80295783"
---
# <a name="azure-active-directory-identity-protection-integration"></a>Azure Active Directory Identity Protection の統合

*適用対象: Microsoft Cloud App Security*

Microsoft Cloud App Security は Azure Active Directory Identity Protection (Identity Protection) と統合され、ハイブリッド環境全体でユーザーエンティティ行動分析 (UEBA) を提供します。 Identity Protection によって提供される機械学習と行動分析の詳細については、「 [Identity protection とは](/azure/active-directory/identity-protection/overview-identity-protection)」を参照してください。

## <a name="prerequisites"></a>前提条件

- Id 保護と Cloud App Security 間の統合を可能にする Cloud App Security 管理者アカウント。

## <a name="enable-identity-protection"></a>Id 保護を有効にする

> [!NOTE]
> Id 保護機能は、既定で有効になっています。 ただし、機能が無効になっている場合は、次の手順を使用して有効にすることができます。

Identity Protection との Cloud App Security 統合を有効にするには:

1. Cloud App Security の設定歯車で、 **[設定]** を選択します。

    ![[設定] メニュー](media/azip-system-settings.png)

1. **[脅威保護]** で、 **[Azure AD Identity Protection]** を選択します。

    ![azure advanced threat protection を有効にする](media/aadip-integration.png)

1. **[Azure AD Identity Protection アラートの統合を有効にする]** を選択し、 **[保存]** をクリックします。

Identity Protection の統合を有効にすると、組織内のすべてのユーザーのアラートを表示できるようになります。

## <a name="disable-identity-protection"></a>Id 保護を無効にする

Identity Protection との Cloud App Security 統合を無効にするには:

1. Cloud App Security の設定歯車で、 **[設定]** を選択します。

1. **[脅威保護]** で、 **[Azure AD Identity Protection]** を選択します。

1. **[Azure AD Identity Protection アラートの統合を有効にする]** をオフにし、 **[保存]** をクリックします。

> [!NOTE]
> 統合を無効にすると、既存の Id 保護アラートは Cloud App Security 保持ポリシーに従って保持されます。

## <a name="configure-identity-protection-policies"></a>Id 保護ポリシーを構成する

Id 保護ポリシーは、重大度スライダーを使用して組織のニーズに合わせて微調整することができます。 感度のスライダーを使用すると、どのアラートを取り込まれたするかを制御できます。 このようにして、カバレッジのニーズと (SNR) ターゲットに応じて検出を調整できます。

次のポリシーを使用できます。

|ポリシー|説明|既定の状態|既定の重要度|
|---|---|---|---|
|漏洩した資格情報|漏洩した資格情報アラートを表示します。ユーザーの有効な資格情報が漏洩しています|有効|低-すべてのアラートを受信する|
|リスクの高いサインイン|複数の危険なサインインの検出、ユーザーによって実行されなかったサインインを集計します|有効|高-重要度の高いアラートのみを受信する|

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
