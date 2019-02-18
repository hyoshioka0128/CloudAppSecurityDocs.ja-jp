---
title: Cloud App Security ポータルへの管理アクセス権を管理する
description: この記事では、管理者用の Cloud App Security ポータルへのアクセス権を設定する手順について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 1/27/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b718edad-350c-4d90-b045-92529d701dc5
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 90cc081f33b30ac3b4774c7292752d1c27dddd0c
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2019
ms.locfileid: "56281232"
---
# <a name="manage-admin-access"></a>管理者アクセスの管理

*適用対象:Microsoft Cloud App Security*

Microsoft Cloud App Security はロール ベースのアクセス制御に対応しています。 この記事では、管理者用の Cloud App Security ポータルへのアクセス権を設定する手順について説明します。 管理者ロールの割り当ての詳細については、[Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles) と [Office 365 ](https://docs.microsoft.com/office365/admin/add-users/assign-admin-roles) に関する記事を参照してください。

## <a name="office-365-and-azure-ad-roles-with-access-to-cloud-app-security"></a>Cloud App Security にアクセスできる Office 365 と Azure AD のロール

既定では、Office 365 と [Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) の次の管理者ロールで Microsoft Cloud App Security にアクセスできます。

- **グローバル管理者とセキュリティ管理者:** **フル アクセス**が可能な管理者には Cloud App Security の完全なアクセス許可があります。 このようなユーザーは管理者の追加、ポリシーと設定の追加、ログのアップロード、ガバナンス アクションの実行ができます。

- **コンプライアンス管理者:** 読み取り専用アクセス許可を持ち、アラートを管理できます。 ファイル ポリシーを作成し、変更できます。ファイル ガバナンス アクションを許可できます。[データ管理] で、組み込みレポートをすべて表示できます。 

- **セキュリティ閲覧者:** 読み取り専用アクセス許可を持ち、アラートを管理できます。 セキュリティ閲覧者は、以下のアクションの実行が制限されています。

  - ポリシーを作成する、または既存のポリシーを編集および変更する 
  - ガバナンス アクションを実行する 
  - 探索ログをアップロードする
  - サードパーティ アプリの禁止または承認
  - IP アドレス範囲設定ページへのアクセスと表示
  - すべての設定ページへのアクセスと表示 
  - 探索設定へのアクセスと表示 
  - アプリ コネクタ ページへのアクセスと表示
  - ガバナンス ログへのアクセスと表示 
  - [スナップショット レポートの管理] ページへのアクセスと表示 

- **アプリ/インスタンス管理者:** 選択した特定のアプリまたはアプリのインスタンスを排他的に扱う Microsoft Cloud App Security のすべてのデータに対するアクセス許可があります。 たとえば、Box European インスタンスへの管理者アクセス許可をユーザーに付与します。 管理者には、ファイル、アクティビティ、ポリシー、アラートのいずれかを問わず、Box European インスタンスに関連するデータのみが表示されます。

  - アクティビティ ページ - 特定のアプリに関するアクティビティのみ
  - アラート - 特定のアプリに関連するアラートのみ
  - ポリシー - すべてのポリシーを表示でき、アプリ/インスタンスを排他的に扱うポリシーのみ編集または作成が可能
  - アカウント ページ - 特定のアプリ/インスタンスのアカウントのみ
  - アプリのアクセス許可 - 特定のアプリ/インスタンスのアクセス許可のみ
  - ファイル ページ - 特定のアプリ/インスタンスからのファイルのみ
  - Conditional Access App Control - アクセス許可なし
  - Cloud Discovery アクティビティ - アクセス許可なし
  - セキュリティ拡張機能 - ユーザー アクセス許可を持つ API トークンのアクセス許可のみ
  - ガバナンス アクション - 特定のアプリ/インスタンスの場合のみ 

- **グループ管理者:** ここで選択した特定のグループを排他的に扱う、Microsoft Cloud App Security のすべてのデータに対するアクセス許可があります。 たとえば、グループ "ドイツ - すべてのユーザー" に対する管理者のアクセス許可をユーザーに与えた場合、管理者は、そのユーザー グループの Microsoft Cloud App Security での情報を表示したり変更したりできます。

  - アクティビティ ページ - グループのユーザーに関するアクティビティのみ
  - アラート - グループのユーザーに関連するアラートのみ
  - ポリシー - すべてのポリシーを表示でき、グループのユーザーを排他的に扱うポリシーのみ編集または作成が可能
  - アカウント ページ - グループ内の特定のユーザーのアカウントのみ
  - アプリのアクセス許可 – アクセス許可がありません
  - ファイル ページ – アクセス許可がありません
  - Conditional Access App Control - アクセス許可なし
  - Cloud Discovery アクティビティ - アクセス許可なし
  - セキュリティ拡張機能 - グループのユーザーを含む API トークンのアクセス許可のみ
  - ガバナンス アクション - グループの特定のユーザーの場合のみ

- **グローバル検出管理者:** すべての Cloud Discovery の設定およびデータを表示および編集できます。 グローバル検出管理者には、次のアクセス許可があります。

  - 設定 -  
     -  システム設定 - 表示のみ
     - Cloud Discovery 設定 - すべて表示および編集可能 (匿名化のアクセス許可は、ロール割り当て時に許可されたかどうかに依存する)
  - Cloud Discovery アクティビティ - フル アクセス許可
  - アラート - Cloud Discovery データに関連するアラートのみ
  - ポリシー - すべてのポリシーの表示が可能、Cloud Discovery ポリシーのみ編集または作成が可能
  - アクティビティ ページ - アクセス許可なし
  - アカウント ページ - アクセス許可なし
  - アプリのアクセス許可 – アクセス許可がありません
  - ファイル ページ – アクセス許可がありません
  - Conditional Access App Control - アクセス許可なし
  - セキュリティ拡張機能 - アクセス許可なし
  - ガバナンス アクション - Cloud Discovery 関連のアクションのみ

## <a name="override-admin-permissions"></a>管理者のアクセス許可をオーバーライドする

Azure Active Directory または Office 365 の管理者のアクセス許可をオーバーライドするには、手動で Cloud App Security にユーザーを追加し、ユーザーにアクセス許可を割り当てます。
たとえば、Azure Active Directory でセキュリティ閲覧者である佐藤さんに、Cloud App Security では**フル アクセス**権を付与するには、手動で佐藤さんを Cloud App Security に追加し、**フル アクセス**を割り当てて元のロールをオーバーライドして、Cloud App Security で必要なアクセス許可を持たせることができます。 

## <a name="add-additional-admins"></a>他の管理者を追加する

Azure Active Directory 管理者ロールにユーザーを追加せずに、Cloud App Security に管理者を追加することができます。 管理者をさらに追加するには、次の手順を実行します。

   >[!IMPORTANT]
   > 全体管理者かセキュリティ管理者だけが Cloud App Security へのアクセスを他のユーザーに与えることができます。


1. 設定の歯車アイコン ![設定アイコン](./media/settings-icon.png "設定アイコン")をクリックし、**[管理者アクセス権を管理します]** をクリックします。 

2. プラス記号をクリックして、Cloud App Security へのアクセス権を付与する管理者を追加します。 内部または外部のメール アドレスを入力して、組織内部、または外部の Managed Security Service Provider (MSSP) の管理者がセキュリティ アラートを管理できるようにします。
  
   ![管理者の追加](./media/add-admin.png)

3. 次に、ドロップダウンをクリックして、管理者のロールの種類 (**グローバル管理者**、**セキュリティ閲覧者**、**コンプライアンス管理者**、**アプリ/インスタンス管理者**) を設定します。**アプリ/インスタンス管理者**を選択した場合は、アクセス許可を与える管理者のアプリとインスタンスを選びます。

     >[!NOTE]
      >アクセスが制限されている管理者が制限されているページにアクセスしたり、制限されている操作を実行しようとしたりすると、そのページへのアクセスまたは操作の実行のアクセス許可がないというエラーが表示されます。

4. **[管理者の追加]** をクリックします。  

## <a name="invite-external-admins"></a>外部管理者を招待する

Microsoft Cloud App Security では、Microsoft Cloud App Security ポータルの管理者として外部の Managed Security Service Provider (MSSP) を招待することができます。 外部ユーザーを管理者として構成し、Microsoft Cloud App Security で使用できるロールのいずれかを割り当てられるようになりました。 さらに、MSSP が複数の顧客テナント間でサービスを提供できるように、複数のテナントへのアクセス権を持つ管理者がポータル内で簡単にテナントを切り替えられるようになりました。 

テナントを切り替えるには、複数のテナントへのアクセス許可を取得してから、ユーザー アイコンをクリックします。 これで、アクセス許可があるテナントのリストが表示されます。 管理するテナントを選択します。

![テナントの選択](./media/choose-tenant.png "テナントの選択")

## <a name="next-steps"></a>次の手順  
[Cloud Discovery のセットアップ](set-up-cloud-discovery.md)   
  
  
  
