---
title: Cloud App Security による Okta 環境の保護
description: この記事では、使用の可視性と制御のために、Okta アプリを API コネクタを使用して Cloud App Security に接続する利点について説明します。
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: d62b7d9d91d5f627217caaccbec462aa20d2fcd2
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75190092"
---
# <a name="how-cloud-app-security-helps-protect-your-okta-environment"></a>Cloud App Security による Okta 環境の保護

*適用対象: Microsoft Cloud App Security*

Id およびアクセス管理ソリューションとして、Okta は組織の最上位のビジネスクリティカルなサービスへのキーを保持します。 Okta は、ユーザーと顧客の認証および承認のプロセスを管理します。 悪意のあるアクターや人為的なエラーによって Okta が悪用されると、最も重要な資産やサービスが攻撃を受ける可能性があります。

Okta を Cloud App Security に接続すると、Okta 管理アクティビティ、管理対象ユーザー、および顧客 sigh に関する洞察が改善され、異常な動作の脅威の検出が可能になります。

## <a name="main-threats"></a>主な脅威

- 侵害されたアカウントと内部の脅威

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Cloud App Security が環境の保護にどのように役立つか

- [クラウドの脅威、侵害されたアカウント、悪意のある内部関係者の検出](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [フォレンジック調査のためにアクティビティの監査証跡を使用する](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-okta-with-built-in-policies-and-policy-templates"></a>組み込みのポリシーとポリシーテンプレートを使用した Okta の制御

次の組み込みポリシーテンプレートを使用して、潜在的な脅威についての検出と通知を行うことができます。

| 種類 | 名前 |
| ---- | ---- |
| 組み込みの異常検出ポリシー | [匿名 IP アドレスからのアクティビティ](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[頻度の低い国からのアクティビティ](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[不審な IP アドレスからのアクティビティ](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[あり得ない移動](anomaly-detection-policy.md#impossible-travel)<br />[複数回失敗したログイン試行](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[ランサムウェアの検出](anomaly-detection-policy.md#ransomware-activity)<br />[通常とは異なる管理アクティビティ](anomaly-detection-policy.md#unusual-activities-by-user) |
| アクティビティポリシーテンプレート | Logon from a risky IP address (危険な IP アドレスからのログオン) |

ポリシーの作成の詳細については、「[ポリシーを作成する](control-cloud-apps-with-policies.md#create-a-policy)」を参照してください。

## <a name="automate-governance-controls"></a>ガバナンスコントロールの自動化

現在、Okta に使用できるガバナンスコントロールはありません。 このコネクタにガバナンスアクションを使用することに関心がある場合は、 [Cloud App Security チームのフィードバック](support-and-ts.md#feedback)を、必要なアクションの詳細と共に送信できます。

アプリからの修復脅威の詳細については、「[接続されているアプリの管理](governance-actions.md)」を参照してください。

## <a name="protect-okta-in-real-time"></a>Okta をリアルタイムで保護する

[外部ユーザーとのセキュリティ保護とコラボレーション](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls)に関するベストプラクティスを確認し、[機密データのダウンロードをアンマネージまたは危険なデバイスにブロックして保護](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices)します。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Okta を Microsoft Cloud App Security に接続する方法](connect-okta-to-microsoft-cloud-app-security.md)
