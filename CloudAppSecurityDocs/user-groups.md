---
title: Cloud App Security で接続されているアプリからユーザー グループをインポートする
description: この記事では、接続されているアプリから Cloud App Security にユーザー グループをインポートする方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 777e672436220642df6ea739c0f2e381487dd9ee
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720363"
---
# <a name="importing-user-groups-from-connected-apps"></a>接続されているアプリからユーザー グループをインポートする

*適用対象: Microsoft Cloud App Security*

API コネクタを使用してアプリを接続するとき、Microsoft Cloud App Security を使用し、たとえば、Office 365 や Azure Active Directory からユーザー グループをインポートできます。 2 種類のユーザー グループがあります。

- 自動グループ  
既定で自動グループが Microsoft Cloud App Security により作成されます。 たとえば、**External** という名前の自動ユーザー グループがあります。このグループは、組織にとって部外者にあたるすべてのユーザーがすべてのアプリから集められて作られ、ファイルへのアクセスが許可されます。あるいは、テナントのユーザー アクティビティに関与したユーザーのグループです。 次の自動グループが Cloud App Security に存在します。

  - 外部リンク
  - Dropbox 管理者
  - Office 365 管理者
  - G Suite 管理者
  - Box 管理者
  - すべての Salesforce 標準/カスタム プロファイル (Salesforce システム管理者など)。 完全一覧は[ここ](https://help.salesforce.com/articleView?id=standard_profiles.htm&language=en&type=0)でご覧いただけます。

- インポートされたグループ  
接続されているアプリからグループをインポートできます。 たとえば、Office 365 (Active Directory) とその他の接続されているアプリからユーザー グループをインポートできます。 組織全体や特定のユーザーを見なくても、特定のグループを見ることで組織内の脅威を探すことができます。

  インポートされたユーザー グループを使用する一般的なシナリオは次のとおりです。

  - HR の人が見ているドキュメントを調べる
  - 経営グループ内で異常なことが発生しているかどうかを確認する
  - 管理者グループの誰かが米国外でアクティビティを実行したかどうかを探す。

## <a name="how-to-import-user-groups"></a>ユーザー グループをインポートする方法

1. メニューバーで、設定アイコン![設定アイコン](media/settings-icon.png "設定アイコン")をクリックし、 **[ユーザーグループ]** を選択します。
1. **[ユーザー グループのインポート]** をクリックします。

    ![ユーザー グループのインポート](media/user-groups-add.png)

1. ユーザー グループのインポート元にするアプリを選択します。 アプリの一覧は、展開したアプリ コネクタによって変わります。
1. インポートするグループを選択します。 利用できるグループの一覧は、アプリ自体のすべての既存ユーザー グループの一覧になります。 新しいグループを追加する場合、アプリ自体でそれを直接追加する必要があります。 その後、グループがここのリストに表示されたら、それを選択します。
1. グループのサイズによっては、インポートに最大 1 時間かかることがあります。 インポート プロセスがかんりょうしたときにメールで通知するオプションを選択できます。
1. クリックして **インポート**します。 グループをインポートすると、Cloud App Security は Active Directory Connect と同様にグループ メンバーを自動同期します。
1. インポートが完了すると、 **[ユーザー グループ]** ページから、特定のグループをクリックし、グループのすべてのメンバーの一覧を表示できます。 グループのメンバーをクリックして、特定のアカウントの詳細にドリルダウンします。 ユーザーやユーザーのアクティビティのグラフなど、ユーザーが使用しているアプリや、アカウントの概要を見ることができます。

グループをインポートすると、 **[アクティビティ ログ]** で調査したり、ポリシーを作成したりするときのフィルターとしてグループを選択できます。

> [!NOTE]
>
> - インポートされたユーザーグループをフィルターで使用できるようになるまで、少し時間がかかる場合があります。
> - あるユーザー グループのインポート後に実行されたアクティビティにのみ、そのユーザー グループのメンバーにより実行されているというタグが付けられます。
> - 初回の同期後は、1 時間ごとにグループが更新されます。

ユーザー グループ フィルターの使用方法については、「[アクティビティ](activity-filters.md)」を参照してください。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Cloud Discovery のセットアップ](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
