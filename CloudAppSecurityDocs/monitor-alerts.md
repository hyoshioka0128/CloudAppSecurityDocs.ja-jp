---
title: Cloud App Security で発生するアラートを監視する
description: この記事では、すべてのアラートの一覧を示して説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: f118a3bf-1663-46ba-884f-b1b03a84ab66
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e5b144b4c260aa55f3bd6546f76c1802c10631e0
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568904"
---
# <a name="monitor-alerts-in-cloud-app-security"></a>Cloud App Security のアラートを監視する

*適用対象:Microsoft Cloud App Security*

アラートは、クラウド環境をより深く理解するための最初のステップです。 この記事では、すべてのアラートの一覧を示して説明します。

## <a name="monitoring-your-alerts"></a>アラートを監視する

すべてのアラートを確認することは良い考えです。 アラートの発生理由を理解することで、ポリシーを修正するための道具としてアラートを利用できます。 

**アラートを表示するには:** Microsoft Cloud App Security ポータルで **[アラート]** をクリックします。


![[アラート] メニュー](./media/alert-menu.png)

 - 確認して不要であると判断したら、アラートを**消去**します。 
     - アラートを消去した理由を説明する**コメント**を入力します。 
     - **[このアラートについてフィードバックをお送りください]** で送信されたフィードバックは Microsoft のセキュリティ研究チームが確認し、アラートの改善に役立てます。

- アラートを調査してリスクを軽減する場合、アラートの **[解決]** を選択します。 

     - このアラートは、アラート テーブルに表示されなくなります。
     - 問題の調査を開始した後、アラートを引き続き残しておきたい場合は、**未読としてマークします**。 
     -  今後のアラート一致を向上させるには、アラートと一致した**ポリシーを調整します**。 
     - アラートを解決する場合、コメントを入力し、**Cloud App Security チームにフィードバックを送信**できます。
 
## <a name="built-in-alerts"></a>組み込みアラート

次のアラートの種類が表示されます。 

|アラート名|アラート ID|説明|
|----|----|----|
|新しい場所|ALERT_GEOLOCATION_NEW_COUNTRY|スキャン開始以降に新しい場所が検出されました (6 か月)。 このアラートは、組織全体で国ごとに 1 回のみ表示されます。 |
|新しい管理ユーザー|ALERT_ADMIN_USER|特定のアプリに対して新しい管理者が検出されました。 あるアプリケーションの管理者が別のアプリケーションの管理者になったのがこの管理者である可能性があります。 このアラートは特定の管理者の種類に関するものなので、管理者の種類が変わるたびに表示されます。 ユーザーが管理者権限が失ってから再び権限を得ると、このアラートが表示されます。|
|非アクティブなアカウント|ALERT_ZOMBIE_USER|ユーザーが 1 つのアプリケーションについて 60 日間非アクティブになっている場合、たとえば、Box ではアクティブであっても G Suite を 60 日間使用していない場合、そのユーザーは G Suite について非アクティブであると見なされます。 そのようなユーザーにはタグが追加されるので、非アクティブなアカウントを検索できます。|
|予期しない管理の場所|ALERT_NEW_ADMIN_LOCATION|スキャン開始以降に、管理者に対して新しい場所が検出されました (6 か月)。 このアラートは、組織全体のすべての管理者について国ごとに 1 回のみ表示されます。 |
|危険な状態のアカウント|ALERT_COMPROMISED_ACCOUNT|アプリケーションで侵害が発生し、侵害されたアカウントの一覧が発行された場合、Cloud App Security は一覧をダウンロードして、ユーザーの一覧と比較します。 ユーザーの一覧には、内部ユーザー、外部ユーザー、個人アカウントが含まれます。 |

## <a name="custom-alerts"></a>カスタム アラート

次のアラートの種類が表示されます。 

|アラート名|アラート ID|説明|
|----|----|----|
|不審なアクティビティのアラート|ALERT_SUSPICIOUS_ACTIVITY|異常なアクティビティがどの程度疑わしいかに従って不審なアクティビティがスコア付けされます (非アクティブなアカウントが関連するか、 新しい場所からか)。これらの条件がすべて計算され、以下のリスク要因に基づいてリスク スコアが提供されます。 <br>ユーザーは管理者である <br>完全にリモートなユーザー<br>匿名プロキシ<br> セッション全体がログインに失敗した<br>多数のログイン失敗<br>新規 (管理者)<br>IP/ISP/国/ユーザーのユーザー エージェント/テナント<br> IP/ISP/国/(管理者) ユーザーのみが使用するユーザー エージェント<br>しばらくの間で最初の (管理者) ユーザー アクティビティ<br>しばらくの間で始めて実行されたこの特定の管理アクティビティ<br>この特定の管理アクティビティが一般的ではない/これまで実行されたことがない<br>過去にこの IP だけがログインに失敗した<br>あり得ない移動|
|不審なクラウド使用アラート|ALERT_DISCOVERY_ANOMALY_DETECTION|Cloud Discovery の異常検出は、通常の動作のパターンを検出し、普通ではない方法で使用されたユーザーまたはアプリを発見します。 |
|アクティビティ ポリシー違反|ALERT_CABINET_EVENT_MATCH_AUDIT|このアラートを使うと、ポリシー一致が検出されたことを把握できます。|
|ファイル ポリシー違反|ALERT_CABINET_EVENT_MATCH_FILE|このアラートを使うと、ポリシー一致が検出されたことを把握できます。|
|プロキシ ポリシー違反|ALERT_CABINET_INLINE_EVENT_MATCH|このアラートを使うと、ポリシー一致が検出されたことを把握できます。|
|フィールド ポリシー違反|ALERT_CABINET_EVENT_MATCH_OBJECT|このアラートを使うと、ポリシー一致が検出されたことを把握できます。|
|新しいサービスの検出|ALERT_CABINET_DISCOVERY_NEW_SERVICE|新しいアプリが検出されました。|
|個人アカウントの使用|ALERT_PERSONAL_USER_SAGE|ファイル共有およびユーザー名に基づいて、検出エンジンは個人アカウントを検索します。 |

## <a name="next-steps"></a>次の手順 

[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
