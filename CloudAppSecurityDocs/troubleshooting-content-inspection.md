---
title: "Cloud App Security で検出されたコンテンツ検査エラーのトラブルシューティング | Microsoft ドキュメント"
description: "このトピックでは、コンテンツ検査の状態の一覧とその意味を示します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/10/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 359eb77f-e719-4c50-9b62-6ef64149a5a5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 40f759d58fe26776c0738271c0112d00bb52bf5a
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2017
---
# <a name="troubleshooting-content-inspection"></a>コンテンツ検査のトラブルシューティング
|コンテンツ検査の状態|説明|
|----|----|
|Completed|コンテンツ検査は正常に完了しました。|
|適用できません|コンテンツ検査をこのファイルに適用できませんでした。 これは、このファイルのコンテンツ検査が必要なポリシーがないか、ファイルの種類がサポートされていないことが原因と考えられます。|
|Pending|ファイルは現在、コンテンツ検査キュー内にあります。|
|失敗: ダウンロード エラー|Cloud App Security が検査用のファイルをダウンロードできませんでした。|
|失敗: ファイルが暗号化されています|このファイルにアクセスできませんでした。|
|失敗: ファイルが壊れています|ファイルが何らかの方法で破損しており、検査できませんでした。|
|失敗: 内部エラー|ファイルを検査しようとして、不明な何らかの問題が発生しました。|
|失敗: 外部 DLP エラー|外部 DLP で何らかの問題が発生したため、Cloud App Security がコンテンツの検査に失敗しました。|
|失敗: ファイル サイズを超えています|ファイルの制限は、ファイル サイズと文字数によって異なります。|
|失敗: ファイル アクセス拒否|ファイルはクラウドの外部にあり、Cloud App Security からアクセスできませんでした。|
|失敗: ファイルは削除されました|ファイルは現在クラウドに存在しておらず、検査できませんでした。|
|失敗: サポートされていないファイルの種類|Cloud App Security は、このファイルの種類に対してコンテンツ検査を実行できません。 これは、ファイルの種類がサポートされていないか、ファイルが実際には予期されるファイルの種類の形式でないことが原因と考えられます。|

> [!NOTE]
> スキャンの状態にダッシュが表示される場合、そのファイルはスキャン対象としてキューに登録されていません。 コンテンツ検査ポリシーの詳細については、「[データ保護ポリシー](data-protection-policies.md)」を参照してください。

## <a name="see-also"></a>参照  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  