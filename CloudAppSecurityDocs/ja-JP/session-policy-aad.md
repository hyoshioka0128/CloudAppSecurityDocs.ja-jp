---
title: ユーザー セッション アクティビティを詳細に可視化し、ダウンロードをブロックするためのセッション ポリシーを作成する | Microsoft Docs
description: このトピックでは、リバース プロキシ機能を使用して、ユーザー セッション アクティビティを詳細に可視化し、ダウンロードをブロックするように Cloud App Security の Conditional Access App Control セッション ポリシーを設定する手順について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/25/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 745df28a-654c-4abf-9c90-203841169f90
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7ae1fa26f818fa652570dc6752028c3addbd3b2a
ms.sourcegitcommit: c5dbeb75e409518feaa26200e9a02c59accc8dcc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
*適用対象: Microsoft Cloud App Security*

# <a name="session-policies"></a>セッション ポリシー 

> [!NOTE]
> これはプレビュー機能です。

Microsoft Cloud App Security のセッション ポリシーを使うと、セッション レベルでのリアルタイム監視が可能になり、クラウド アプリの詳細な情報を把握し、ユーザー セッションに設定したポリシーに応じて異なるアクションを実行できます。 セッション制御では、[アクセスを完全に許可またはブロックする](access-policy-aad.md)のではなく、Conditional Access App Control のリバース プロキシ機能を使用して、セッションを監視しながらアクセスを許可したり、特定のセッション アクティビティを制限したりできます。 

たとえば、デバイスが管理されていない場合やセッションが特定の場所から行われている場合に、アプリにアクセスすることをユーザーに許可しながら、機密ファイルのダウンロードを制限したり、特定のドキュメントがダウンロード時に保護されることを要求したりすることができます。 セッション ポリシーを使用すると、このようなユーザー セッション制御を設定し、アクセスを許可することができます。これにより、ユーザーは次の操作を行うことができます。

