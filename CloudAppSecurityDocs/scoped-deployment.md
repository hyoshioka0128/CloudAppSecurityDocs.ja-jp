---
title: Microsoft Cloud App Security のデプロイのスコープを指定する
description: この記事では、Cloud App Security のデプロイのスコープを指定して、特定のユーザーやグループを含めたり除外したりする方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: fe2ce27b-1020-45e9-ad72-fad93d197169
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e3ca7c6bf16eec51f684e42c8964628ee5aa7ad0
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2019
ms.locfileid: "56281785"
---
# スコープ付きデプロイ <a name="scoped-deployment"></a> 

*適用対象:Microsoft Cloud App Security*

Microsoft Cloud App Security を使用するとデプロイのスコープを指定できます。 スコープを指定することで、アプリについて監視する特定のユーザー グループを選択したり、監視から除外したりできます。

## <a name="include-or-exclude-user-groups"></a>ユーザー グループを追加または除外する

組織内のすべてのユーザーに向けて Microsoft Cloud App Security を使用する必要がない場合があります。 スコープ指定は、ライセンス制約に起因して展開を制限する場合に特に役立ちます。 また、特定の国のユーザーを監視しないことを要求するコンプライアンスのために制限が必要になることもあります。 たとえば、展開時にスコープを指定し、米国に居住する従業員のみを監視します。 あるいは、ドイツに居住するユーザーにアクティビティを見せないようにすることができます。

- デプロイのスコープを指定するには、最初に Microsoft Cloud App Security に[ユーザー グループをインポートする](user-groups.md)必要があります。 既定では、次のグループが表示されます。
    - **アプリケーション** ユーザー グループ - Office 365 アプリケーションと Azure AD アプリケーションによって実行されるアクティビティの表示を可能にする組み込みのグループ。
    - **外部ユーザー** グループ - 組織に設定した [IP アドレス範囲](ip-tags.md)内にないすべてのユーザー。
- 包含ルールを設定すると、包含されるグループのうちに入らないすべてのグループが自動的に除外されます。 たとえば、米国オフィス グループのすべてのメンバーを含めるルールを設定すると、そのグループの一部でないグループは監視されません。
- 除外されるユーザー グループは、含まれるユーザー グループをオーバーライドします。 つまり、"英国従業員" というユーザー グループを包含して、"マーケティング" を除外した場合、英国のマーケティング メンバーは、**英国従業員**グループのメンバーであっても監視されません。

1. メニュー バーで設定歯車をクリックし、**[スコープ付きの展開]** を選択します。  

    ![設定アイコン](./media/settings-icon.png "設定アイコン")

2. デプロイのスコープを指定して特定のグループを包含または除外するためには、最初に Microsoft Cloud App Security に[ユーザー グループをインポートする](user-groups.md)必要があります。 

3. Microsoft Cloud App Security で特定のグループを監視するように設定するには、**[含める]** タブでプラス アイコンをクリックします。 
    ![アイコン](./media/plus-icon.png)

4. **[新しい包含ルールの作成]** ダイアログ ボックスで、次の手順を行います。

    1. **[Type rule name]\(ルール名を入力してください\)** の下に、ルールの内容を表す名前を入力します。
    2. **[ユーザー グループの選択]** の下で、Cloud App Security で監視するグループをすべて選択します。
    3. このルールを、接続されたすべてのアプリに適用するのか、**特定のアプリ**にのみ適用するのか選択します。 **特定のアプリ**を選択した場合、ルールが影響を及ぼすのは、選択したアプリの監視に対してのみです。 たとえば、グループに **[UI チーム ユーザー]** と **[ボックス]** を選択した場合、Cloud App Security は UI チーム ユーザー グループのボックス アクティビティのみを監視し、その他のすべてのアプリの場合は、Cloud App Security はすべてのユーザーのすべてのアクティビティを監視します。
     
        ![包含ルール](./media/include-rule.png)

5. 特定のグループを監視から除外するよう設定するには、**[含まない]** タブでプラス アイコンをクリックします。 
    
   ![アイコン](./media/plus-icon.png)

6. **[新しい除外ルールの作成]** ダイアログ ボックスで、次のパラメーターを設定します。

    1. **[Type rule name]\(ルール名を入力してください\)** の下に、ルールの内容を表す名前を入力します。
    **[ユーザー グループの選択]** の下で、Cloud App Security に監視させないグループをすべて選択します。
    2. このルールを、接続されたすべてのアプリに適用するのか、**特定のアプリ**にのみ適用するのか選択します。 **特定のアプリ**を選択した場合、Cloud App Security は選択したアプリに対してのみ選択したグループの監視を停止します。 つまり、グループに **[UI チーム ユーザー]** と **[Active Directory]** を選択した場合、Cloud App Security は、UI チーム ユーザーが実行する Active Directory のアクティビティを除いて、すべてのユーザー アクティビティを監視します。
    
       ![除外ルール](./media/exclude-rule.png)

## <a name="example-results-for-include-and-exclude-rules"></a>包含ルールと除外ルールの結果例

作成した包含ルールと除外ルールが共に働いて、Microsoft Cloud App Security によって実行される全体の監視のスコープが指定されます。 作成できる包含ルールと除外ルールの例と、これらのルールを実行した後で最終的に Microsoft Cloud App Security が監視する対象を、ここに示します。

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

## <a name="next-steps"></a>次の手順  
[Cloud Discovery のセットアップ](set-up-cloud-discovery.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
  
