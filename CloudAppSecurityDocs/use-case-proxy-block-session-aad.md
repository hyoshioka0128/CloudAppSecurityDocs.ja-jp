---
title: "Cloud App Security プロキシを使用して管理されていないデバイスへの機密データのダウンロードをブロックする方法 | Microsoft Docs"
description: "このトピックでは、Azure AD のプロキシ機能を使用して管理されていないデバイスによる機密データのダウンロードから組織を守るためのシナリオについて説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 06238ebc-2088-4372-9412-96cceaf3b145
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c84cadea48fb131c4602cbaa5377827236764690
ms.sourcegitcommit: 3bc510959e66a29d474cbef412deac0daefa8a24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="blocking-downloads-of-sensitive-information-using-the-microsoft-cloud-app-security-proxy"></a>Microsoft Cloud App Security プロキシを使用する機密情報のダウンロードのブロック

> [!NOTE]
> Microsoft Cloud App Security プロキシ機能のロールアウトが開始されました。

現在の IT 管理者は板挟みになっています。従業員が生産性を高められるようにする必要があります。 これは、従業員が任意のデバイスからいつでも作業できるようにアプリへのアクセスを許可することを意味します。 その一方で、会社の資産を守らなければなりません。それには所有財産や特権アクセス情報などが含まれます。 従業員にクラウド アプリへのアクセスを許可しつつ、データを保護するにはどうすればよいでしょうか。 **このユース ケースを使用すれば、管理されていないデバイスや社外ネットワークの場所からエンタープライズ クラウド アプリの機密データにアクセスできるユーザーによるダウンロードをブロックできます。**


## <a name="the-threat"></a>脅威
組織のアカウント マネージャーが週末、自宅で自分のノート PC から Salesforce の情報を確認します。 Salesforce データには、顧客のクレジット カード情報や個人情報が含まれている可能性があります。 自宅の PC は管理されていません。つまり、このマネージャーが Salesforce のドキュメントを PC にダウンロードすると、マルウェアに感染するおそれがあります。あるいは、PC を紛失したり、盗まれたりした場合、パスワードで保護されていなければ、機密情報が誰にでも見られてしまいます。 

## <a name="the-solution"></a>解決策
Azure AD の条件付きアクセスと Cloud App Security プロキシを使用して、クラウド アプリの使用を監視し制御することにより、組織を保護します。  

## <a name="prerequisites"></a>前提条件

- Azure AD Premium P2 の有効なライセンス
- Azure AD で SSO のクラウド アプリを構成する  
- [アプリが Cloud App Security にデプロイされている](proxy-deployment-aad.md)ことを確認する

## <a name="create-a-block-download-policy-for-unmanaged-devices"></a>管理されていないデバイスに対するダウンロードのブロック ポリシーを作成する  

Cloud App Security セッション ポリシーでは、デバイス状態に基づいてセッションをさらに制限できます。 条件として、そのデバイスを使用してセッションを制御する場合は、条件付きアクセス ポリシーとセッション ポリシーの両方を作成して実行する必要があります。  

### <a name="step-1-create-an-azure-ad-conditional-access-policy"></a>手順 1: Azure AD の条件付きアクセス ポリシーを作成する

1. 割り当て済みユーザーとアプリを使用して、Azure AD の条件付きアクセス ポリシーを作成します。
2. 条件付きアクセス ポリシー内のセッション制御で **[プロキシによって適用される制限を使用する]** を選択します。   

 ![Azure AD の条件付きアクセス](./media/proxy-deploy-restrictions-aad.png)

このタスクが完了したら、Cloud App Security ポータルに進み、セッションでのファイルのダウンロードを監視して制御するセッション ポリシーを作成します。

### <a name="step-2-create-a-session-policy"></a>手順 2: セッション ポリシーを作成する

1. Cloud App Security ポータルで、**[制御]**、**[ポリシー]** の順に選択します。 

2. **[ポリシー]** ページで、**[ポリシーの作成]**、**[セッション ポリシー]** の順にクリックします。
 
 ![セッション ポリシーを作成する](./media/create-session-policy.png)

2. **[セッション ポリシーの作成]** ページで、ポリシーの名前と説明を指定します。 たとえば、**管理されていないデバイスに対して Salesforce からのダウンロードをブロックする**などと指定します。

