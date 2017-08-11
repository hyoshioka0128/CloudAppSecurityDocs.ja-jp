---
title: "Cloud App Security プロキシでのクラウド アプリの使用を制御するポリシーの作成 | Microsoft Docs"
description: "このトピックでは、Cloud App Security プロキシでのクラウド アプリの使用を制御するポリシーを作成する方法について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/16/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b419aff0-3f50-4917-9ee2-9ecf7539a5d7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4544f5b48484f9341bb85d09d8fdc8d11fd4ba00
ms.sourcegitcommit: c5a0d07af558239976ce144c14ae56c81642191b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2017
---
# <a name="controlling-app-use-with-proxy-control"></a>プロキシ制御でのアプリの使用の制御

プロキシをデプロイした後は、望ましくないアクセスや動作をブロックするポリシーを作成することにより、組織のクラウドでのアクセスとセッションを制御できます。

## <a name="create-access-control-policies-in-cloud-app-security"></a>Cloud App Security でアクセス制御ポリシーを作成する

アクセス制御ポリシーを作成するには:

1.  **[制御]** の **[ポリシー]** を選びます。

2.  **[ポリシーの作成]** で **[プロキシ ポリシー]** を選び、**[アクティビティの種類]** として **[シングル サインオン ログオン]** を選びます。

3.  その後、関連するアプリとフィルターを選び、適切な軽減オプションを選びます。

>[!NOTE]
> フィルターでは、**[デバイス タグ]** を選び、**[管理されたデバイス]** と等しく、または等しくなく、設定できます。 [管理されたデバイス](#_Managed_devices)について詳しくは、後の説明をご覧ください。

また、**[Mitigating actions]\(軽減するアクション\)** では、**[ログ]** または **[アクセスのブロック]** を選ぶか、**[Cloud App Security にルーティング]** を選んでセッションでポリシーを監視および作成することができます。 これについては、「[Creating session control policies in Cloud App Security](#_Creating_session_control)」(Cloud App Security でセッション制御ポリシーを作成する) でさらに説明します。

## <a name="create-session-control-policies-in-cloud-app-security"></a>Cloud App Security でセッション制御ポリシーを作成する 

プロキシをデプロイした後は、Cloud App Security ポータルでセッションのポリシーを定義することにより、セッション制御機能を追加できます。

組織全体にデプロイする前に、少数のユーザー グループでセッション制御を有効にして始めることをお勧めします。 さらに、すべてのセッションまたは大部分のセッションについてセッション制御を有効にすることはお勧めしません。 セッション制御は制限のあるエージェントレスのデプロイに基づいているため、ユーザーが制限のある、または制御できないデバイスおよびアプリを使っている場合を対象に設計されています。

セッション制御ポリシーを作成するには:

1.  [アクセス ポリシー](#working-with-proxy-control-features)を作成した後、軽減するアクションとして **[Cloud App Security にルーティング]** を選びます。

2.  **[制御]** で **[ポリシー]** に移動し、**[ポリシーの作成]** で **[プロキシ ポリシー]** を選びます。

3.  **[アクティビティの種類]** として **[ファイルのダウンロード]** または **[レポートのエクスポート]** を選びます。 関連するアプリとフィルターを選び、必要に応じて軽減を選びます。

## <a name="enabling-managedunmanaged-device-control"></a>管理された/管理されていないデバイスの制御の有効化

### <a name="step-1-deploy-certificates"></a>ステップ 1: 証明書をデプロイする

クラウドに接続しているデバイスが管理されているかいないかを Cloud App Security が識別するには、クライアント証明書をデプロイする必要があります。 これはさまざまな方法で実行できますが、通常は、既存のモバイル デバイス管理ソリューションの証明書を利用するか、または Active Directory のグループ ポリシーを使います。

### <a name="step-2-upload-the-root-certificate-to-cloud-app-security"></a>ステップ 2: Cloud App Security にルート証明書をアップロードする

Cloud App Security ポータルで管理されたデバイスの識別を有効にするには、先に証明機関のルート証明書をアップロードする必要があります。

1.  設定の歯車アイコンをクリックし、**[管理されたデバイス]** を選びます。

2.  **[デバイスの識別]** を有効にします。

3. ルート証明書をアップロードします。

![Cloud App Security プロキシの管理されたデバイスの証明書](./media/managed-device-cert.png)

### <a name="step-3-create-managed-device-policies"></a>ステップ 3: 管理されたデバイスのポリシーを作成する

ルート証明書をアップロードした後、**デバイス タグ**が**管理されたデバイス**と等しいか等しくないかを調べるフィルターを使って、プロキシ ポリシーを作成するか、アクティビティ ログでイベントを検索します。

管理されたデバイスを識別する手段としてクライアント証明書を使う場合は、セッションをブロックまたは監視する前に、監視モードで始めることをお勧めします。 つまり、**[管理されたデバイス]** フィルターでアクセス ポリシーを定義し、軽減するアクションを **[ログのみ]** にします。 ユーザーについての経験が得られた後、アクセスのブロックやセッションの監視などの他の軽減アクションを追加できます。


## <a name="see-also"></a>参照  
[Cloud App Security プロキシの操作](proxy-intro.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  