---
title: API を使用してアクティビティを調査する-Cloud App Security |Microsoft Docs
description: この記事では、API を使用して Cloud App Security のユーザーアクティビティを調査する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/26/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 0f2f971d-10e3-496d-8004-96d9fad71cae
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 98b1811fb17b0ade9a7901761e10c9dbb28d01f3
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72335746"
---
# <a name="investigate-activities-using-the-api"></a>API を使用してアクティビティを調査する

*適用対象: Microsoft Cloud App Security*

Microsoft Cloud App Security には、サービスをプログラムで操作できるようにするための完全にサポートされた REST API が用意されています。

Microsoft Cloud App Security Api を使用して、接続されたクラウドアプリ全体でユーザーが実行するアクティビティを調査できます。 

Cloud App Security アクティビティ API モードは、大量のデータ (5000 アクティビティを超える) のスキャンと取得のために最適化されています。 API スキャンは、すべての結果がスキャンされるまで、アクティビティデータに対して繰り返しクエリを実行します。 

> [!NOTE] 
> 大量のアクティビティと大規模なデプロイの場合は、アクティビティのスキャンに[SIEM エージェント](siem.md)を使用することをお勧めします。

**アクティビティスキャン API を使用するには:**

1. データに対してクエリを実行します。
1. 1回のスキャンで一覧表示されているよりも多くのレコードがある場合は、@no__t 0 の return コマンドを実行する必要があります。 このコマンドは、クエリがすべての結果を返すまでスキャンするたびに取得されます。
 
 
**要求本文のパラメーター**:
- "filters": 要求のすべての検索フィルターを使用してオブジェクトをフィルター処理します。詳細については、「[アクティビティフィルター](activity-filters.md) 」を参照してください。 要求が調整されないようにするには、クエリに制限を含めてください。たとえば、最後の日のアクティビティに対してクエリを実行したり、特定のアプリをフィルター処理したりすることができます。
- "isScan": Boolean。 スキャンモードを有効にします。
- "sortDirection": 並べ替えの方向、可能な値は "asc" と "desc" です。 
- "sortField": アクティビティの並べ替えに使用されるフィールドです。 次の値をとります。 
    - 日付-アクティビティが発生した日付 (既定値)。
    - created-アクティビティが保存されたときのタイムスタンプ。
- "limit": 整数。 スキャンモードでは、500と 5000 (既定値は 500) です。 すべてのデータをスキャンするために使用する反復処理の回数を制御します。 

**応答パラメーター**:
- "data": 返されるデータ。 には、各反復処理のレコード数が "制限" されます。 プルするレコードが多い場合 (hasNext = true)、すべてのデータが1回だけ表示されるように、最後のいくつかのレコードが削除されます。
- "hasNext": Boolean。 データの別の反復処理が必要かどうかを示します。
- "nextQueryFilters": 別のイテレーションが必要な場合は、実行する連続する JSON クエリが含まれています。 次の要求では、これを "filters" パラメーターとして使用します。

次の Python の例では、Exchange Online から過去1日のすべてのアクティビティを取得します。

      import requests
      import json
      ACTIVITIES_URL = 'https://<your_tenant>.portal.cloudappsecurity.com/api/v1/activities/'
    
      your_token = '<your_token>'
         headers = {
         'Authorization': 'Token {}'.format(your_token),
        }
    
        filters = {
          # optionally, edit to match your filters
          'date': {'gte_ndays': 1},
          'service': {'eq': [20893]}
        }
        request_data = {
         'filters': filters,
         'isScan': True
        }
        
        records = []
        has_next = True
        while has_next:
            content = json.loads(requests.post(ACTIVITIES_URL, json=request_data, headers=headers).content)
            response_data = content.get('data', [])
            records += response_data
            print('Got {} more records'.format(len(response_data)))
            has_next = content.get('hasNext', False)
            request_data['filters'] = content.get('nextQueryFilters')
        
        print('Got {} records in total'.format(len(records)))
        
 
## <a name="next-steps"></a>次のステップ
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
