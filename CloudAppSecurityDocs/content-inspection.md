---
title: Cloud App Security がコンテンツ検査を実行する方法
description: この記事では、クラウド内のデータに対して DLP コンテンツ検査を実行するときのプロセス Cloud App Security について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 1/6/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 82d157bbe887f70194cbb55708635759e48433b1
ms.sourcegitcommit: 288c279a0d2dd62a8ad8d7425c3e9e98857bf5f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2020
ms.locfileid: "80666436"
---
# <a name="content-inspection"></a>コンテンツ検査

*適用対象: Microsoft Cloud App Security*

コンテンツ検査を有効にした場合は、事前設定された式を使用するか、他のカスタマイズされた式を検索するかを選択できます。

正規表現を指定して、結果からファイルを除外することができます。 このオプションは、ポリシーから除外する内部分類キーワード標準がある場合に非常に便利です。

ファイルが違反と見なされる前に、一致させるコンテンツ違反の最小数を設定できます。 たとえば、10個以上のクレジットカード番号が含まれているファイルについて警告を表示する場合は、10を選択できます。

選択した式とコンテンツが一致すると、違反テキストが "X" 文字に置き換えられます。 既定では、違反はマスクされ、違反の前後に100文字が表示されます。 式のコンテキスト内の数値は "#" 文字に置き換えられ、Cloud App Security 内には格納されません。 違反の最後の4文字をマスク**解除するオプション**を選択すると、違反自体の最後の4文字をマスク解除できます。 正規表現で検索するデータ型 (コンテンツ、メタデータ、ファイル名) を設定する必要があります。 既定では、コンテンツとメタデータが検索されます。

## <a name="content-inspection-for-protected-files"></a>保護されたファイルのコンテンツ検査

Cloud App Security を使用すると、管理者は、暗号化されたファイルの暗号化を解除し、そのコンテンツの違反をスキャンするための Cloud App Security アクセス許可を付与する

Cloud app Security に必要なアクセス許可を付与するには、次の手順を実行します。

1. **設定** にアクセスし、 **Azure Information Protection** をクリックします。
2. **保護されたファイルの検査を有効にします。**
3. プロンプトに従って、Azure Active Directory で必要なアクセス許可を付与します。
4. [ファイルごとの設定] ポリシーを構成して、保護されたファイルをスキャンするポリシーを指定することができます。

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
