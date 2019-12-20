---
title: Cloud App Security が Cisco Webex 環境の保護にどのように役立つか
description: この記事では、使用の可視性と制御のために、API コネクタを使用して、Cisco Webex アプリを Cloud App Security に接続する利点について説明します。
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: 5ee11b6c97bc8aa5b0ec35394ac6f1f40bd3873a
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75190212"
---
# <a name="how-cloud-app-security-helps-protect-your-cisco-webex-environment"></a>Cloud App Security が Cisco Webex 環境の保護にどのように役立つか

*適用対象: Microsoft Cloud App Security*

Cisco Webex は、コミュニケーションとコラボレーションのプラットフォームとして、組織全体の円滑なコミュニケーションとコラボレーションを実現します。 データと資産の交換に Cisco Webex を使用すると、従業員との会話に参加している可能性があるチャットルームなどで、機密組織の情報が外部ユーザーに公開される可能性があります。

Cisco Webex を Cloud App Security に接続すると、ユーザーのアクティビティに関する洞察が向上し、情報保護の検出が可能になり、自動化されたガバナンス制御が可能になります。

## <a name="main-threats"></a>主な脅威

- 侵害されたアカウントと内部の脅威
- データ漏えい
- セキュリティ意識の不足
- 攻撃
- 管理されていない独自のデバイスの持ち込む (BYOD)

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Cloud App Security が環境の保護にどのように役立つか

- [クラウドに格納されているデータに DLP ポリシーとコンプライアンスポリシーを適用する](best-practices.md#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [共有データの公開を制限し、コラボレーションポリシーを適用する](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [フォレンジック調査のためにアクティビティの監査証跡を使用する](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-cisco-webex-with-built-in-policies-and-policy-templates"></a>組み込みのポリシーとポリシーテンプレートを使用して Cisco Webex を制御する

次の組み込みポリシーテンプレートを使用して、潜在的な脅威についての検出と通知を行うことができます。

| 種類 | 名前 |
| ---- | ---- |
| 組み込みの異常検出ポリシー | [終了したユーザーによって実行されるアクティビティ](anomaly-detection-policy.md#activity-performed-by-terminated-user)(AAD は IdP として必要)<br />[複数回失敗したログイン試行](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[ランサムウェアの検出](anomaly-detection-policy.md#ransomware-activity)<br />[異常なファイル削除アクティビティ](anomaly-detection-policy.md#unusual-activities-by-user)<br />[通常とは異なるファイル共有アクティビティ](anomaly-detection-policy.md#unusual-activities-by-user)<br />[通常とは異なる複数ファイルのダウンロードアクティビティ](anomaly-detection-policy.md#unusual-activities-by-user) |
| ファイルポリシーテンプレート | 承認されていないドメインで共有されているファイルを検出する<br />個人用電子メールアドレスで共有されるファイルを検出する<br />PII/PCI/PHI を使用したファイルの検出 |
| アクティビティポリシーテンプレート | Mass download by a single user (1 人のユーザーによる大量ダウンロード)<br />ランサムウェア アクティビティの可能性 |

ポリシーの作成の詳細については、「[ポリシーを作成する](control-cloud-apps-with-policies.md#create-a-policy)」を参照してください。

## <a name="automate-governance-controls"></a>ガバナンスコントロールの自動化

潜在的な脅威を監視するだけでなく、次の Cisco Webex ガバナンスアクションを適用して自動化し、検出された脅威を修復することができます。

| 種類 | 操作 |
| ---- | ---- |
| ユーザーガバナンス | -警告をユーザーに通知する (Azure AD 経由)<br />-ユーザーにもう一度サインインするように要求します (Azure AD 経由)<br />-ユーザーの中断 (Azure AD 経由) |
| データガバナンス | -ごみ箱ファイル |

アプリからの修復脅威の詳細については、「[接続されているアプリの管理](governance-actions.md)」を参照してください。

## <a name="protect-cisco-webex-in-real-time"></a>Cisco Webex をリアルタイムで保護する

[外部ユーザーとのセキュリティ保護とコラボレーション](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls)に関するベストプラクティスを確認し、[機密データのダウンロードをアンマネージまたは危険なデバイスにブロックして保護](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices)します。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Cisco Webex を Microsoft Cloud App Security に接続する方法](connect-webex-to-microsoft-cloud-app-security.md)
