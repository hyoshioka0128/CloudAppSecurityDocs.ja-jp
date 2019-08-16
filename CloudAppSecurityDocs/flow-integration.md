---
title: Flow と Cloud App Security を統合して、カスタム アラート オートメーションを取得する
description: この記事では、Flow と Cloud App Security を統合することでカスタム アラート オートメーションを取得する方法について説明します。
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: shsagir
ms.date: 6/18/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 344f92e2-6b3b-46db-bfd0-3b1016e0bc34
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 251eec930864bc5baee4b0c7922f5abc8429e867
ms.sourcegitcommit: 12dfc4c0b8d72aad8cfae9c70f0014ca312b9e4e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037406"
---
# <a name="integrate-with-flow-for-custom-alert-automation"></a>カスタムアラート自動化のフローとの統合

*適用対象: Microsoft Cloud App Security*

Cloud App Security は [Microsoft Flow](https://docs.microsoft.com/flow/getting-started) と統合して、カスタム アラート オートメーションとオーケストレーション プレイブックを提供します。 Microsoft Flow で使用可能な[コネクタのエコシステム](https://docs.microsoft.com/connectors/)を使用することで、Cloud App Security がアラートを生成するときに、プレイブックのトリガーを自動化することができます。 たとえば、[ServiceNow コネクタ](https://docs.microsoft.com/connectors/service-now/)を使用してチケット発行システムで問題を自動的に作成したり、Cloud App Security でアラートがトリガーされたときに、カスタム ガバナンス アクションを実行するための承認メールを送信します。  

## <a name="prerequisites"></a>前提条件 

 - 有効な [Microsoft Flow プラン](https://flow.microsoft.com/pricing)が必要

## <a name="how-it-works"></a>しくみ

Cloud App Security 単体で、ポリシーを定義するときに、ユーザーの停止やファイルを非公開にするなどの定義済みのガバナンス オプションを提供します。 Cloud App Security コネクタを使用して Microsoft Flow でプレイブックを作成すると、ワークフローを作成してポリシー用にカスタマイズしたガバナンス オプションを有効にすることができます。 Flow でプレイブックが作成されたら、それを Cloud App Security でポリシーと関連付けて、アラートを Flow に送信するだけです。 Microsoft Flow では、組織用にカスタマイズされたワークフローを作成するために複数のコネクタと条件が用意されています。 

フロー内の[Cloud App Security コネクタ](https://docs.microsoft.com/connectors/cloudappsecurity/)は、自動トリガーとアクションをサポートしています。 Flow は Cloud App Security がアラートを生成するときに自動的にトリガーされます。 アクションには、Cloud App Security でのアラートの状態の変更が含まれます。 

## <a name="how-to-create-playbooks-with-microsoft-flow"></a>Microsoft Flow でプレイブックを作成する方法

1. Cloud App Security で [API トークンを作成](api-tokens.md)します。 

2. [Microsoft Flow ポータル](https://flow.microsoft.com)にアクセスして、[ **[Create a new flow from scratch]\(新しいフローを最初から作成する\)** ](https://docs.microsoft.com/flow/get-started-logic-flow) を選択します。 

3. 検索コネクタとトリガーに、「**Cloud App Security**」を入力して、 **[When an alert is generated]\(アラートの生成時\)** を選択します。

   ![アラート生成時のフロー](./media/flow-when-alert.png)

4. **[認証設定]** の下に、手順 1 の API トークンを貼り付けます。 

5. Cloud App Security でポリシーがアラートを生成するときにトリガーされる必要があるワークフローを定義します。 アクション、論理条件を追加し、スイッチ ケースの条件、またはループを追加して、プレイブックを保存できます。 

   ![Flow ワークフロー](./media/flow-workflow.png)

6. Cloud App Security ポータルで、 **[ポリシー]** に移動し、Flow に送信するポリシーのアラートの行で、3 つのドットをクリックして、 **[設定]** を選択します。 
7. **[アラート]** の下で、 **[Flow にアラートを送信する]** を選択し、ドロップダウン メニューからプレイブックの名前を選択します。  

   ![Cloud App Security ポータルで Flow を有効にする](./media/flow-mcas-config.png)

8. 作成した、またはアクセスを許可された Cloud App Security プレイブックは、 **[セキュリティ拡張機能]** 画面に表示されます。 

  
   ![Cloud App Security でプレイブックを表示する](./media/flow-extensions.png)
 
 

## <a name="next-steps"></a>次の手順 
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
