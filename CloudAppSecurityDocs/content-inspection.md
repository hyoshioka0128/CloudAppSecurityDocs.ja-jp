---
title: Cloud App Security でコンテンツの検査を実施する方法 | Microsoft ドキュメント
description: この記事では、クラウド内のデータに対して DLP コンテンツ検査を実行する場合に Cloud App Security が従うプロセスについて説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 2401adbc-0011-4938-9e3a-a4c719a2f619
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c40e7081cab923f5778912425e3f34776b849bbd
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143770"
---
*適用対象: Microsoft Cloud App Security*



# <a name="built-in-content-inspection"></a>組み込みのコンテンツ検査

この記事では、クラウド内のデータに対して組み込みの DLP コンテンツ検査を実行する場合に Microsoft Cloud App Security が従うプロセスについて説明します。 


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

## <a name="supported-languages"></a>サポートされている言語

Cloud App Security コンテンツ検査のエンジンは、次のようになっています。
-   すべての Unicode 文字をサポートします。
-   1,000 を超えるファイルの種類を扱います。
-   複数の言語、特に Unicode 文字セットを使用するファイルがサポートされています。 これらの言語をカバーするポリシーを定義するようにしてください。たとえば、キーワードを扱うなら、使用する言語のすべてについてキーワードを配置する必要があります。
-   中国語 (GB2312) などの非 Unicode エンコードを使うテキスト ベースのファイルの種類では、Unicode の中国語キーワードは期待通りには動作しません。
-   サード パーティ製のライブラリに依存しているファイルの種類では、文字列と単語のマッチングは常に期待通りに動作するとは限りません。 これがよく起きるのは、言語および文字のセットに Java 文字列を返すサードパーティ製のライブラリに依存したコンテンツ検査が行われるファイル (バイナリ ファイルなど) です。



## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  