---
title: Cloud App Security と Azure AD の検出機能の違い
description: この記事では、Cloud App Security と Azure AD の検出機能の違いについて説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/29/2019
ms.topic: overview
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 825a8532588cc479bcc37e5373bff23ccc841d8d
ms.sourcegitcommit: 0b929f7c8feed7dfb40d5294179fd5c6fc079614
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "74461040"
---
# <a name="what-are-the-differences-in-discovery-capabilities-for-azure-active-directory-and-microsoft-cloud-app-security"></a>Azure Active Directory と Microsoft Cloud App Security では、検出機能にどのような違いがありますか。

*適用対象:Microsoft Cloud App Security*

この記事では、Cloud App Security と Azure Active Directory (Azure AD) の検出機能の違いについて説明します。

ライセンスの詳細については、「[Microsoft Cloud App Security ライセンス データシート](https://aka.ms/mcaslicensing)」を参照してください。

## <a name="microsoft-cloud-app-security"></a>Microsoft Cloud App Security

Microsoft Cloud App Security は包括的なクロス SaaS ソリューションであり、深い可視性、強力なデータ制御、強化された脅威保護をクラウド アプリにもたらします。 Cloud Discovery は Cloud App Security の機能の 1 つであり、使用中のクラウド アプリを検出することでシャドウ IT を見えるようにします。

## <a name="enhanced-cloud-app-discovery-in-azure-active-directory"></a>Azure Active Directory の強化された Cloud App Discovery

Azure Active Directory Premium P1 には追加コストなしで [Azure Active Directory Cloud App Discovery](https://aka.ms/caddocsnew) が含まれます。 この機能は、組織のクラウド アプリ使用状況が詳しく見えるようになる Microsoft Cloud App Security Cloud Discovery 機能を基盤にしています。 [Microsoft Cloud App Security にアップグレードする](https://www.microsoft.com/cloud-platform/cloud-app-security)と、Microsoft Cloud App Security の Cloud App Security Broker (CASB) 機能が一式全部与えられます。

### <a name="feature-comparison"></a>機能の比較

次の表は、Microsoft Cloud App Security と Azure AD の検出機能を比較したものです。

|機能|機能|Microsoft Cloud App Security|Azure AD Cloud App Discovery|
|----|----|----|----|
|Cloud Discovery|検出されたアプリ|16,000 超のクラウド アプリ|16,000 超のクラウド アプリ|
||検出分析のためのデプロイ|手動と自動のログ アップロード|手動と自動のログ アップロード|
||ユーザー プライバシーのログ匿名化|はい|はい|
||完全なクラウド アプリ カタログへのアクセス|はい|はい|
||クラウド アプリのリスク評価|はい|はい|
||アプリ、ユーザー、IP アドレス別のクラウド利用状況分析|はい|はい|
||継続的な分析と報告|はい|はい|
||検出されたアプリの異常検出|はい||
|情報の保護|データ損失防止 (DLP) サポート|クロス SaaS DLP とデータ共有制御||
||アプリのアクセス許可とアクセスを取り消す機能|はい||
||ポリシー設定と適用|はい||
||Azure Information Protection との統合 |はい||
||サード パーティ製の DLP ソリューションとの統合|はい||
|脅威検出|異常検出と行動分析|クロス SaaS アプリの場合||
||手動と自動のアラート修復|はい||
||SIEM コネクタ|はい。 クロス SaaS アプリのアラートとアクティビティ ログ。||
||Microsoft インテリジェント セキュリティ グラフへの統合|はい||
||アクティビティ ポリシー|はい||

## <a name="next-steps"></a>次のステップ

基本については、「[Cloud App Security の使用を開始する](getting-started-with-cloud-app-security.md)」をご覧ください。

[!INCLUDE [Open support ticket](includes/support.md)] にする必要があります。
