---
title: Cloud App Security が Workday 環境の保護にどのように役立つか
description: この記事では、API コネクタを使用して Cloud App Security に Workday アプリを接続する利点について説明します。これにより、使用状況を表示したり制御したりできます。
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: 9a08b00cabaa7829663d391073a9a4935efdee58
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75190032"
---
# <a name="how-cloud-app-security-helps-protect-your-workday-environment"></a>Cloud App Security が Workday 環境の保護にどのように役立つか

*適用対象: Microsoft Cloud App Security*

主要な HCM ソリューションとして、Workday は従業員の個人データ、契約、ベンダーの詳細など、組織内の最も重要な情報の一部を保持します。 このデータの漏えいを防ぐには、悪意のあるアクターやセキュリティ非対応の insider が機密情報を盗み出すことがないように、継続的な監視を行う必要があります。

Workday を Cloud App Security に接続すると、ユーザーのアクティビティに関する洞察が向上し、異常な動作の脅威の検出を行うことができます。

## <a name="main-threats"></a>主な脅威

- 侵害されたアカウントと内部の脅威
- データ漏えい
- セキュリティ意識の不足
- 管理されていない独自のデバイスの持ち込む (BYOD)

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Cloud App Security が環境の保護にどのように役立つか

- [クラウドの脅威、侵害されたアカウント、悪意のある内部関係者の検出](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [フォレンジック調査のためにアクティビティの監査証跡を使用する](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-workday-with-built-in-policies-and-policy-templates"></a>組み込みのポリシーとポリシーテンプレートを使用して Workday を制御する

次の組み込みポリシーテンプレートを使用して、潜在的な脅威についての検出と通知を行うことができます。

| 種類 | 名前 |
| ---- | ---- |
| アクティビティポリシーテンプレート | Logon from a risky IP address (危険な IP アドレスからのログオン) |

ポリシーの作成の詳細については、「[ポリシーを作成する](control-cloud-apps-with-policies.md#create-a-policy)」を参照してください。

## <a name="automate-governance-controls"></a>ガバナンスコントロールの自動化

現在、Workday で使用できるガバナンスコントロールはありません。 このコネクタにガバナンスアクションを使用することに関心がある場合は、 [Cloud App Security チームのフィードバック](support-and-ts.md#feedback)を、必要なアクションの詳細と共に送信できます。

アプリからの修復脅威の詳細については、「[接続されているアプリの管理](governance-actions.md)」を参照してください。

## <a name="protect-workday-in-real-time"></a>Workday をリアルタイムで保護する

[外部ユーザーとのセキュリティ保護とコラボレーション](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls)に関するベストプラクティスを確認し、[機密データのダウンロードをアンマネージまたは危険なデバイスにブロックして保護](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices)します。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Workday を Microsoft Cloud App Security に接続する方法](connect-workday-to-microsoft-cloud-app-security.md)
