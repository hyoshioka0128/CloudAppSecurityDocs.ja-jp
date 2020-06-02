---
title: Microsoft Cloud App Security のデプロイのスコープを指定する
description: この記事では、Cloud App Security のデプロイのスコープを指定して、特定のユーザーやグループを含めたり除外したりする方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 05/27/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 6cfc4421569a59c49c9a980af3ce2e0876d90bce
ms.sourcegitcommit: 6886d285601955f0efc7acf980c9d4740ff873fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2020
ms.locfileid: "84253819"
---
# <a name="activity-privacy"></a>活動のプライバシー

*適用対象:Microsoft Cloud App Security*

Microsoft Cloud App Security により、企業は、グループのメンバーシップに基づいて監視するユーザーを細かく決定できます。 アクティビティのプライバシーは、ユーザーのプライバシーを侵害することなく、組織のコンプライアンス規制に従う機能を追加します。 これは、アクティビティログでアクティビティを非表示にすることによって、ユーザーのプライバシーを維持しながらユーザーを監視できるようにすることで実現されます。 承認された管理者のみが、これらのプライベートアクティビティを表示するオプションを選択できます。各インスタンスは、ガバナンスログで監査されます。

## <a name="configure-activity-privacy-user-groups"></a>活動プライバシーユーザーグループを構成する

監視対象の Cloud App Security にユーザーがいる場合がありますが、コンプライアンスに関する規制により、その操作を可能にするユーザーを制限する必要があります。 アクティビティのプライバシーを使用すると、既定では、活動を非表示にするユーザーグループを定義できます。

ユーザーのプライバシーグループを構成するには、最初に[ユーザーグループ](user-groups.md)を Cloud App Security にインポートする必要があります。 既定では、次のグループが表示されます。

- **アプリケーション** ユーザー グループ - Office 365 アプリケーションと Azure AD アプリケーションによって実行されるアクティビティの表示を可能にする組み込みのグループ。

- **External users** group-組織用に構成した管理対象ドメインのメンバーではないすべてのユーザー。

1. メニューバーで [設定] 歯車をクリックし、[スコープされた**デプロイとプライバシー**] を選択します。

    ![設定アイコン](media/settings-icon.png)

1. Cloud App Security によって監視される特定のグループを設定するには、[**アクティビティのプライバシー** ] タブで、プラスアイコンをクリックします。
    ![icon](media/plus-icon.png)

1. [**ユーザーグループの追加**] ダイアログボックスの [**ユーザーグループの選択**] で、Cloud App Security にプライベートにするすべてのグループを選択し、[**追加**] をクリックします。

    ![[ユーザーグループの追加] ダイアログボックスのスクリーンショット](media/activity-privacy-add-user-groups.png)

    > [!NOTE]
    > ユーザーグループが追加されると、そのグループのユーザーによって実行されるすべてのアクティビティが、以降はプライベートになります。 既存の活動は影響を受けません。

## <a name="assign-admins-permission-to-view-private-activities"></a>管理者のアクセス許可を割り当ててプライベートアクティビティを表示する

1. メニューバーで [設定] 歯車をクリックし、[**管理者アクセスの管理**] を選択します。

    ![設定アイコン](media/settings-icon.png)

1. 特定の管理者にプライベート活動を表示するアクセス許可を付与するには、[**アクティビティのプライバシーアクセス許可**] タブでプラスアイコンをクリックします。
    ![icon](media/plus-icon.png)

1. [**管理者のアクセス許可の追加**] ダイアログで、管理者の UPN または電子メールアドレスを入力し、[**アクセス許可の追加**] をクリックします。

    ![[管理者権限の追加] ダイアログボックスが表示されたスクリーンショット](media/activity-privacy-add-admin-permission.png)

    > [!NOTE]
    > プライベートアクティビティを表示するアクセス許可を割り当てることができるのは、管理者のみです。

## <a name="viewing-private-activities"></a>プライベートアクティビティの表示

管理者には、プライベートアクティビティを表示するための適切なアクセス許可が付与された後、アクティビティログでこれらのアクティビティを表示するかどうかを選択するオプションがあります。

### <a name="to-view-private-activities"></a>プライベートアクティビティを表示するには

1. [**アクティビティログ**] ページで、アクティビティテーブルの右側にある [設定] アイコンをクリックし、[**プライベートアクティビティの表示**] を選択します。

    ![[アクティビティログの設定] アイコンを示すスクリーンショット](media/activity-privacy-view-settings-icon.png)

1. [**プライベートアクティビティの表示**] ダイアログで、[ **OK** ] をクリックして、アクションが監査されていることを理解していることを確認します。 確認が完了すると、プライベートアクティビティがアクティビティログに表示され、アクションがガバナンスログに記録されます。

[!INCLUDE [Open support ticket](includes/support.md)]
