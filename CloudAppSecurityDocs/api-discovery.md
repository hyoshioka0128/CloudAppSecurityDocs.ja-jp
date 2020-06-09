---
title: Cloud App Security Cloud Discovery API
description: この記事では、Cloud Discovery API の使用方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 647570edd98fd1fd4977a9096fcf475f3ee09a8e
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505251"
---
# <a name="cloud-discovery-api"></a>Cloud Discovery API

*適用対象:Microsoft Cloud App Security*

Cloud Discovery は、ユーザーが提供するシステムログを解析して、クラウド環境内の新しいアプリケーションや不明なアプリケーションを検出します。 Cloud Discovery API を使用して、会社の探索ログファイルのアップロードを自動化します。 ファイルのアップロードプロセスは3つの API 呼び出しで構成され、連続して呼び出す必要があります。

また、Cloud App Security では、既存のオンプレミスセキュリティアプライアンスを使用して、承認されていないアプリへのアクセスをブロックすることができます。 ブロックスクリプトの生成呼び出しを使用して専用ブロックスクリプトを取得し、それをアプライアンスにインポートします。

サポートされている要求を次に示します。

- [ファイルのアップロードの開始](api-discovery-initiate.md)
- [ファイルのアップロードを実行する](api-discovery-perform.md)
- [ファイルのアップロードの最終処理](api-discovery-finalize.md)
- [ブロック スクリプトを生成する](api-discovery-script.md)

[!INCLUDE [Open support ticket](includes/support.md)]
