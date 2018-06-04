---
title: Cloud App Security ポータルへの管理アクセス権を管理する | Microsoft Docs
description: ここでは、管理者用の Cloud App Security ポータルへのアクセス権を設定する手順について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/30/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b718edad-350c-4d90-b045-92529d701dc5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 1d7d73fcc4dd31874613cb0e31e21b1bb21060db
ms.sourcegitcommit: af8fad9709171b200699ca1ed513e2831826ed7e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34568392"
---
*適用対象: Microsoft Cloud App Security*


## <a name="managing-admin-access"></a>管理アクセス許可の管理

Microsoft Cloud App Security はロール ベースのアクセス制御に対応しています。 既定では、Office 365 と Azure AD の次の管理者ロールで Microsoft Cloud App Security にアクセスできます。

- 全体管理者とセキュリティ管理者: **フル アクセス**権を持つ管理者は、Cloud App Security で管理者の追加、ポリシーと設定の追加、ログのアップロード、ガバナンス アクションを実行するフル アクセス許可を持っています。

- コンプライアンス管理者: 読み取り専用アクセス許可を持ち、アラートを管理できます。 ファイル ポリシーを作成し、変更できます。ファイル ガバナンス アクションを許可できます。[データ管理] で、組み込みレポートをすべて表示できます。 

- セキュリティ閲覧者: 読み取り専用アクセス許可を持ち、アラートを管理できます。 セキュリティ閲覧者は、以下の機能を実行できません。

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

- アプリ/インスタンス管理者: ここで選択した特定のアプリまたはアプリのインスタンスのみを扱う Microsoft Cloud App Security のすべてのデータに対するアクセス許可があります。 たとえば、Box European インスタンスに対する管理者アクセス許可をユーザーに与えた場合、管理者は次のように、ファイル、アクティビティ、ポリシー、アラートのいずれの場合も、このアプリ インスタンスに関連するデータのみを表示できます。
- 
  - アクティビティ ページ - タグ付きのエンティティに関するアクティビティのみ
  - アラート - 特定のアプリに関連するアラートのみ
  - ポリシー - すべてのポリシーを表示でき、アプリ/インスタンスのみを扱うポリシーのみを編集または作成できます。
  - アカウント - 特定のアプリ/インスタンスのアカウントのみ
  - アプリのアクセス許可 - 特定のアプリ/インスタンスのアクセス許可のみ
  - ファイル ページ - 特定のアプリ/インスタンスからのファイルのみ
  - Conditional Access App Control - アクセス許可なし
  - Cloud Discovery アクティビティ - アクセス許可なし
  - セキュリティ拡張機能 - ユーザー アクセス許可を持つ API トークンのアクセス許可のみ
  - ガバナンス アクション - 特定のアプリ/インスタンスの場合のみ 

詳細については、「[Azure Active Directory での管理者ロールの割り当て](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-assign-admin-roles)」を参照してください。

Azure Active Directory 管理者ロールにユーザーを追加せずに、Cloud App Security に管理者を追加することもできます。次の手順を実行します。

1. 設定の歯車アイコン ![設定アイコン](./media/settings-icon.png "設定アイコン") をクリックし、**[管理者の管理]** をクリックします。 

2. プラス記号をクリックして、Cloud App Security へのアクセス権を付与する管理者を追加します。
  
  ![管理者の追加](./media/add-admin.png)
    
3. 次に、ドロップダウンをクリックして、管理者のロールの種類 (**グローバル管理者**、**セキュリティ閲覧者**、**コンプライアンス管理者**、**アプリ/インスタンス管理者**) を設定します。**アプリ/インスタンス管理者**を選択した場合は、アクセス許可を与える管理者のアプリとインスタンスを選びます。

     >[!NOTE]
      >アクセスが制限されている管理者が制限されているページにアクセスしたり、制限されている操作を実行しようとしたりすると、そのページへのアクセスまたは操作の実行のアクセス許可がないというエラーが表示されます。
4. **[管理者の追加]** をクリックします。  

   >[!NOTE]
    >全体管理者かセキュリティ管理者だけが Cloud App Security へのアクセスを他のユーザーに与えることができます。
  
**管理者のアクセス許可を上書きするには:**

Azure Active Directory または Office 365 の管理者のアクセス許可を上書きするには、手動で Cloud App Security にユーザーを追加し、ユーザーにアクセス許可を割り当てます。
たとえば、Azure Active Directory でセキュリティ閲覧者である佐藤さんに、Cloud App Security では**フル アクセス**権を付与するには、手動で佐藤さんを Cloud App Security に追加し、**フル アクセス**を割り当てて元のロールを上書きして、Cloud App Security で目的のアクセス許可を持たせることができます。 


Cloud App Security に管理者を追加するには:
1. 設定の歯車アイコン ![設定アイコン](./media/settings-icon.png "設定アイコン")をクリックし、**[管理者アクセス権を管理します]** をクリックします。 

2. Cloud App Security へのアクセス権を付与する管理者を追加します。 ユーザーのアクセス レベルを選択し、**[閉じる]** をクリックします。

## <a name="see-also"></a>参照  
[Cloud Discovery のセットアップ](set-up-cloud-discovery.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  