---
title: Microsoft Cloud App Security のデプロイのスコープを指定する | Microsoft Docs
description: この記事では、Cloud App Security のデプロイのスコープを指定して、特定のユーザーやグループを含めたり除外したりする方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/30/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: fe2ce27b-1020-45e9-ad72-fad93d197169
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4e97155b07dfc1e7f360eb798961406c36f85003
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143753"
---
*適用対象: Microsoft Cloud App Security*


# スコープ付きデプロイ <a name="scoped-deployment"></a> 

Microsoft Cloud App Security を使用すると、デプロイのスコープを指定して、特定のユーザー グループのみを監視したり、特定のユーザー グループを監視から除外したりできます。

組織内のすべてのユーザーに向けて Microsoft Cloud App Security を使用する必要がない場合があります。 これは、ライセンスの制限や、特定の国のユーザーを監視しないよう要求するコンプライアンス規定などにより、デプロイを制限する必要がある場合に特に便利です。 スコープ付きデプロイを使用すると、たとえば、米国を拠点とする従業員のみを監視したり、またはドイツを拠点とするユーザーに対するすべてのアクティビティを表示しないようにしたりできます。 

- デプロイのスコープを指定するには、最初に Microsoft Cloud App Security に[ユーザー グループをインポートする](user-groups.md)必要があります。 既定で表示されるのは、**[アプリケーション]** ユーザー グループ (Office 365 と Azure AD のアプリケーションによって実行されるアクティビティを表示する、組み込みのグループ) と、**[外部ユーザー]** グループ (組織用に設定した [IP アドレスの範囲](ip-tags.md)に含まれないユーザーをすべて統合するグループ) です。
- 包含ルールを設定すると、包含されるグループのうちに入らないすべてのグループが自動的に除外されます。 たとえば、米国オフィス グループのすべてのメンバーを含めるルールを設定すると、そのグループの一部でないグループは監視されません。
- 除外されるユーザー グループは、含まれるユーザー グループをオーバーライドします。 つまり、"英国従業員" というユーザー グループを包含して、"マーケティング" を除外した場合、英国のマーケティング メンバーは、**英国従業員**グループのメンバーであっても監視されません。

1. メニュー バーで設定アイコン ![設定アイコン](./media/settings-icon.png "設定アイコン") をクリックし、**[Scoped deployment]\(スコープ付きデプロイ\)** を選択します。  

2. デプロイのスコープを指定して特定のグループを包含または除外するためには、最初に Microsoft Cloud App Security に[ユーザー グループをインポートする](user-groups.md)必要があります。 

3. Microsoft Cloud App Security で特定のグループを監視するように設定するには、**[含める]** タブでプラス ![アイコン](./media/plus-icon.png) をクリックします。 <br>**[Create new include rule]\(新しい包含ルールの作成\)** ダイアログ ボックスで、次の操作を行います。

    1. **[Type rule name]\(ルール名を入力してください\)** の下に、ルールの内容を表す名前を入力します。
    2. **[ユーザー グループの選択]** の下で、Cloud App Security で監視するグループをすべて選択します。
    3. このルールを、接続されたすべてのアプリに適用するのか、**特定のアプリ**にのみ適用するのか選択します。 **特定のアプリ**を選択した場合、ルールが影響を及ぼすのは、選択したアプリの監視に対してのみです。 つまり、グループ**英国ユーザー**と**ボックス**を選択した場合、Cloud App Security は英国のユーザーのボックス アクティビティのみを監視し、その他のすべてのアプリの場合は、Cloud App Security はすべてのユーザーのすべてのアクティビティを監視します。
     
     ![包含ルール](./media/include-rule.png)

4. 特定のグループを監視から除外するよう設定するには、**[含まない]** タブでプラス ![アイコン](./media/plus-icon.png) をクリックします。 <br>**[新しい除外ルールの作成]** ダイアログ ボックスで、次のパラメーターを設定します。

    1. **[Type rule name]\(ルール名を入力してください\)** の下に、ルールの内容を表す名前を入力します。
    **[ユーザー グループの選択]** の下で、Cloud App Security に監視させないグループをすべて選択します。
    2. このルールを、接続されたすべてのアプリに適用するのか、**特定のアプリ**にのみ適用するのか選択します。 **特定のアプリ**を選択した場合、Cloud App Security は選択したアプリに対してのみ選択したグループの監視を停止します。 つまり、グループ**ドイツのユーザー**と **Active Directory** を選択した場合、Cloud App Security は、ドイツのユーザーが実行する Active Directory のアクティビティを除いて、すべてのユーザー アクティビティを監視します。
    
    ![除外ルール](./media/exclude-rule.png)

作成した包含ルールと除外ルールが共に働いて、Microsoft Cloud App Security によって実行される全体の監視のスコープが指定されます。

作成できる包含ルールと除外ルールの例と、これらのルールを実行した後で最終的に Microsoft Cloud App Security が監視する対象を、ここに示します。

次のルールを作成するとします。

- "ドイツのすべてのユーザー" というユーザー グループを除外
- Office 365 のアクティビティに対してのみ "グローバル営業" というユーザー グループを含める
- Power BI のアクティビティに対してのみ "営業部長" というユーザー グループを含める
- Salesforce を Microsoft Cloud App Security に接続し、それに対するルールを設定しない

次のユーザー アクティビティが監視されます。

|User|グループのメンバーシップ|監視されるアクティビティ|
|----|----|----|
|Adriana|ドイツのすべてのユーザー<br>グローバル営業<br>営業部長|None|
|Alain|グローバル営業|Office 365 と Power BI を除くすべてのサブ アプリ|
|Cornel|グローバル営業<br>営業部長|Office 365 とすべてのサブ アプリ|
|Raymond|営業部長|Power BI のみ|

> [!NOTE] 
> このルールで、他のアプリがグループのスコープによる影響を受けることはありません。
> 例では、Salesforce の場合、すべてのユーザー グループのすべてのアクティビティが監視されます。

  
    
## <a name="see-also"></a>参照  
[Cloud Discovery のセットアップ](set-up-cloud-discovery.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  
