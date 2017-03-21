---
title: "Cloud App Security でコンテンツの検査を実施する方法 | Microsoft ドキュメント"
description: "この記事では、クラウド内のデータに対して DLP コンテンツ検査を実行する場合に Cloud App Security が従うプロセスについて説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2401adbc-0011-4938-9e3a-a4c719a2f619
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: a1ff57c60d8b35711330e8e4879fe1a48a7dee77
ms.sourcegitcommit: 355226ee21981563066d637e7db0bff0d53c2da6
translationtype: HT
---
# <a name="content-inspection"></a>コンテンツ検査
この記事では、クラウド内のデータに対して DLP コンテンツ検査を実行する場合に Cloud App Security が従うプロセスについて説明します。 


Cloud App Security コンテンツ検査は次のように行われます。
1. Cloud App Security は、まず新規または変更されたものとして検出されたイベントとドライブに対してほぼリアルタイム (NRT) のスキャンを実行します。
2. この処理の完了後、Cloud App Security はすべてのドライブのすべての関連ファイルを継続的にスキャンします。  

NRT スキャンが実行されるファイルと継続的にスキャンされるファイルは、両方とも検査のためにキューに追加されます。 スキャン キュー内のファイルの順序は、ファイルと、ドライブのスキャンでのアクティビティごとに設定されます。 ファイルがスキャンされるのは、ファイル メタデータでサポートされている MIME の種類であることが示されている場合のみです。 このスキャンは、データ スキャンに関連するファイルに対して行われます (ドキュメント、画像、プレゼンテーション、スプレッドシート、テキスト、zip/アーカイブ ファイル)。  

ファイルがスキャンされた後、以下の処理が行われます。

1. Cloud App Security は、コンテンツ自体ではなく、メタデータに関連するカスタム ポリシーをすべて適用します。 たとえば、ファイルが 20 MB を超える場合に警告するポリシーや、docx ファイルが OneDrive に保存される場合に警告するポリシーなどです。 

2. コンテンツ検査を必要とするポリシーがあり、ファイルがコンテンツ検査の対象である場合、コンテンツは検査のためにキューに入れられます。 キューの長さは、テナントのサイズと、スキャンを必要とするファイルの数によって異なります。 

3. この時点で、**[検査]** > **[ファイル]** に移動し、ファイルをクリックすれば、コンテンツ検査の状態を表示できます。 ファイルの詳細情報が表示されたファイル ドロワーの **[Content Inspection status]** (コンテンツ検査の状態) には、**[Completed]** (完了)、**[Pending]** (保留中)、**[Not applicable]** (該当なし) が表示されます。 コンテンツ スキャンのエラー メッセージの詳細については、「[Troubleshooting content inspection](troubleshooting-content-inspection.md)」(コンテンツ検査のトラブルシューティング) を参照してください。

> [!NOTE]
> スキャンの状態にダッシュが表示される場合、そのファイルはスキャン対象としてキューに登録されていません。 コンテンツ検査ポリシーの詳細については、「[データ保護ポリシー](data-protection-policies.md)」を参照してください。

組み込みのコンテンツ検査スキャン ポリシーでは、以下を検索できます。

- 電子メール アドレス 
- クレジット カード番号 
  - すべてのクレジット カード会社 (Visa、MasterCard、American Express、Diners Club、Discover、JCB、Dankort、UnionPay) 
  - 区切り記号 (スペース、ドット、またはダッシュ)
  - このスキャンには、Luhn 検証も含まれています。
- SWIFT コード
- 国際パスポート番号
- 運転免許証番号
- 日付
- 銀行の ABA ルーティング転送番号
- 銀行識別コード
- HIPAA HICN 健康保険請求番号
- HIPAA NPI National プロバイダー識別番号
- PHI の姓名と誕生日
- カリフォルニア州 ID または運転免許証番号
- 運転免許証番号
- 自宅住所
- パスポート カード
- 社会保障番号



## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  