---
title: "Cloud App Security でアラートを使用する | Microsoft ドキュメント"
description: "このトピックでは、すべてのアラートの一覧を示して説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/12/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: f118a3bf-1663-46ba-884f-b1b03a84ab66
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b3d0aacdef885ba89638628b6d485ef81c3b26f3
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2017
---
# <a name="alerts"></a>アラート
アラートを表示するには:

Cloud App Security ポータルで [アラート] をクリックします。


![[アラート] メニュー](./media/alert-menu.png)


次のアラートの種類が表示されます。 

## <a name="built-in-alerts"></a>組み込みアラート

|アラート名|アラート ID|説明|
|----|----|----|
|新しい場所|ALERT_GEOLOCATION_NEW_COUNTRY|スキャン開始以降に新しい場所が検出されました (6 か月)。 これは、組織全体で国ごとに 1 回のみ表示されます。 |
|新しい管理ユーザー|ALERT_ADMIN_USER|特定のアプリに対して新しい管理者が検出されました。これは、あるアプリケーションの管理者が別のアプリケーションの管理者になった可能性があります。 このアラートは特定の管理者の種類に関するものなので、管理者の種類が変わるたびに表示されます。 ユーザーが管理者権限が失ってから再び権限を得ると、このアラートが表示されます。|
|非アクティブなアカウント|ALERT_ZOMBIE_USER|ユーザーが 1 つのアプリケーションについて 60 日間非アクティブになっている場合、たとえば、Box ではアクティブであっても G Suite を 60 日間使用していない場合、そのユーザーは G Suite について非アクティブであると見なされます。 そのようなユーザーにはタグが追加されるので、非アクティブなアカウントを検索できます。|
|予期しない管理の場所|ALERT_NEW_ADMIN_LOCATION|スキャン開始以降に、管理者に対して新しい場所が検出されました (6 か月)。 これは、組織全体のすべての管理者について国ごとに 1 回のみ表示されます。 |
|危険な状態のアカウント|ALERT_COMPROMISED_ACCOUNT|アプリケーションで侵害が発生し、侵害されたアカウントの一覧が発行された場合、Cloud App Security は一覧をダウンロードして、ユーザー (内部ユーザー、外部ユーザー、個人アカウント) の一覧と比較します。 |

## <a name="custom-alerts"></a>カスタム アラート

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

## <a name="see-also"></a>参照  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  