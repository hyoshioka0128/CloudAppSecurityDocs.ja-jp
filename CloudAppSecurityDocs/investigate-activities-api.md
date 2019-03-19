---
title: Cloud App Security の API を使用してアクティビティの調査 |Microsoft Docs
description: この記事では、API を使用して Cloud App Security でのユーザー アクティビティを調査する方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 3/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 0f2f971d-10e3-496d-8004-96d9fad71cae
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 233df1cf7f01266bbca6c122a6908811e4c6649b
ms.sourcegitcommit: 57bad4dc9b28326c93ee480d308d52ea23c42089
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/18/2019
ms.locfileid: "58163873"
---
# <a name="investigate-activities-using-the-api"></a>API を使用してアクティビティを調査します。

*適用対象:Microsoft Cloud App Security*

Microsoft Cloud App Security Api を使用して、接続されているクラウド アプリ間で、ユーザーによって実行されたアクティビティを調査することができます。 

大量のデータ (5,000 を超えるアクティビティ) の取得とスキャンは、Cloud App Security アクティビティ API のモードが最適化されます。 API は、すべての結果のスキャンが完了するまで繰り返しクエリ アクティビティ データをスキャンします。 

> [!NOTE] 
> アクティビティと大規模なデプロイの量が多い場合望ましいを使用する、 [SIEM エージェント](siem.md)アクティビティをスキャンするためです。

**アクティビティのスキャン API を使用するには。**

1. データに対するクエリを実行します。
1. 単一のスキャンで扱われることよりも多くのレコードがある場合は、戻り値を持つコマンドが表示されます`nextQueryFilters`実行する必要があります。 このコマンドは、クエリのすべての結果が返されるまでをスキャンするたびに表示されます。
 
 
**要求本文のパラメーター**:
- 「フィルター」:フィルターは、要求は、すべての検索フィルターを使用してオブジェクトを参照してください[アクティビティ フィルター](activity-filters.md)詳細についてはします。 調整する、クエリの制限を含めることを確認要求を避けるには、最後の日のアクティビティをクエリや、特定のアプリをフィルター処理などです。
- "isScan":ブール値。 スキャン モードを有効にします。
- "sortDirection":並べ替え方向を指定できる値は"asc"と"desc" 
- "sortField":フィールドは、アクティビティの並べ替えに使用します。 次の値をとります。 
    - 日付 - アクティビティが発生し、日付 (これは、既定値です)。
    - 作成したアクティビティが保存されたときのタイムスタンプ。
- "limit":整数。 500 ~ 5000 で、スキャン モード (既定値は 500)。 すべてのデータをスキャンするために使用するイテレーションの数を制御します。 

**応答パラメーター**:
- "data": 返されるデータ。 最大レコード数が"limit"各反復処理されます。 多くのレコードがプルされることがある場合 (hasNext = true)、最後にいくつかのレコードをすべてのデータが 1 回だけ表示されていることを確実に削除されます。
- "hasNext":ブール値。 データを別のイテレーションが必要かどうかを示します。
- “nextQueryFilters”:別のイテレーションが必要な場合、連続する JSON クエリ実行するにはが含まれています。 これは、次回の要求に「フィルター」パラメーターとして使用します。



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
        
 
## <a name="next-steps"></a>次の手順
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
