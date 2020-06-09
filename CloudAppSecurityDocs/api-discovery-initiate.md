---
title: ファイルのアップロードの開始-Cloud Discovery API
description: この記事では、Cloud App Security の Cloud Discovery API での upload_url 要求について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 6259161ecaa02a7820d97aafc5b7efb98c988c07
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505391"
---
# <a name="initiate-file-upload---cloud-discovery-api"></a>ファイルのアップロードの開始-Cloud Discovery API

*適用対象:Microsoft Cloud App Security*

GET 要求を実行して、アップロードプロセスを開始します。 この呼び出し (最初の3つ) は、後でアップロード (PUT) 要求を実行するために使用される URL を返します。

## <a name="http-request"></a>HTTP 要求

```rest
GET /api/v1/discovery/upload_url/
```

## <a name="request-url-parameters"></a>要求 URL パラメーター

| パラメーター | Description |
| --- |--- |
| ファイル名 | Cloud Discovery の処理にアップロードするファイルの名前 |
| source | アップロードされている Cloud Discovery ログファイルの種類 |

現在、次のソースの種類がサポートされています。

- BARRACUDA
- BLUECOAT
- CHECKPOINT
- CHECKPOINT_CEF_SYSLOG
- CHECKPOINT_SMART_VIEW_TRACKER
- CHECKPOINT_XML
- CISCO_ASA
- CISCO_ASA_FIREPOWER
- CISCO_FIREPOWER_V6_SYSLOG
- CISCO_FWSM
- CISCO_IRONPORT_PROXY
- CISCO_IRONPORT_WSA_II
- CISCO_SCAN_SAFE
- CLAVISTER
- CORRATA
- FORCEPOINT
- FORCEPOINT_LEEF
- FORTIGATE
- GENERIC_CEF
- GENERIC_LEEF
- GENERIC_W3C
- I_FILTER
- IBOSS
- JUNIPER_SRX
- JUNIPER_SRX_SD
- JUNIPER_SRX_WELF
- JUNIPER_SSG
- MACHINE_ZONE_MERAKI
- MCAFEE_SWG
- MICROSOFT_ISA_W3C
- PALO_ALTO
- PALO_ALTO_LEEF
- SONICWALL_SYSLOG
- SOPHOS_CYBEROAM
- SOPHOS_SG
- SOPHOS_XG
- SQUID
- SQUID_NATIVE
- STORMSHIELD
- WEBSENSE_SIEM_CEF
- WEBSENSE_V7_5
- ZSCALER
- ZSCALER_CEF
- ZSCALER_QRADAR

> [!NOTE]
> ファイル形式が見つからない場合は、ポータルを使用して手動アップロードを実行します。

## <a name="response-parameters"></a>応答パラメーター

| パラメーター | 説明 |
| --- | --- |
| url | Cloud Discovery のアップロードを実行するターゲット URL。 |
| provider | "Azure" または "aws" のいずれかで、アップロードが Windows Azure Storage と AWS S3 ストレージのどちらを対象としているかを示します。 |

## <a name="example"></a>例

### <a name="request"></a>Request

要求の例を次に示します。

```rest
curl -XGET -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/discovery/upload_url/?filename=my_discovery_file.txt&source=LOG_3COM"
```

### <a name="response"></a>Response

JSON 応答の例を次に示します。

```json
{
  "url": "https://<initiate_file_upload_response_url>",
  "provider": "azure"
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
