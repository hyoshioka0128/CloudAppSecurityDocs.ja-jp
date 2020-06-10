---
title: Cloud App Security REST API
description: この記事では、HTTPS 経由で Cloud App Security を操作する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: df70a9408b88692b9faf789a00b5f307c0af24ee
ms.sourcegitcommit: 3172d6bd5e9d7a08f5cd2aa2e36980ef21bf0235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84563901"
---
# <a name="cloud-app-security-rest-api"></a>Cloud App Security REST API

*適用対象:Microsoft Cloud App Security*

この記事では、HTTPS 経由で Cloud App Security を操作する方法について説明します。

Microsoft Cloud App Security API を使うと、REST API エンドポイントからプログラムで Cloud App Security にアクセスできます。 アプリケーションで API を使うことにより、Cloud App Security のデータとオブジェクトに対して読み取りと更新の操作を実行できます。 たとえば、Cloud App Security API は、ユーザー オブジェクトに対する次の一般的な操作をサポートしています。

- Cloud Discovery のログ ファイルをアップロードします
- ブロック スクリプトを生成します
- アクティビティとアラートの一覧表示
- アラートを無視または解決します

## <a name="api-url-structure"></a>API URL 構造

Cloud App Security API を使用するには、最初にテナントから API URL を取得する必要があります。 API URL は、の形式を使用し `https://<portal_url>/api/<endpoint>` ます。

テナントの Cloud App Security ポータルの URL を取得するには、次の手順を実行します。

1. Cloud App Security ポータルで、メニュー バーの**疑問符のアイコン**をクリックします。 次に、**[バージョン情報]** を選択します。

    ![[バージョン情報] をクリックします。](media/about-menu.png)

1. Cloud App Security の [バージョン情報] 画面に、ポータルの url が表示されます。

    ![データ センターを表示する](media/api-url.png)

ポータルの url を取得したら、 `/api` それにサフィックスを追加して API url を取得します。 たとえば、ポータルの URL がの場合、 `https://mytenant.us2.contoso.com` API url はに `https://mytenant.us2.contoso.com/api` なります。

## <a name="api-tokens"></a>API トークン

Cloud App Security には、次のように、サーバーへのすべての API 要求のヘッダーに API トークンが必要です。

```http
Authorization: Token <your_token_key>
```

ここ `<your_token_key>` で、は個人用 API トークンです。

API トークンの詳細については、「 [api トークンの管理](api-authentication.md)」を参照してください。

### <a name="example"></a>例

```rest
curl -XGET -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/example-endpoint"
```

## <a name="what-actions-are-supported"></a>サポートされているアクション

次の表では、サポートされている操作について説明します。

|リソース|HTTP 動詞|URI ルート|
|---|---|---|
|探索|GET、POST、PUT|/api/v1/discovery/|
|データ強化|POST|/サブネット/|
|Activities|GET または POST|/api/v1/activities/|
|警告|GET または POST|/api/v1/alerts/|
|エンティティ|GET または POST|/api/v1/entities/|
|Files|GET または POST|/api/v1/files/|

ここで、**リソース**は関連エンティティのグループを表します。

## <a name="what-field-types-are-supported"></a>どのようなフィールドの種類がサポートされていますか。

次の表では、サポートされているフィールドの種類について説明します。

|フィールド|説明|
|---|---|
|string|テキスト文字列|
|boolean|True/false を表すブール値|
|整数 (integer)|32 ビット符号付き整数|
|timestamp|エポックからのミリ秒|

## <a name="limits"></a>制限

要求に limit パラメーターを指定することで、要求の制限を選択できます。

Limit パラメーターを指定するために、次のメソッドがサポートされています。

- URL エンコード (ヘッダー付き `Content-Type: application/x-www-form-urlencoded` )
- フォームデータ
- JSON 本文 ( `Content-Type: multipart/form-data` および適切な境界ヘッダーを含む)

> [!NOTE]
>
> - 制限を指定しない場合、既定で100が設定されます。
> - API トークンを使用して行われるすべての要求に対する応答は、最大100項目に制限されます。

## <a name="filters"></a>フィルター

多数の結果がある場合は、フィルターを使用して要求を微調整すると便利です。 ここでは、フィルターで使用できるの構造と、で使用できる演算子について説明します。

### <a name="structure"></a>構造体

一部の API エンドポイントは、クエリの実行時にフィルターをサポートしています。 関連するセクションには、使用可能なすべてのフィルター選択可能なフィールドと、そのリソースでサポートされている演算子の一覧が記載されています。

ほとんどのフィルターでは、強力なクエリを提供するために複数の値がサポートされています。 フィルターと演算子を組み合わせる場合は、フィルター間の論理演算子としてとを使用します。

### <a name="example"></a>例

```rest
curl -XGET -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/example-endpoint" -d '{
  "filters": {
    "some.field": {
      "eq": ["value1", "value2"],
      "isset": true
    },
    "some.field2": {
      "gte": 5
    }
  },
  "skip": 5,
  "limit": 10
}'
```

### <a name="operators"></a>演算子

> [!NOTE]
> すべての演算子がすべてのフィルターと互換性があるわけではありません。

次の表では、サポートされている演算子について説明します。

| 演算子 | 応答の種類 | 説明 |
| --- | --- | --- |
| contains | 文字列の一覧 | 指定された文字列の1つを含むすべての関連レコードを返します。 |
| deq | 値の一覧 | 指定された値と等しくない1つの値を含むすべてのレコードを返します |
| descendantof | 値の一覧 | 値または子孫の子孫に一致するすべての関連レコードを返します |
| notnotstartwith | 文字列の一覧 | 指定された各文字列で開始されていないすべての関連レコードを返します。 |
| endswith | 文字列の一覧 | 指定されたいずれかの文字列で終わるすべての関連レコードを返します。 |
| eq | 値の一覧 | 指定された値のいずれかを含むすべての関連レコードを返します。 |
| gt | 単一の値 | 値が指定された値より大きいすべてのレコードを返します |
| gte | 単一の値 | 指定された値以上の値を持つすべてのレコードを返します |
| gte_ndays | number | N 日前よりも後の日付を持つすべてのレコードを返します |
| isnotset | boolean | "True" に設定すると、指定したフィールドに値がない関連レコードがすべて返されます。 |
| isset | boolean | "True" に設定すると、指定したフィールドに値を持つすべての関連レコードが返されます。 |
| lt | 単一の値 | 値が指定された値より小さいすべてのレコードを返します |
| lte | 単一の値 | 指定された値以下の値を持つすべてのレコードを返します |
| lte_ndays | number | N 日前より前の日付を持つすべてのレコードを返します |
| ncontains | 文字列の一覧 | 指定された文字列の1つを含まないすべての関連レコードを返します。 |
| ndescendantof | 値の一覧 | 一致しない値または子孫の子孫ではないすべての関連レコードを返します |
| neq | 値の一覧 | 指定されたすべての値を含まないすべての関連レコードを返します。 |
| range | "開始" フィールドと "終了" フィールドを含むオブジェクトの一覧 | 指定されたいずれかの範囲内のすべてのレコードを返します |
| startswith | 文字列の一覧 | 指定されたいずれかの文字列で始まるすべての関連レコードを返します。 |
| startswithsingle | string | 指定された文字列で始まるすべての関連レコードを返します。 |
| text | string | すべてのレコードのフルテキスト検索を実行します。 |

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [API 認証](api-authentication.md)

[!INCLUDE [Open support ticket](includes/support.md)]
