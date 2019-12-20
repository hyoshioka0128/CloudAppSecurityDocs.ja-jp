---
title: Cloud App Security によってアマゾンウェブサービス環境を保護する方法
description: この記事では、AWS アプリを API コネクタを使用して Cloud App Security に接続する利点について説明します。これにより、使用状況を表示したり制御したりできます。
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: 151e698fe196946c41e945857b69a1e41135d433
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75190012"
---
# <a name="how-cloud-app-security-helps-protect-your-amazon-web-services-aws-environment"></a>Cloud App Security によってアマゾンウェブサービス (AWS) 環境を保護する方法

*適用対象: Microsoft Cloud App Security*

アマゾンウェブサービスは、組織がクラウドでワークロード全体をホストして管理できるようにする IaaS プロバイダーです。 クラウドでインフラストラクチャを活用する利点と共に、組織の最も重要な資産が脅威にさらされる可能性があります。 公開された資産には、機密性の高い情報を持つストレージインスタンス、最も重要なアプリケーション、ポート、および仮想プライベートネットワークの一部を操作するコンピューティングリソースが含まれます。これにより、組織へのアクセスが可能になります。

AWS を Cloud App Security に接続することで、資産を保護し、潜在的な脅威を検出することができます。これには、管理およびサインインアクティビティを監視し、考えられるブルートフォース攻撃、特権のあるユーザーアカウントの悪意のある使用、Vm の異常な削除を通知します。パブリックに公開されているストレージバケット。

## <a name="main-threats"></a>主な脅威

- クラウドリソースの不正悪用
- 侵害されたアカウントと内部の脅威
- データ漏えい
- リソースの構成に誤りがあり、アクセス制御が不十分である

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Cloud App Security が環境の保護にどのように役立つか

- [クラウドの脅威、侵害されたアカウント、悪意のある内部関係者の検出](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [共有データの公開を制限し、コラボレーションポリシーを適用する](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [最新のセキュリティ構成の推奨事項を使用して最新情報を入手する](security-config-aws.md)
- [フォレンジック調査のためにアクティビティの監査証跡を使用する](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-aws-with-built-in-policies-and-policy-templates"></a>組み込みのポリシーとポリシーテンプレートを使用した AWS の制御

次の組み込みポリシーテンプレートを使用して、潜在的な脅威についての検出と通知を行うことができます。

| 種類 | 名前 |
| ---- | ---- |
| アクティビティポリシーテンプレート | 管理コンソールのサインインエラー<br />CloudTrail の構成の変更<br />EC2 インスタンスの構成の変更<br />IAM ポリシーの変更<br />Logon from a risky IP address (危険な IP アドレスからのログオン)<br />ネットワークアクセス制御リスト (ACL) の変更<br />ネットワークゲートウェイの変更<br />S3 構成の変更<br />セキュリティグループの構成の変更<br />仮想プライベートネットワークの変更 |
| 組み込みの異常検出ポリシー | [匿名 IP アドレスからのアクティビティ](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[頻度の低い国からのアクティビティ](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[不審な IP アドレスからのアクティビティ](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[あり得ない移動](anomaly-detection-policy.md#impossible-travel)<br />[終了したユーザーによって実行されるアクティビティ](anomaly-detection-policy.md#activity-performed-by-terminated-user)(AAD は IdP として必要)<br />[複数回失敗したログイン試行](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[通常とは異なる管理アクティビティ](anomaly-detection-policy.md#unusual-activities-by-user)<br />[通常とは異なる複数のストレージ削除アクティビティ](anomaly-detection-policy.md#unusual-activities-by-user)(プレビュー)<br />[複数の VM 削除アクティビティ](anomaly-detection-policy.md#multiple-delete-vm-activities)<br />[通常とは異なる複数の VM 作成アクティビティ](anomaly-detection-policy.md#unusual-activities-by-user)(プレビュー) |
| ファイルポリシーテンプレート | S3 バケットにパブリックにアクセスできる |

ポリシーの作成の詳細については、「[ポリシーを作成する](control-cloud-apps-with-policies.md#create-a-policy)」を参照してください。

## <a name="automate-governance-controls"></a>ガバナンスコントロールの自動化

潜在的な脅威を監視するだけでなく、次の AWS ガバナンスアクションを適用して自動化し、検出された脅威を修復できます。

| 種類 | 操作 |
| ---- | ---- |
| ユーザーガバナンス | -警告をユーザーに通知する (Azure AD 経由)<br />-ユーザーにもう一度サインインするように要求します (Azure AD 経由)<br />-ユーザーの中断 (Azure AD 経由) |
| データガバナンス | -S3 バケットをプライベートにする<br />-S3 バケットのコラボレーターを削除します |

アプリからの修復脅威の詳細については、「[接続されているアプリの管理](governance-actions.md)」を参照してください。

## <a name="protect-aws-in-real-time"></a>AWS をリアルタイムで保護する

管理されていない[デバイスまたは危険なデバイスへの機密データのダウンロードをブロックし、保護する](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices)ためのベストプラクティスを確認します。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [AWS を Microsoft Cloud App Security に接続する方法](connect-aws-to-microsoft-cloud-app-security.md)
