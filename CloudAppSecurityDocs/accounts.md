---
title: クラウド アプリのアカウントの表示 - Cloud App Security | Microsoft Docs
description: この記事では、接続されたアプリからのアカウントの確認に関する情報を提供します。
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
ms.assetid: 7811f23b-6100-427f-93b1-44f5f81f6c76
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 35b9bdf9e1b59bfecefe18f5fcaacd4ce6b73edf
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65565878"
---
# <a name="accounts"></a>[アカウント]

*適用対象:Microsoft Cloud App Security*

Microsoft Cloud App Security は、接続されたアプリのアカウントを表示します。 アプリ コネクターを使用して Cloud App Security をアプリに接続すると、Cloud App Security は接続されたアプリに関連付けられたアカウントの情報を読み取ります。 [アカウント] ページでは、アカウント、アクセス許可、アカウントが属しているグループ、エイリアス、および使用アプリを調査することができます。 さらに、接続されたいずれかのアプリ (アクティビティやファイル共有など) で以前は存在しなかった新しいアカウントが Cloud App Security によって検出されると、アカウントはそのアプリのアカウント リストに追加されます。 これにより、クラウド アプリと対話する外部ユーザーのアクティビティを把握できます。

管理者は、特定のユーザーのメタデータまたはユーザーのアクティビティを検索できます。 **[ユーザーとアカウント]** ページでは、接続されているクラウド アプリケーションから取得したエンティティに関する包括的な詳細が提供されます。 また、ユーザーのアクティビティ履歴とユーザーに関連するセキュリティ通知も表示されます。

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]


**[ユーザーとアカウント]** ページをフィルター処理して、特定のアカウントを検索したり、さまざまな種類のアカウントの詳細を確認したりできます。たとえば、過去 1 年間アクセスされていないすべての外部アカウントをフィルター処理して検索することができます。 

**[ユーザーとアカウント]** ページでは、ご利用のアカウントについて次のような問題の調査を簡単に行うことができます。  

-   特定のサービスで長期間非アクティブになっているアカウントがないか (そのユーザーのそのサービス用のライセンスを取り消す必要がないか) を確認します。  
-   管理者のアクセス許可を持つユーザーの一覧をフィルター処理することができます。  

-   既に組織の一員ではなくなったものの、まだアクティブなアカウントを持っているユーザーを検索することができます。  

-   アプリの中断やアカウント設定ページへの移動など、アカウントに対するガバナンス アクションを実行することができます。 ガバナンス アクションの完全なリストについては、[ガバナンス ログ](governance-actions.md)を参照してください。
    
-   各ユーザー グループに含まれているアカウントを確認できます。  

-   各アカウントによってアクセスされているアプリ、特定のアカウントに対して削除されているアプリを確認できます。
    

![アカウントの画面](./media/accounts-page.png)

## <a name="users-and-accounts-filters"></a>ユーザーとアカウントのフィルター
以下は、適用できるアカウント フィルターの一覧です。 ポリシー作成時の強力なツールを提供するために、ほとんどのフィルターでは NOT をはじめとする複数値をサポートしています。  
  
<!--- **Account name**: The account name is the primary alias of the user, but other identifiers from other Microsoft accounts (Office 365 and Azure Active Directory) such as proxy addresses, aliases, SID are supported and consolidated beneath the primary alias. -->

- **所属団体**: 所属団体は、**内部**または**外部**のいずれかです。 "内部" とするユーザーおよびアカウントを設定するには、**[設定]** で、内部組織の**IP アドレス範囲**を必ず設定します。 アカウントに管理者のアクセス許可が割り当てられている場合、[アカウント] テーブル内のアイコンには赤いネクタイが加わります。 ![アカウント管理アイコン](./media/accounts-admin-icon.png)

- **アプリ**: 組織内のアカウントで使用されている API 接続アプリをフィルター処理することができます。

- **ドメイン**: 特定のドメインに属するユーザーをフィルター処理することができます。

- **グループ**: Cloud App Security でユーザー グループ (組み込みのユーザー グループとインポートされたユーザー グループ) のメンバーをフィルター処理することができます。

- **インスタンス**: 特定のアプリ インスタンスのメンバーをフィルター処理することができます。 

- **最終利用日**: **最終利用日**フィルターでは、休止状態にあるアカウント、およびユーザーがアクティビティをしばらく実行していないアカウントを検索することができます。

- **組織**: ご利用の接続されたアプリで定義されている特定の組織グループのメンバーをフィルター処理することができます。

- **管理者のみを表示**: アカウントと管理者であるユーザーがフィルター処理されます。

- **状態**: 該当なし、ステージング、アクティブ、中断、削除済みの各ユーザー アカウント状態に基づいてフィルター処理されます。

- **型**: ユーザーまたはアカウントの種類のいずれかにフィルター処理することができます。

- **ユーザー名**: 特定のユーザーにフィルター処理することができます。 


## <a name="next-steps"></a>次の手順  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しい問題を作成することもできます。](https://premier.microsoft.com/)  
  
  
