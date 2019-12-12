---
title: コンテンツ検査エラーのトラブルシューティング - Cloud App Security | Microsoft Docs
description: この記事では、コンテンツ検査の状態の一覧とその意味を示します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: be3c76516217e9cc36a06c85d778a717609ba254
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74721140"
---
# <a name="troubleshooting-content-inspection"></a>コンテンツ検査のトラブルシューティング

*適用対象: Microsoft Cloud App Security*

この記事では、コンテンツ検査の状態の一覧とその意味を示します。

## <a name="content-inspection-status"></a>コンテンツ検査の状態

この表には、各コンテンツ検査の状態とその説明を示します。

|コンテンツ検査の状態|[説明]|
|----|----|
|Completed|コンテンツ検査は正常に完了しました。|
|適用できません|コンテンツ検査をこのファイルに適用できませんでした。 この状態は、このファイルのコンテンツ検査が必要なポリシーがないか、ファイルの種類がサポートされていないことが原因で表示されることがあります。|
|Pending|ファイルは現在、コンテンツ検査キュー内にあります。|
|失敗: ダウンロード エラー|Microsoft Cloud App Security が検査用のファイルをダウンロードできませんでした。|
|失敗: ファイルが暗号化されています|このファイルの暗号化を解除できませんでした。|
|失敗: ファイルが壊れています|ファイルが何らかの方法で破損しており、検査できませんでした。|
|失敗: 内部エラー|ファイルを検査しようとして、不明な何らかの問題が発生しました。|
|失敗: 外部 DLP エラー|外部 DLP で何らかの問題が発生したため、Cloud App Security がコンテンツの検査に失敗しました。|
|失敗: ファイル サイズを超えています|ファイルの制限は、ファイル サイズと文字数によって異なります。|
|失敗: ファイル アクセス拒否|ファイルはクラウドの外部にあり、Cloud App Security からアクセスできませんでした。|
|失敗: ファイルは削除されました|ファイルは現在クラウドに存在しておらず、検査できませんでした。|
|失敗: サポートされていないファイルの種類|Cloud App Security は、このファイルの種類に対してコンテンツ検査を実行できません。 この状態は、ファイルの種類がサポートされていないか、ファイルが実際には予期されるファイルの種類の形式でないことが原因で表示される場合があります。|

> [!NOTE]
> スキャンの状態にダッシュが表示される場合、そのファイルはスキャン対象としてキューに登録されていません。 コンテンツ検査ポリシーの詳細については、「[データ保護ポリシー](data-protection-policies.md)」を参照してください。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
