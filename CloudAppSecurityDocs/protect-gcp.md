---
title: Cloud App Security によって Google Cloud Platform 環境を保護する方法
description: この記事では、API コネクタを使用して Cloud App Security に Google Cloud Platform アプリを接続して、使用状況を表示および制御する利点について説明します。
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: de9a6d460725766dee348fdd91f8c12a9bfe5745
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75190082"
---
# <a name="how-cloud-app-security-helps-protect-your-google-cloud-platform-gcp-environment"></a>Cloud App Security が Google Cloud Platform (GCP) 環境を保護する方法

*適用対象: Microsoft Cloud App Security*

Google Cloud Platform は、組織がクラウドでワークロード全体をホストして管理できるようにする IaaS プロバイダーです。 クラウドでインフラストラクチャを活用する利点と共に、組織の最も重要な資産が脅威にさらされる可能性があります。 公開された資産には、機密性の高い情報を持つストレージインスタンス、最も重要なアプリケーション、ポート、および仮想プライベートネットワークの一部を操作するコンピューティングリソースが含まれます。これにより、組織へのアクセスが可能になります。

GCP を Cloud App Security に接続することによって、資産をセキュリティで保護し、潜在的な脅威を検出することができます。そのためには、管理およびサインインアクティビティを監視し、考えられるブルートフォース攻撃に関する通知、特権ユーザーアカウントの悪意のある使用、および異常な削除を行います。Vm.

## <a name="main-threats"></a>主な脅威

- クラウドリソースの不正悪用
- 侵害されたアカウントと内部の脅威
- データ漏えい
- リソースの構成に誤りがあり、アクセス制御が不十分である

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Cloud App Security が環境の保護にどのように役立つか

- [クラウドの脅威、侵害されたアカウント、悪意のある内部関係者の検出](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [フォレンジック調査のためにアクティビティの監査証跡を使用する](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-gcp-with-built-in-policies-and-policy-templates"></a>組み込みのポリシーとポリシーテンプレートを使用した GCP の制御

次の組み込みポリシーテンプレートを使用して、潜在的な脅威についての検出と通知を行うことができます。

| 種類 | 名前 |
| ---- | ---- |
| 組み込みの異常検出ポリシー | [匿名 IP アドレスからのアクティビティ](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[頻度の低い国からのアクティビティ](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[不審な IP アドレスからのアクティビティ](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[あり得ない移動](anomaly-detection-policy.md#impossible-travel)<br />[終了したユーザーによって実行されるアクティビティ](anomaly-detection-policy.md#activity-performed-by-terminated-user)(AAD は IdP として必要)<br />[複数回失敗したログイン試行](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[通常とは異なる管理アクティビティ](anomaly-detection-policy.md#unusual-activities-by-user)<br />[複数の VM 削除アクティビティ](anomaly-detection-policy.md#multiple-delete-vm-activities)<br />[通常とは異なる複数の VM 作成アクティビティ](anomaly-detection-policy.md#unusual-activities-by-user)(プレビュー) |
| アクティビティポリシーテンプレート | コンピューティングエンジンリソースへの変更<br />StackDriver の構成に対する変更<br />ストレージリソースへの変更<br />仮想プライベートネットワークの変更<br />Logon from a risky IP address (危険な IP アドレスからのログオン) |

ポリシーの作成の詳細については、「[ポリシーを作成する](control-cloud-apps-with-policies.md#create-a-policy)」を参照してください。

## <a name="automate-governance-controls"></a>ガバナンスコントロールの自動化

潜在的な脅威を監視するだけでなく、次の GCP ガバナンスアクションを適用して自動化し、検出された脅威を修復することができます。

| 種類 | 操作 |
| ---- | ---- |
| ユーザーガバナンス | -ユーザーが Google にパスワードをリセットする必要があります (接続されたリンクされた G Suite インスタンスが必要です)<br />-ユーザーの中断 (接続されたリンクされた G Suite インスタンスが必要)<br />-警告をユーザーに通知する (Azure AD 経由)<br />-ユーザーにもう一度サインインするように要求します (Azure AD 経由)<br />-ユーザーの中断 (Azure AD 経由) |

アプリからの修復脅威の詳細については、「[接続されているアプリの管理](governance-actions.md)」を参照してください。

## <a name="protect-gcp-in-real-time"></a>GCP をリアルタイムで保護する

[外部ユーザーとのセキュリティ保護とコラボレーション](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls)に関するベストプラクティスを確認し、[機密データのダウンロードをアンマネージまたは危険なデバイスにブロックして保護](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices)します。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [GCP を Microsoft Cloud App Security に接続する方法](connect-google-gcp-to-microsoft-cloud-app-security.md)
