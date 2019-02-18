---
title: Cloud App Security で接続されているアプリからユーザー グループをインポートする
description: この記事では、接続されているアプリから Cloud App Security にユーザー グループをインポートする方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 12/14/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 87b831ef-5977-4df8-bed3-3ee54a8adbb5
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fb823e9aa13df6710ee3d07ced6b6db97d442eb0
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2019
ms.locfileid: "56282224"
---
# <a name="importing-user-groups-from-connected-apps"></a>接続されているアプリからユーザー グループをインポートする

*適用対象:Microsoft Cloud App Security*

API コネクタを使用してアプリを接続するとき、Microsoft Cloud App Security を使用し、たとえば、Office 365 や Azure Active Directory からユーザー グループをインポートできます。
2 種類のユーザー グループがあります。 
- 自動グループ </br>既定で自動グループが Microsoft Cloud App Security により作成されます。 たとえば、**External** という名前の自動ユーザー グループがあります。このグループは、組織にとって部外者にあたるすべてのユーザーがすべてのアプリから集められて作られ、ファイルへのアクセスが許可されます。あるいは、テナントのユーザー アクティビティに関与したユーザーのグループです。
 次の自動グループが Cloud App Security に存在します。
  - 外部リンク
  - Dropbox 管理者
  - Office 365 管理者
  - G Suite 管理者
  - Box 管理者
  - すべての Salesforce 標準/カスタム プロファイル (Salesforce システム管理者など)。 完全一覧は[ここ](https://help.salesforce.com/articleView?id=standard_profiles.htm&language=en&type=0)でご覧いただけます。

- インポートされたグループ</br>接続されているアプリからグループをインポートできます。 たとえば、Office 365 (Active Directory) とその他の接続されているアプリからユーザー グループをインポートできます。 組織全体や特定のユーザーを見なくても、特定のグループを見ることで組織内の脅威を探すことができます。 

インポートされたユーザー グループを使用する一般的なシナリオは次のとおりです。
   - HR の人が見ているドキュメントを調べる
   - 経営グループ内で異常なことが発生しているかどうかを確認する
   - 管理者グループの誰かが米国外でアクティビティを実行したかどうかを探す。 

## <a name="how-to-import-user-groups"></a>ユーザー グループをインポートする方法

1. メニュー バーで設定アイコン ![設定アイコン](./media/settings-icon.png "設定アイコン") をクリックし、**[ユーザー グループ]** を選択します。
2. **[ユーザー グループのインポート]** をクリックします。

   ![ユーザー グループのインポート](./media/user-groups-add.png)

3. ユーザー グループのインポート元にするアプリを選択します。 アプリの一覧は、展開したアプリ コネクタによって変わります。
4. インポートするグループを選択します。 利用できるグループの一覧は、アプリ自体のすべての既存ユーザー グループの一覧になります。 新しいグループを追加する場合、アプリ自体でそれを直接追加する必要があります。 その後、グループがここのリストに表示されたら、それを選択します。
5. グループのサイズによっては、インポートに最大 1 時間かかることがあります。 インポート プロセスがかんりょうしたときにメールで通知するオプションを選択できます。
6. クリックして **インポート**します。 グループをインポートすると、Cloud App Security は Active Directory Connect と同様にグループ メンバーを自動同期します。
7. インポートが完了すると、**[ユーザー グループ]** ページから、特定のグループをクリックし、グループのすべてのメンバーの一覧を表示できます。 グループのメンバーをクリックして、特定のアカウントの詳細にドリルダウンします。 ユーザーやユーザーのアクティビティのグラフなど、ユーザーが使用しているアプリや、アカウントの概要を見ることができます。

グループをインポートすると、**[アクティビティ ログ]** で調査したり、ポリシーを作成したりするときのフィルターとしてグループを選択できます。 

> [!NOTE]
> - あるユーザー グループのインポート後に実行されたアクティビティにのみ、そのユーザー グループのメンバーにより実行されているというタグが付けられます。
> - 初回の同期後は、1 時間ごとにグループが更新されます。

ユーザー グループ フィルターの使用方法については、「[アクティビティ](activity-filters.md)」を参照してください。


## <a name="next-steps"></a>次の手順
 
[Cloud Discovery のセットアップ](set-up-cloud-discovery.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
  
