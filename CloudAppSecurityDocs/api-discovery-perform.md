---
title: ファイルのアップロードを実行する-Cloud Discovery API
description: この記事では Cloud App Security の Cloud Discovery API でのファイルアップロード要求の実行について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: b187b8cfa7b9df0610523baeb02410b76bcf00f4
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505381"
---
# <a name="perform-file-upload---cloud-discovery-api"></a>ファイルのアップロードを実行する-Cloud Discovery API

*適用対象:Microsoft Cloud App Security*

HTTP PUT 要求を実行して、ファイルの内容をアップロードします。 [ファイルのアップロードの開始](api-discovery-initiate.md)要求によって返される URL を使用する必要があります。

ターゲット URL にファイルをアップロードする場合、Azure と AWS のヘッダーと制限は異なります。

> [!NOTE]
>
> - 最大 5 GB の個々のファイルをアップロードできます。 より大きなファイルをアップロードする必要がある場合は、Cloud Discovery データを複数のチャンクに分割します。
> - 実行している環境がわからない場合は、[[ファイルのアップロードの開始](api-discovery-initiate.md)] 要求を確認します。これにより、この情報が返されます。

## <a name="http-request"></a>HTTP 要求

```rest
PUT https://<initiate_file_upload_response_url>
```

> [!NOTE]
>
> Azure の場合:
> - ファイルが 64 MB 未満の場合は、要求にヘッダー "x-y-ms-BlockBlob" を追加します。
> - ファイルサイズが 64 MB を超える場合は、チャンク単位でアップロードします。 これを行う最も簡単な方法は、 [AZURE SDK](https://azure.microsoft.com/downloads/)を使用することです。

## <a name="example"></a>例

### <a name="request"></a>Request

Azure の要求の例を次に示します。

```rest
curl --request PUT --upload-file <file_to_upload> -H "x-ms-blob-type: BlockBlob" "https://<initiate_file_upload_response_url>"
```

Azure Java SDK の要求の例を次に示します。

```java
File fileReference = new File("file.name");
// Create a blob using the URI that contains the shared access signature.
CloudBlockBlob sasBlob = new CloudBlockBlob(uri);

// Upload the file to the blob.
sasBlob.upload(new FileInputStream(fileReference), fileReference.length());
```

[!INCLUDE [Open support ticket](includes/support.md)]