- [すべてのアクティビティを監視する](#monitor-session)
- [すべてのダウンロードをスキャンする](#block-download)
- [特定のアクティビティをブロックする](#block-activities)
- [ダウンロード時にファイルを保護する](#protect-download)
 

## <a name="prerequisites-to-using-session-policies"></a>セッション ポリシーを使うための前提条件

- Azure AD Premium P2 のライセンス
- 関連するアプリを [Conditional Access App Control と共にデプロイ](proxy-deployment-aad.md)する必要があります。
- 以下の説明のとおり、Microsoft Cloud App Security にユーザーをリダイレクトする [Azure AD 条件付きアクセス ポリシー](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)を設定する必要があります。

> [!NOTE]
> - セッション ポリシーは、プライベート プレビューの Azure AD 以外の ID プロバイダーで構成されたアプリにも対応しています。 プライベート プレビューに関する詳細については、mcaspreview@microsoft.com に電子メールをお送りください。

## <a name="create-an-azure-ad-conditional-access-policy"></a>Azure AD 条件付きアクセス ポリシーを作成する

Azure Active Directory の条件付きアクセス ポリシーと Cloud App Security のセッション ポリシーは連携して動作し、各ユーザー セッションを調べて、各アプリに関するポリシーの決定を行います。 Azure AD で条件付きアクセス ポリシーを設定するには、次の手順のようにします。

1. ユーザーまたはユーザー グループに対する割り当てと、Conditional Access App Control で制御する SAML アプリを指定して、[Azure AD 条件付きアクセス ポリシー](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)を構成します。 

   > [!NOTE]
   > このポリシーが適用されるのは、[Conditional Access App Control と共にデプロイ](proxy-deployment-aad.md)されたアプリだけです。

2. **[セッション]** ブレードで **[Use Conditional Access App Control enforced restrictions]\(Conditional Access App Control によって適用される制限を使用する\)** を選んで、Microsoft Cloud App Security にユーザーをルーティングします。

   ![Conditional Access App Control で制限する Azure AD 条件付きアクセス](./media/proxy-deploy-restrictions-aad.png)

## <a name="create-a-cloud-app-security-session-policy"></a>Cloud App Security セッション ポリシーを作成する 

新しいセッション ポリシーを作成するには、以下の手順を実行します。

1. ポータルで、**[制御]**、**[ポリシー]** の順に選びます。
2. **[ポリシー]** ページで、**[ポリシーの作成]** をクリックし、**[セッション ポリシー]** を選びます。  

   ![セッション ポリシーを作成する](./media/create-session-policy.png)

3. **[セッション ポリシー]** ウィンドウで、ポリシーの名前を割り当てます (例: "*マーケティング ユーザー用 Box の機密ドキュメントのダウンロードをブロックする*")。

   ![新しいセッション ポリシー](./media/new-session-policy.png)

4. **[セッション制御の種類]** フィールドで次のようにします。 

   1. ユーザーによるアクティビティを監視するだけの場合は、**[監視のみ]** を選びます。 これで監視のみのポリシーが作成され、選択したアプリについて、すべてのサインイン、発見的ダウンロード、アクティビティの種類がダウンロードされます。

   2. ユーザーのアクティビティを監視し、ユーザーのダウンロードのブロックや保護などの追加アクションを実行する場合は、**[ファイル ダウンロードの制御 (DLP 使用)]** を選びます。

      ![セッション ポリシー制御の種類](./media/session-policy-control-type.png)
   
   3. **[アクティビティのブロック]** を選択して、**[アクティビティの種類]** フィルターを使用して選択する特定のアクティビティをブロックします。 選択したアプリのすべてのアクティビティが監視されます (さらにアクティビティ ログで報告されます)。 選択した特定のアクティビティがブロックされるのは、**[ブロック]** アクションを選択した場合です。選択した特定のアクティビティからアラートが生成されるのは、**[テスト]** アクションを選択してアラートをオンにした場合のみです。

1. **[次のすべてに一致するアクティビティ]** セクションの **[アクティビティ ソース]** で、ポリシーに適用する追加のアクティビティ フィルターを選びます。 次のオプションを指定できます。 

   - **[デバイス タグ]**: 管理されていないデバイスを識別するには、このフィルターを使います。

   - **[場所]**: 不明な (したがって危険な) 場所を識別するには、このフィルターを使います。 

   - **[IP アドレス]**: IP アドレスでフィルター処理するか、前に割り当てた IP アドレス タグを使うには、このフィルターを使います。 

   - **[ユーザー エージェント タグ]**: モバイル アプリまたはデスクトップ アプリを識別するためにヒューリスティックを有効にするには、このフィルターを使います。 このフィルターは、**ネイティブ クライアント**と等しくなるように、または等しくならないように設定でき、各クラウド アプリについてモバイル アプリとデスクトップ アプリに対してテストする必要があります。
         
       ![ネイティブ クライアントのサポート](./media/user-agent-tag.png)

     >[!NOTE]
     >セッション ポリシーは、モバイル アプリとデスクトップ アプリをサポートしていません。 セッション ポリシーがモバイル アプリとデスクトップ アプリの機能に干渉しないことをテストして確認してください。 必要な場合は、モバイル アプリとデスクトップ アプリをセッション ポリシーから除外します。

     ![セッション ポリシーのアクティビティ ソース](./media/session-policy-activity-filters.png)

6. **[ファイル ダウンロードの制御 (DLP 使用)]** オプションを選んだ場合:

   1. **[次のすべてに一致するファイル]** セクションの **[アクティビティ ソース]** で、ポリシーに適用する追加のファイル フィルターを選びます。 次のオプションを指定できます。

      - **[分類ラベル]**: 組織が Azure Information Protection を使っていて、データがその分類ラベルで保護されている場合は、このフィルターを使います。 適用した分類ラベルに基づいてファイルをフィルター処理できます。 Cloud App Security と Azure Information Protection の統合について詳しくは、「[Azure Information Protection の統合](azip-integration.md)」をご覧ください。

      - **[ファイル名]**: 特定のファイルにポリシーを適用するには、このフィルターを使います。

      - **[ファイルの種類]**: 特定のファイルの種類にポリシーを適用するには、このフィルターを使います (すべての .xls ファイルのダウンロードをブロックする場合など)。

        ![セッション ポリシーのファイル フィルター](./media/session-policy-file-filters.png)

        
   2. **[コンテンツ検査]** セクションで、DLP エンジンによるドキュメントとファイルのコンテンツのスキャンを有効にするかどうかを設定します。
 
      ![セッション ポリシーのコンテンツ検査](./media/session-policy-content-inspection.png)

   3. **[アクション]** ウィンドウで、次のいずれかを選びます。 

      - **[テスト]**(すべてのアクティビティを監視する): 設定したポリシー フィルターに従ってダウンロードを明示的に許可するには、このアクションを設定します。

      - **[ブロック]**(ファイルのダウンロードをブロックし、すべてのアクティビティを監視します): 設定したポリシー フィルターに従ってダウンロードを明示的にブロックするには、このアクションを設定します。 詳しくは、「[ダウンロードのブロックのしくみ](#block-download)」をご覧ください。

      - **[保護]**(ダウンロードしたファイルに分類ラベルを適用し、すべてのアクティビティを監視します): これを選択できるのは、**[セッション ポリシー]** の下で **[ファイル ダウンロードの制御 (DLP 使用)]** を選択した場合のみです。 組織が Azure Information Protection を使っている場合は、Azure Information Protection で設定されている分類ラベルをファイルに適用するように **[アクション]** を設定できます。 詳しくは、「[ダウンロードの保護のしくみ](#protect-download)」をご覧ください。

        ![セッション ポリシーのアクション](./media/session-policy-actions.png)

7. **一致するイベントごとにポリシー重要度に応じたアラートを作成**し、アラート制限を設定して、アラートをメールとテキスト メッセージのどちらか一方または両方にするかどうかを選ぶことができます。

   ![セッション ポリシーのアラート](./media/session-policy-alert.png)


## すべてのアクティビティを監視する <a name="monitor-session"></a>

セッション ポリシーを作成すると、ポリシーに一致する各ユーザー セッションは、直接アプリにではなく、セッション制御にリダイレクトされます。 ユーザーには、セッションが監視されていることを知らせる監視通知が表示されます。

   ![セッション監視のしくみ](./media/session-monitoring-notice.png)

監視されていることをユーザーに通知したくない場合は、通知メッセージを無効にすることができます。

1. 設定の歯車アイコンで、**[全般設定]** を選びます。 

2. 次に、Conditional Access App Control の設定で、**ユーザーへの通知**チェック ボックスをオフにします。

    ![セッション監視通知を無効にする](./media/disable-session-monitoring-notice.png)

セッション内でユーザーを保持するために、Conditional Access App Control は、アプリ セッション内の関連するすべての URL、Java スクリプト、Cookie を、Microsoft Cloud App Security の URL に置き換えます。 たとえば、ドメインが myapp.com で終わるリンクを含むページをアプリが返した場合、Conditional Access App Control はそのリンクを、myapp.com.us.cas.ms などで終わるドメインに置き換えます。 これにより、セッション全体が Microsoft Cloud App Security によって監視されます。

Conditional Access App Control は、ルーティングされてきたすべてのユーザー セッションのトラフィック ログを記録します。 トラフィック ログには、時刻、IP、ユーザー エージェント、アクセスした URL、アップロードおよびダウンロードされたバイト数が含まれます。 これらのログが分析されて、**Cloud App Security の Conditional Access App Control** という継続的なレポートが、Cloud Discovery ダッシュボードの Cloud Discovery レポート一覧に追加されます。

![Conditional Access App Control レポート](./media/proxy-report.png)


ログをエクスポートするには:

1. 設定の歯車アイコンに移動し、**[Conditional Access App Control]** をクリックします。
2. テーブルの右側にあるエクスポート ボタンをクリックします ![エクスポート ボタン](./media/export-button.png)。 
3. レポートの範囲を選び、**[エクスポート]** をクリックします。 この処理には時間がかかる場合があります。

エクスポートされたログをダウンロードするには:

1. レポートの準備ができたら、**[調査]**、**[カスタム レポート]** の順に移動します。
2. テーブルで、**Conditional Access App Control トラフィック ログ**の一覧から関連するレポートを選んで、ダウンロード ![ダウンロード ボタン](./media/download-button.png) をクリックします。 


## すべてのダウンロードをブロックする <a name="block-download"></a>

Cloud App Security セッション ポリシーで実行する **[アクション]** として **[ブロック]** が設定されていると、Conditional Access App Control はポリシーのファイル フィルターに従ってユーザーがファイルをダウンロードできないようにします。 ダウンロード イベントは各 SAML アプリの Microsoft Cloud App Security によって認識され、ユーザーがこのイベントを開始すると、Conditional Access App Control はリアルタイムで介入して実行を防ぎます。 ユーザーがダウンロードを開始したことを示す信号を受け取った Conditional Access App Control は、**ダウンロードが制限されている**というメッセージをユーザーに返し、ダウンロードされるファイルを、ユーザーに対するカスタマイズ可能なメッセージを含むテキスト ファイルに置き換えます。これは、セッション ポリシーから構成できます。  

## 特定のアクティビティをブロックする <a name="block-activities"></a>

**[アクティビティの種類]** として **[アクティビティのブロック]** が設定されているとき、特定のアプリ内でブロックする特定のアクティビティを選択できます。 選択したアプリのすべてのアクティビティが監視されます (さらにアクティビティ ログで報告されます)。選択した特定のアクティビティがブロックされるのは、**[ブロック]** アクションを選択した場合です。選択した特定のアクティビティからアラートが生成されるのは、**[テスト]** アクションを選択してアラートをオンにした場合のみです。

## ダウンロード時にファイルを保護する <a name="protect-download"></a>
**[アクティビティのブロック]** を選択して、**[アクティビティの種類]** フィルターを使用して選択する特定のアクティビティをブロックします。 選択したアプリのすべてのアクティビティが監視されます (さらにアクティビティ ログで報告されます)。 選択した特定のアクティビティがブロックされるのは、**[ブロック]** アクションを選択した場合です。選択した特定のアクティビティからアラートが生成されるのは、**[テスト]** アクションを選択してアラートをオンにした場合のみです。
Cloud App Security のセッション ポリシーで実行する **[アクション]** として **[保護]** が設定されていると、Conditional Access App Control はポリシーのファイル フィルターに従って、ファイルのラベル付けとその後の保護を適用します。 ラベルは Azure の Azure Information Protection コンソールで構成され、Cloud App Security ポリシーのオプションとしてラベルが表示されるためには、ラベル内で **[保護]** が選ばれている必要があります。 ラベルが選ばれていて、Cloud App Security ポリシーの条件 (ラベル) に一致するファイルがダウンロードされると、アクセス許可がある対応する保護が、ダウンロード時にファイルに適用されます。 元のファイルはクラウド アプリ内にそのまま残っていますが、ダウンロードされるファイルは保護されています。 ファイルにアクセスしようとするユーザーは、適用された保護によって決定されるアクセス許可要件を満たす必要があります。  
 
 
## <a name="see-also"></a>参照  
[Azure AD の Conditional Access App Control 機能を使って管理されていないデバイスでのダウンロードをブロックする](use-case-proxy-block-session-aad.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  