3. **[ポリシー重要度]** と **[カテゴリ]** を割り当てます。

 ![新しいセッション ポリシー](./media/new-session-policy.png)

4. **[セッション制御の種類]** で、**[Monitor all activities and control file download]\(すべての活動を監視し、ファイルのダウンロードを制御する\)** を選択します。 これで、Salesforce セッション内でユーザーが行うあらゆる活動を監視し、ダウンロードをリアルタイムでブロックしたり、保護したりできます。

 ![セッション ポリシー制御の種類](./media/session-policy-control-type.png)

5.  **[次のすべてに一致する活動]** セクションの **[アクティビティ ソース]** で、次のフィルターを選択します。 
    
    - **[デバイス タグ]**: **[次の値に等しくない]** を選択してから、管理対象デバイスを識別するために組織で使用されている方法に応じて、**[準拠]**、**[ドメイン参加済み]**、または **[有効なクライアント証明書]** を選択します。 
    
    - **[アプリ]**: 制御対象のアプリを選択します。  

    - **[ユーザー]**: 監視対象のユーザーを選択します。  
    
7. または、企業ネットワークに含まれない場所でのダウンロードをブロックする場合は、**[次のすべてに一致する活動]** セクションの **[アクティビティ ソース]** で、次のフィルターを設定します。 

  - **[IP アドレス]** または **[場所]**: これら 2 つのパラメーターのいずれかを使用することで、ユーザーが機密データにアクセスしようしている可能性のある、会社以外または不明な場所を識別することができます。

     > [!NOTE]
     > 管理されていないデバイスと会社以外の場所の両方からのダウンロードをブロックする場合は、2 つのセッション ポリシーを作成する必要があります。その 1 つでは、場所を使用して **[アクティビティ ソース]** を設定し、もう 1 つでは、**[アクティビティ ソース]** を管理されていないデバイスに設定します。
 
   - **[アプリ]**: 制御対象のアプリを選択します。    
   
   - **[ユーザー]**: 監視対象のユーザーを選択します。  

6. **[次のすべてに一致するファイル]** セクションの **[アクティビティ ソース]** で、次のフィルターを設定します。 
   
    - **[分類ラベル]**: Azure Information Protection 分類ラベルを使用して、特定の Azure Information Protection 分類ラベルに基づいてファイルをフィルター処理する場合。
   
    - **[ファイル名]** または **[ファイルの種類]** を選択し、選択内容に基づいて制限を適用します。
 
     ![セッション ポリシーのファイル フィルター](./media/session-policy-file-filters.png)

7. **[コンテンツ検査]** を有効にし、内部 DLP でファイルをスキャンし、機密性の高いコンテンツがないかを確認できるようにします。 

 ![セッション ポリシーのコンテンツ検査](./media/session-policy-content-inspection.png)

8. **[アクション]** で、**[ブロック]** を選択します。 ユーザーがファイルをダウンロードできない場合に表示するブロック メッセージをカスタマイズします。  

 ![セッション ポリシーのアクション](./media/session-policy-actions.png)

9. ポリシーに一致したときに受け取るアラートを設定します。 アラートが大量に発生しすぎないように上限を設定できます。また、アラートの形式としてメール メッセージまたはテキスト メッセージ、あるいはその両方を選択できます。

 ![セッション ポリシー アラート](./media/session-policy-alert.png)


10. **[作成]** をクリックします。  
 

## <a name="validate-your-policy"></a>ポリシーの検証 

1. 管理されていないデバイスまたは会社以外のネットワークの場所からブロックされているファイルのダウンロードをシミュレートするには、アプリにログインし、ファイルのダウンロードを試します。 

2. ファイルはブロックされ、**[ブロック メッセージのカスタマイズ]** で設定したメッセージが表示されます。 

  ![ダウンロードのブロック メッセージ](./media/block-download-message.png)

3. Cloud App Security ポータルで、**[制御]**、**[ポリシー]** の順にクリックし、作成したポリシーをクリックしてポリシー レポートを表示します。 セッション ポリシーの一致がすぐに表示されます。 
 
  ![セッション ポリシー レポート](./media/session-policy-report.png)

4. ポリシー レポートでは、セッション制御のプロキシにリダイレクトされたログインと、監視対象セッションからダウンロードまたはブロックされたファイルを確認することができます。

  
## <a name="see-also"></a>参照  
[セッション ポリシーを作成する](session-policy-aad.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  