---
title: Cloud App Security で組織の設定をセットアップする
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
ms.openlocfilehash: 07482404f8c3c374f8ebe8182512add5db64345b
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74719251"
---
# <a name="basic-setup-for-cloud-app-security"></a>Cloud App Security の基本セットアップ

*適用対象: Microsoft Cloud App Security*

ここでは、Microsoft Cloud App Security ポータルをカスタマイズする手順について説明します。

## <a name="prerequisites"></a>必要条件

ポータルにアクセスするには、次の IP アドレスをファイアウォールの許可一覧に追加して、Cloud App Security ポータルにアクセスできるようにする必要があります。

* 104.42.231.28

米国政府の GCC 高のお客様については、次の IP アドレスをファイアウォールの許可一覧に追加して、Cloud App Security GCC High ポータルにアクセスできるようにする必要もあります。

* 52.227.143.223
* 13.72.19.4

> [!NOTE]
> URL および IP アドレスが変更されときに更新されるようにするには、「[Office 365 の URL および IP アドレス範囲](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)」で説明されているように RSS を購読します。

## <a name="set-up-the-portal"></a>ポータルのセットアップ

1. Cloud App Security ポータルのメニューバーで、[設定] 歯車![設定アイコン](media/settings-icon.png "設定アイコン")をクリックし、 **[設定]** を選択して組織の詳細を構成します。

1. **[組織の詳細]** に自社の**組織の表示名**を指定することは重要です。 これは、システムから送信される電子メールや Web ページに表示されます。

1. **環境名** (テナント) を指定します。 この情報は、複数のテナントを管理する場合に特に重要です。

1. システムから送信されるメールや Web ページで表示される**ロゴ**を指定することもできます。 ロゴには、150 x 50 ピクセル以下のサイズで背景が透明色の png ファイルを使用する必要があります。

1. **マネージド ドメイン**のリストを追加します。 マネージド ドメインの追加は非常に重要な手順です。 マネージド ドメインは、Cloud App Security により、内部ユーザーと外部ユーザー、およびファイルの共有の可否を判別する際に使用されます。 この情報は、レポートとアラートに使用されます。

    * 内部として構成されていないドメイン内のユーザーは、外部とマークされます。 外部ユーザーについては、アクティビティまたはファイルはスキャンされません。

1. **[自動サインアウト]** で、セッションが自動的にサインアウトされるまでのセッションの非アクティブ状態を継続する時間を指定します。

1. Azure Information Protection の統合により統合を行う場合は、「[Azure Information Protection の統合](azip-integration.md)」を参照してください。

    * Azure Information Protection の統合を行うには、[Office 365 用アプリ コネクタ](connect-office-365-to-microsoft-cloud-app-security.md)を有効にする必要があります。

1. Azure Advanced Threat Protection 統合と統合する場合は、 [Azure Advanced Threat Protection の統合](azip-integration.md)に関する情報を参照してください。

1. ポータル設定は、この画面からいつでもバックアップできます。 **[ポータル設定をエクスポート]** をクリックすると、ポリシー規則やユーザー グループ、IP アドレス範囲などのポータル設定がすべて記述された json ファイルが作成されます。

> [!NOTE]
> ExpressRoute を使用している場合は、Cloud App Security は Azure に展開され、[ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/) に完全に統合されます。 検出ログのアップロードを含む、Cloud App Security アプリとのすべての通信、および Cloud App Security に送信されるトラフィックは、ExpressRoute の**パブリック ピアリング**経由でルーティングされるため、待機時間、パフォーマンス、およびセキュリティが改善されます。 お客様側で設定を行う必要はありません。
>
> パブリック ピアリングの詳細については、「[ExpressRoute 回線とルーティング ドメイン](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/)」を参照してください。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Cloud Discovery のセットアップ](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
