---
title: Set up your organization's settings in Cloud App Security
description: この記事では、Cloud App Security に組織の情報を入力する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/01/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 2708e8606e1838678e7d2b66fcb4e32584d475fc
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2019
ms.locfileid: "74458755"
---
# <a name="basic-setup-for-cloud-app-security"></a>Cloud App Security の基本セットアップ

*適用対象: Microsoft Cloud App Security*

ここでは、Microsoft Cloud App Security ポータルをカスタマイズする手順について説明します。

## <a name="prerequisites"></a>必要条件

For portal access, it's necessary to add the following IP addresses to your Firewall's allow list to provide access for the Cloud App Security portal:

* 104.42.231.28

For US Government GCC High customers, it's also necessary to add the following IP addresses to your Firewall’s allow list to provide access for the Cloud App Security GCC High portal:

* 52.227.143.223
* 13.72.19.4

> [!NOTE]
> URL および IP アドレスが変更されときに更新されるようにするには、「[Office 365 の URL および IP アドレス範囲](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)」で説明されているように RSS を購読します。

## <a name="set-up-the-portal"></a>ポータルのセットアップ

1. In the Cloud App Security portal, in the menu bar, click the settings cog ![settings icon](./media/settings-icon.png "設定アイコン") and select **Settings** to configure your organization's details.

1. **[組織の詳細]** に自社の**組織の表示名**を指定することは重要です。 これは、システムから送信される電子メールや Web ページに表示されます。

1. **環境名** (テナント) を指定します。 この情報は、複数のテナントを管理する場合に特に重要です。

1. システムから送信されるメールや Web ページで表示される**ロゴ**を指定することもできます。 ロゴには、150 x 50 ピクセル以下のサイズで背景が透明色の png ファイルを使用する必要があります。

1. **マネージド ドメイン**のリストを追加します。 マネージド ドメインの追加は非常に重要な手順です。 マネージド ドメインは、Cloud App Security により、内部ユーザーと外部ユーザー、およびファイルの共有の可否を判別する際に使用されます。 この情報は、レポートとアラートに使用されます。

    * 内部として構成されていないドメイン内のユーザーは、外部とマークされます。 外部ユーザーについては、アクティビティまたはファイルはスキャンされません。

1. Under **Auto sign out**, specify the amount of time a session can remain inactive before the session is automatically signed out.

1. Azure Information Protection の統合により統合を行う場合は、「[Azure Information Protection の統合](azip-integration.md)」を参照してください。

    * Azure Information Protection の統合を行うには、[Office 365 用アプリ コネクタ](connect-office-365-to-microsoft-cloud-app-security.md)を有効にする必要があります。

1. If you're integrating with Azure Advanced Threat Protection integration, see [Azure Advanced Threat Protection Integration](azip-integration.md) for information.

1. ポータル設定は、この画面からいつでもバックアップできます。 **[ポータル設定をエクスポート]** をクリックすると、ポリシー規則やユーザー グループ、IP アドレス範囲などのポータル設定がすべて記述された json ファイルが作成されます。

> [!NOTE]
> ExpressRoute を使用している場合は、Cloud App Security は Azure に展開され、[ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/) に完全に統合されます。 検出ログのアップロードを含む、Cloud App Security アプリとのすべての通信、および Cloud App Security に送信されるトラフィックは、ExpressRoute の**パブリック ピアリング**経由でルーティングされるため、待機時間、パフォーマンス、およびセキュリティが改善されます。 お客様側で設定を行う必要はありません。
>
> パブリック ピアリングの詳細については、「[ExpressRoute 回線とルーティング ドメイン](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/)」を参照してください。

## <a name="next-steps"></a>次のステップ

[Cloud Discovery のセットアップ](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
