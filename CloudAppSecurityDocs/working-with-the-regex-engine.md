---
title: コンテンツ検査ポリシーに Cloud App Security の RegEx エンジンを使用する
description: この記事では、Cloud App Security ポリシーのパターン マッチングに正規表現を使用する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/14/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5c055cebf7bf63f50fcea997648316f25a7b4429
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74721150"
---
# <a name="working-with-the-regex-engine"></a>RegEx エンジンの操作

*適用対象: Microsoft Cloud App Security*

この記事では、Cloud App Security ポリシーのパターン マッチングに正規表現を使用する方法について説明します。

## <a name="regular-expressions-in-cloud-app-security"></a>Cloud App Security での正規表現

Microsoft Cloud App Security のコンテンツ検査ポリシーでは、パターン マッチングに正規表現が使用されます。 コンテンツ検査は、ファイル ポリシーの一部として適用できます。

### <a name="testing-regular-expressions"></a>正規表現のテスト

正規表現をテストするには、次の Web サイトを使用できます。

- [https://regexpal.com/](https://regexpal.com/) - 必ず**大文字と小文字の区別なし**を選択します。

- [https://regex101.com/](https://regex101.com/) - 正規表現を詳細に分析できます。

### <a name="limitations-of-regular-expressions-in-cloud-app-security"></a>Cloud App Security での正規表現の制限

カスタムの正規表現には、次の制限が課せられます。

- 検索では常に大文字と小文字が区別されません。

- 使用できる数量詞: {n, m} n、m < 10

- すべてのグループは非キャプチャである必要があります。例: (?: xxx)

    (group) の代わりに (?:group) を使用します

- 使用できない数量詞: *、+、{n,}

    \* の代わりに {0,9} を使用します

    \+ の代わりに {1,9} を使用します

- 使用できない逆参照: \\<number\> または \k\<name>

### <a name="example-expressions"></a>式の例

次の表では、式の例と、一致するかどうかを示します。

|              正規表現              |                     データ                     |      [一致する]      |
|---------------------------------------------------------------|---------------------------------------------------------------|------------------------------------|
|            Colou?r (?:black&#124;blue&#124;white)             |   Color black<br /><br /> Color white<br /><br /> Color red   | [はい]<br /><br /> [はい]<br /><br /> [いいえ] |
|           [a-z0-9]{1,9}@[a-z0-9]{1,9}\\.[a-z]{2,3}            | Some1@abc.com<br /><br /> user@host.org<br /><br /> @bad.com  | [はい]<br /><br /> [はい]<br /><br /> [いいえ] |
| 20\d{2}-(?:0[1-9]&#124;1[0-2])-(?:[0-2][0-9]&#124;30&#124;31) |   2015-12-31<br /><br /> 2015-01-09<br /><br /> 1999-12-31    | [はい]<br /><br /> [はい]<br /><br /> [いいえ] |
|                       d.n't\s{0,10}c.r.                       | Don't     care<br /><br /> D!n'tcor0<br /><br /> Doesn't care | [はい]<br /><br /> [はい]<br /><br /> [いいえ] |

## <a name="check-out-this-video"></a>このビデオをご覧ください。

> [!div class="nextstepaction"]
> [RegEx エンジンの操作](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security-Working-with-the-Regex-Engine)

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
