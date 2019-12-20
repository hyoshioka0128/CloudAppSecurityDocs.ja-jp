---
title: Cloud App Security が Azure 環境の保護にどのように役立つか
description: この記事では、Azure アプリを Cloud App Security に接続する利点について説明します。 API コネクタを使用して、使用状況を表示したり制御したりすることができます。
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: f6638891b8a3dbd75fe103bac7042b572c647e1a
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75190062"
---
# <a name="how-cloud-app-security-helps-protect-your-azure-environment"></a>Cloud App Security が Azure 環境の保護にどのように役立つか

*適用対象: Microsoft Cloud App Security*

Azure は、組織がクラウドでワークロード全体をホストして管理できるようにする IaaS プロバイダーです。 クラウドでインフラストラクチャを活用する利点と共に、組織の最も重要な資産が脅威にさらされる可能性があります。 公開された資産には、機密性の高い情報を持つストレージインスタンス、最も重要なアプリケーション、ポート、および仮想プライベートネットワークの一部を操作するコンピューティングリソースが含まれます。これにより、組織へのアクセスが可能になります。

Azure を Cloud App Security に接続することで、資産をセキュリティで保護し、潜在的な脅威を検出することができます。そのためには、管理およびサインインアクティビティを監視し、考えられるブルートフォース攻撃に関する通知、特権を持つユーザーアカウントの悪意のある使用、および異常な削除を行います。Vm.

## <a name="main-threats"></a>主な脅威

- クラウドリソースの不正悪用
- 侵害されたアカウントと内部の脅威
- データ漏えい
- リソースの構成に誤りがあり、アクセス制御が不十分である

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Cloud App Security が環境の保護にどのように役立つか

- [クラウドの脅威、侵害されたアカウント、悪意のある内部関係者の検出](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [共有データの公開を制限し、コラボレーションポリシーを適用する](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [フォレンジック調査のためにアクティビティの監査証跡を使用する](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-azure-with-built-in-policies-and-policy-templates"></a>組み込みのポリシーとポリシーテンプレートを使用して Azure を制御する

次の組み込みポリシーテンプレートを使用して、潜在的な脅威についての検出と通知を行うことができます。

| 種類 | 名前 |
| ---- | ---- |
| 組み込みの異常検出ポリシー | [匿名 IP アドレスからのアクティビティ](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[頻度の低い国からのアクティビティ](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[不審な IP アドレスからのアクティビティ](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[終了したユーザーによって実行されるアクティビティ](anomaly-detection-policy.md#activity-performed-by-terminated-user)(AAD は IdP として必要)<br />[複数回失敗したログイン試行](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[通常とは異なる管理アクティビティ](anomaly-detection-policy.md#unusual-activities-by-user)<br />[通常とは異なる複数のストレージ削除アクティビティ](anomaly-detection-policy.md#unusual-activities-by-user)(プレビュー)<br />[複数の VM 削除アクティビティ](anomaly-detection-policy.md#multiple-delete-vm-activities)<br />[通常とは異なる複数の VM 作成アクティビティ](anomaly-detection-policy.md#unusual-activities-by-user)(プレビュー) |

ポリシーの作成の詳細については、「[ポリシーを作成する](control-cloud-apps-with-policies.md#create-a-policy)」を参照してください。

## <a name="automate-governance-controls"></a>ガバナンスコントロールの自動化

潜在的な脅威の監視に加えて、検出された脅威を修復するために、次の Azure ガバナンスアクションを適用して自動化することができます。

| 種類 | 操作 |
| ---- | ---- |
| ユーザーガバナンス | -警告をユーザーに通知する (Azure AD 経由)<br />-ユーザーにもう一度サインインするように要求します (Azure AD 経由)<br />-ユーザーの中断 (Azure AD 経由) |

アプリからの修復脅威の詳細については、「[接続されているアプリの管理](governance-actions.md)」を参照してください。

## <a name="protect-azure-in-real-time"></a>Azure をリアルタイムで保護する

[外部ユーザーとのセキュリティ保護とコラボレーション](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls)に関するベストプラクティスを確認し、[機密データのダウンロードをアンマネージまたは危険なデバイスにブロックして保護](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices)します。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Azure を Microsoft Cloud App Security に接続する方法](connect-azure-to-microsoft-cloud-app-security.md)
