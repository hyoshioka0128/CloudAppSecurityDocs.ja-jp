---
title: コンテンツ検査エラーのトラブルシューティング - Cloud App Security | Microsoft Docs
description: この記事では、コンテンツ検査の状態の一覧とその意味を示します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 359eb77f-e719-4c50-9b62-6ef64149a5a5
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 8e7c4de4407c476282db832f6d4aa60b0e987e1c
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568430"
---
# <a name="troubleshooting-content-inspection"></a>コンテンツ検査のトラブルシューティング

*適用対象:Microsoft Cloud App Security*

この記事では、コンテンツ検査の状態の一覧とその意味を示します。

## <a name="content-inspection-status"></a>コンテンツ検査の状態

この表には、各コンテンツ検査の状態とその説明を示します。

|コンテンツ検査の状態|説明|
|----|----|
|Completed|コンテンツ検査は正常に完了しました。|
|適用なし|コンテンツ検査をこのファイルに適用できませんでした。 この状態は、このファイルのコンテンツ検査が必要なポリシーがないか、ファイルの種類がサポートされていないことが原因で表示されることがあります。|
|Pending|ファイルは現在、コンテンツ検査キュー内にあります。|
|［失敗］:ダウンロード エラー|Microsoft Cloud App Security が検査用のファイルをダウンロードできませんでした。|
|［失敗］:ファイルを暗号化します。|このファイルの暗号化を解除できませんでした。|
|［失敗］:ファイルが壊れています|ファイルが何らかの方法で破損しており、検査できませんでした。|
|［失敗］:内部エラー。|ファイルを検査しようとして、不明な何らかの問題が発生しました。|
|［失敗］:外部 DLP エラー|外部 DLP で何らかの問題が発生したため、Cloud App Security がコンテンツの検査に失敗しました。|
|［失敗］:ファイル サイズを超えています|ファイルの制限は、ファイル サイズと文字数によって異なります。|
|［失敗］:ファイル アクセス拒否|ファイルはクラウドの外部にあり、Cloud App Security からアクセスできませんでした。|
|［失敗］:ファイルは削除されました|ファイルは現在クラウドに存在しておらず、検査できませんでした。|
|［失敗］:サポートされていないファイルの種類|Cloud App Security は、このファイルの種類に対してコンテンツ検査を実行できません。 この状態は、ファイルの種類がサポートされていないか、ファイルが実際には予期されるファイルの種類の形式でないことが原因で表示される場合があります。|

> [!NOTE]
> スキャンの状態にダッシュが表示される場合、そのファイルはスキャン対象としてキューに登録されていません。 コンテンツ検査ポリシーの詳細については、「[データ保護ポリシー](data-protection-policies.md)」を参照してください。

## <a name="see-also"></a>関連項目  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  

## <a name="next-steps"></a>次の手順
 
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)

