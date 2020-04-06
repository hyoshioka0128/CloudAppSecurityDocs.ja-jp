---
title: Cloud App Security がコンテンツ検査を実行する方法
description: この記事では、クラウド内のデータに対して DLP コンテンツ検査を実行するときのプロセス Cloud App Security について説明します。
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
ms.openlocfilehash: 543631f5ffaa6716d8686e86e1386b55c081158b
ms.sourcegitcommit: 288c279a0d2dd62a8ad8d7425c3e9e98857bf5f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2020
ms.locfileid: "80666477"
---
# <a name="built-in-content-inspection"></a>組み込みのコンテンツ検査

*適用対象: Microsoft Cloud App Security*

この記事では、クラウド内のデータに対して組み込みの DLP コンテンツ検査を実行するときの Microsoft Cloud App Security プロセスについて説明します。

Cloud App Security コンテンツ検査は次のように機能します。

1. まず、Cloud App Security は、新規または変更されたことが検出されたドライブとイベントのほぼリアルタイム (NRT) のスキャンを実行します。
2. スキャンが完了すると、Cloud App Security はすべてのドライブ内のすべての関連ファイルを継続的にスキャンします。

NRT スキャンと連続スキャンの両方のファイルが、検査のためにキューに追加されます。 スキャンキュー内のファイルの順序は、ファイルおよびドライブのスキャンに対するアクティビティごとに設定されます。 ファイルがスキャンされるのは、ファイルのメタデータがサポートされている MIME の種類であることが示されている場合のみです。 このスキャンは、データスキャンに関連するファイル (ドキュメント、画像、プレゼンテーション、スプレッドシート、テキスト、zip/アーカイブファイル) を対象としています。

ファイルがスキャンされると、次の操作が行われます。

1. Cloud App Security は、コンテンツ自体ではなく、メタデータに関連するすべてのカスタムポリシーを適用します。 たとえば、ファイルが 20 MB を超える場合にアラートを生成するポリシーや、.docx ファイルが OneDrive に保存されたときにアラートを生成するポリシーなどがあります。

2. コンテンツ検査を必要とするポリシーがあり、ファイルがコンテンツ検査の対象になっている場合、コンテンツは検査のためにキューに入れられます。 キューの長さは、テナントのサイズとスキャンが必要なファイルの数によって異なります。

3. この時点で、[ > **ファイル**の**調査**] に移動し、ファイルをクリックして、コンテンツ検査の状態を確認できます。 ファイルの詳細が表示されたファイルドロアーで、**コンテンツ検査の状態**は **[完了]** 、 **[保留中]** 、 **[該当なし]** (ファイルの種類がサポートされていない場合)、またはエラーメッセージのいずれかが表示されます。 コンテンツスキャンエラーメッセージの詳細については、「[コンテンツ検査のトラブルシューティング](troubleshooting-content-inspection.md)」を参照してください。

> [!NOTE]
> スキャン状態にダッシュが表示されている場合は、そのファイルがスキャンの対象としてキューに登録されていないことを意味します。 コンテンツ検査ポリシーの設定の詳細については、「[ファイルポリシー](data-protection-policies.md) 」を参照してください。

組み込みのコンテンツ検査スキャンポリシーでは、次の項目を検索できます。

- 電子メールアドレス
- クレジットカード番号
  - すべてのクレジットカード会社 (Visa、MasterCard、アメリカ Express、Diners クラブ、Discover、JCB、Dankort、UnionPay)
  - 区切り記号-スペース、ドット、またはダッシュ
  - このスキャンには、Luhn 検証も含まれます。
- SWIFT コード
- 国際パスポート番号
- 運転免許証番号
- Dates
- 銀行 ABA ルーティングの転送数
- 銀行識別コード
- HIPAA HICN Health 保険請求番号
- HIPAA NPI National プロバイダーの id 番号
- PHI の氏名と生年月日
- カリフォルニア ID または運転免許証番号
- 運転免許証番号
- 自宅の住所
- Passport カード
- 社会保障番号

## <a name="supported-languages"></a>サポートされる言語

Cloud App Security コンテンツ検査エンジン:

- すべての Unicode 文字をサポートします。
- 100のファイルの種類について説明します。
- 複数の言語がサポートされています。特に、Unicode 文字セットを使用するファイルです。 これらの言語を考慮して、ポリシーを定義してください。 たとえば、キーワードを探している場合は、使用する言語全体でキーワードを指定する必要があります。
- Unicode 以外のエンコーディングを使用するテキストベースのファイルの種類 (中国語 GB2312 など) では、Unicode 中国語キーワードとの比較は期待どおりに機能しません。
- サードパーティのライブラリに依存しているファイルの種類の場合、一致する文字列と単語が期待どおりに機能しないことがあります。 これは、ファイル (バイナリファイルの種類など) で最も一般的であり、コンテンツ検査では、言語および文字セットの Java 文字列を返すサードパーティのライブラリに依存しています。

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
