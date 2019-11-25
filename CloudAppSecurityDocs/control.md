---
title: Cloud App Security でガバナンス アクションを使用する方法
description: この記事では、組織のクラウド アプリの使用を制御するため Cloud App Security で実施できるガバナンス アクションについて説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: bc11bbfe-ec6c-458c-8302-8112c383199d
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d6c535c0ae8abb280265d5ae2f9b5c92fe462905
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460906"
---
# <a name="control"></a>Control

*適用対象: Microsoft Cloud App Security*

ガバナンス アクションは、クラウド環境全体のユーザーのファイルに適用できます。 クラウドについて十分に調査して理解したら、ガバナンス アクションを使用して組織の保護に役立てることができます。  

## <a name="use-policies-to-assess-risk"></a>ポリシーを使用してリスクを評価  
発生中のアラートを確認した後は、ポリシー センターに移動して、アラートをトリガーしないポリシー違反を確認します。  

-   Cloud App Security ダッシュボードで **[制御]** 、 **[ポリシー]** の順にクリックします。  

-   特定のポリシーを選択して、アラートをトリガーしていないポリシーの一致の **[現在一致しています]** リストを確認します。  

-   違反を 1 つずつクリックし、それぞれの処理を決定します。 ガバナンス アクションの詳細については、以下の図を参照してください。  

     コンプライアンス違反を見つけるようにポリシーが設定されていて、誰かがクレジット カード番号を OneDrive 上のファイルに保存する場合、ポリシーに一致します。  

     ![PCI matches](./media/pci-matches.png "pci 一致")  

-   一致を選択して、ポリシーに違反しているファイルを参照します。  

     ![PCI content matches](./media/pci-content-matches.png "pci コンテンツ一致")  

     ファイル自体を選択すると、そのファイルに関する情報を取得できます。  

     **[グループ作業者]** をクリックすると、そのファイルにアクセスできるユーザーが表示されます。  

     **[一致]** をクリックすると、実際のクレジット カード番号が表示されます。  

     ![Content matches credit card numbers](./media/content-matches-ccn.png "content matches credit card numbers")  

## <a name="apply-governance-actions"></a>ガバナンス アクションの適用  
ガバナンス アクションは、ポリシー内、アラート内、**ファイル** ログから適用できます。  

**[設定]** 歯車アイコンで **[ガバナンス ログ]** を選択すると、以前に適用されたすべてのガバナンス アクションの状態をいつでも表示して確認することができます。 ![settings icon](./media/settings-icon.png "settings icon")

ガバナンス アクションが失敗した場合は、 **[再試行]** を選択して再度適用できます。 ![Retry icon](./media/retry-icon.png "retry icon")   

ポリシー、違反、アプリの種類に応じて、さまざまなガバナンス アクションを使用できます。  

## <a name="move-from-detection-to-automatic-remediation"></a>検出から自動修復への移行  
ポリシー フィルターを定義してカスタマイズすると、ポリシー違反が発生するたびに実行される自動ガバナンス アクションを選択できます。  
修復アクションではクラウド プロバイダーの API を利用するため、アプリごとにアクションが異なる場合があります。  

> [!NOTE]  
>  ガバナンス アクションを設定する場合には十分に注意してください。 ファイルへのアクセス許可が失われ、元に戻せなくなる可能性があります。  
> 複数の検索フィールドを使用して、ポリシーを実行する対象ファイルのみが表示されるようにフィルター条件を絞り込むことをお勧めします。 フィルター条件を絞り込むほど、適切な結果が得られます。  
>   
>  **[フィルター]** セクションの **[結果の編集とプレビュー]** ボタンを使用すると結果を確認できます。  

![File policy edit and preview results](./media/file-policy-edit-and-preview-results.png "ファイル ポリシーの編集とプレビュー結果")  

## <a name="migration"></a>移行  
Cloud App Security では、組織内のどのユーザーがどのアプリを使用しているかを把握できると共に、新しいアプリの導入を監視するツールを提供することで、移行のロールアウトをサポートします。 また、組織内でどのような種類のアプリを提供する必要があるかを理解できるように、すべてのユーザーが既に使用しているアプリを表示するツールが提供されます。  

### <a name="migrate-your-users-to-a-new-app"></a>新しいアプリにユーザーを移行する  
たとえば、最近になって Office 365 を購入し、組織内のすべてのユーザーに他のクラウド ストレージ アプリの使用を停止して、代わりに OneDrive を使用してほしいと考えているとします。 この場合、以下の操作を実行できます。  

1. **Cloud Discovery ダッシュボード**に移動して、 **[アプリのカテゴリ]** から **[クラウド ストレージ]** でアプリをフィルター処理します。 **[ユーザー]** または **[IP アドレス]** 別に結果を並べ替え、最も多く使用されているアプリを確認します。  

2. 他のアプリを使用しているユーザーを確認することができます。 また、それらのアプリにドリルダウンして、以下の手順で、そのアプリのユーザーに対して OneDrive に移行するように通知することもできます。

   1. **Cloud Discovery ダッシュボード**で **[Dropbox]** を選び、 **[IP アドレス]** または **[ユーザー]** タブを選びます。  

   2. **[エクスポート]** 矢印アイコンを選択して、エクスポートのオプションを選択します。 ![Arrow icon](./media/arrow-icon.png "arrow icon")

### <a name="find-more-secure-alternatives"></a>安全な代替アプリの検索  
Cloud App Security サービス カタログを使用すると、ユーザーが使用している危険なアプリの代わりに、組織に最適な代替アプリを検索できます。  

たとえば、生産性ツールの購入を検討しているものの、ユーザーがそのツールを活用するかどうか確信できないとします。  

1.   **Cloud Discovery ダッシュボード**に移動します。  

2.   **[カテゴリ]** から **[生産性]** によってアプリをフィルタリングします。  

3.   使用中の各アプリについて、 **[スコア]** をチェックして、アプリが安全であるかどうかを確認し、安全でない場合はその理由を確認します。  

4.   組織全体のエンタープライズ ライセンスを購入しようと考えている場合は、 **[ユーザー]** 列もチェックしてください。 この列では、決定を行う前に、現在最も多くのユーザーが使用しているアプリ、そのアプリの信頼性、そのアプリに備わっているセキュリティ機能を確認することができます。  

## <a name="next-steps"></a>次のステップ
クラウド アプリの使用を制御するポリシーを設定する方法については、「[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)」を参照してください。   

[!INCLUDE [Open support ticket](includes/support.md)]  
