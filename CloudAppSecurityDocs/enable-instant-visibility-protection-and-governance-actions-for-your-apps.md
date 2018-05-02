---
title: アプリを Cloud App Security に接続して使用状況を詳細に表示し、管理する | Microsoft Docs
description: このトピックでは、API コネクタを使用して、アプリを組織のクラウド内のアプリに接続するプロセスについて説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3b15ba46-ac9c-4b4f-aefc-137edc903bc1
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b0f009770d16f7d801df637e1ba632cc6f82f1ac
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2018
---
*適用対象: Microsoft Cloud App Security*


# <a name="connect-apps"></a>アプリを接続する 
アプリのコネクタを使用するとアプリ プロバイダーの API を利用できるため、Microsoft Cloud App Security による接続先アプリの表示および制御がしやすくなります。  

Microsoft Cloud App Security はクラウド プロバイダーが提供する API を利用しますが、各サービスには独自のフレームワークと API の制限事項があります。 Microsoft Cloud App Security はサービスを利用して、API の使用を最適化し、最高のパフォーマンスを実現できるようになりました。 サービスが API に加えたさまざまな制限事項 (調整、API の制限、動的なタイムシフト API の期間など) を考慮して、Cloud App Security エンジンでは使用可能な機能が活用されます。 テナント内のすべてのファイルのスキャンなど、一部の処理には大量の API が必要となるため、長時間にわたって実行されます。 ポリシーによっては、数時間または数日間にわたって実行される場合があります。  

## <a name="multi-instance-support"></a>複数インスタンスのサポート

Cloud App Security は接続された同一アプリの複数のインスタンスをサポートします。 たとえば、Salesforce の複数のインスタンスがある場合 (営業用とマーケティング用など)、その両方を Cloud App Security に接続し、詳細にポリシーを作成して調査し、同じコンソールから管理することができます。 このサポートは API 接続アプリにのみ適用され、クラウドで検出されたアプリやプロキシ接続されたアプリには適用されません。

## <a name="how-it-works"></a>しくみ  
Cloud App Security はシステム管理者権限で展開されているため、環境内のすべてのオブジェクトへのフル アクセスができます。  

アプリ コネクタのフローは次のとおりです:
1. Cloud App Security は認証のためのアクセス許可をスキャンして保存します。
2.  Cloud App Security はユーザー リストを要求します。 この処理を初めて実行する場合は、スキャンが完了するまでにいくらか時間がかかることがあります。 ユーザーのスキャンが完了すると、Cloud App Security はアクティビティとファイルに進みます。 スキャンが開始されるとすぐに、いくつかのアクティビティが Cloud App Security で利用できるようになります。 
4. ユーザー リクエストが完了すると、Cloud App Security はユーザー、グループ、アクティビティ、ファイルを定期的にスキャンします。 最初のフル スキャンが完了すると、すべてのアクティビティが利用できるようになります。 

スキャンする必要があるテナントのサイズ、ユーザーの数、ファイルのサイズと数によっては、フル スキャンが完了するまでにいくらか時間がかかる場合があります。 

接続先のアプリケーションによって (以下の表を参照)、API 接続を使用すると次を行うことができます。  

-   **アカウント情報:**  

     ユーザー、アカウント、プロファイル情報、状態 (中断、アクティブ、無効) グループ、および特権を表示できます。  

-   **監査証跡:**  

     ユーザー アクティビティ、管理者アクティビティ、ログオン アクティビティを表示できます。  

-   **データ スキャン:**  

     2 つのプロセスを使用した非構造化データを、定期的 (12 時間ごと) およびリアルタイム (変更が検出されるたびに開始) にスキャンできます。  

-   **アプリのアクセス許可:**  

     発行済みトークンとそのアクセス許可を表示できます。  

-   **アカウント ガバナンス:**  

     ユーザーによる使用の中断やパスワードの取り消しなどを行います。  

-   **データ ガバナンス:**  

     ごみ箱のファイルを含むファイルの検疫やファイルの上書きを行います。  

-   **アプリのアクセス許可のガバナンス:**  

     トークンを削除します。  

次の表は、クラウド アプリごとの、アプリのコネクタによって使用できるようになる機能のリストです。  

> [!div class="mx-tableFixed"]
> 
> ||**Office 365**|**Box**|**Okta**|**G Suite**|**Service Now**|**Salesforce**|**Dropbox**|**AWS**|  
> |-|-|-|-|-|-|-|-|-|  
> |**アカウントの一覧表示**|✔|✔|✔|✔|✔|✔|✔|✔|  
> |**グループ**|✔|✔|✔|✔|✔|✔|✔|✔|  
> |**権限**|✔|✔|プロバイダーはサポートしていません|✔|✔|✔|✔||  
> |**ユーザー ガバナンス**|✔|✔||✔|近日中にご利用になれます|近日中にご利用になれます|近日中にご利用になれます||  
> |**ログオン アクティビティ**|✔|✔|✔|✔|✔|✔|✔|✔|  
> |**ユーザーの利用状況**|✔*|✔|✔|✔ - Google Unlimited が必要です|一部|Salesforce Shield でサポート|✔|適用できません|  
> |**管理者アクティビティ**|✔|✔|✔|✔|一部|✔|✔|✔|  
> |**定期的なファイル スキャン**|✔|✔|適用できません|✔|✔|✔|✔|適用できません|  
> |**ほぼリアルタイムのファイル スキャン**|✔|✔|適用できません|✔ - Google Unlimited が必要です|||近日中にご利用になれます||  
> |**コントロールの共有**|✔|✔|適用できません|✔|適用できません||✔||  
> |**検疫**|✔|✔|適用できません|近日中にご利用になれます|||近日中にご利用になれます||  
> |**アプリのアクセス許可の表示**|✔|プロバイダーはサポートしていません|適用できません|✔||✔|プロバイダーはサポートしていません||  
> |**アプリのアクセス許可の取り消し**|✔||適用できません|✔||✔|適用できません||  
> |**Azure Information Protection ラベルの適用**|✔|✔|||||||  

## <a name="prerequisites"></a>前提条件  

- アプリによっては、IP アドレスをホワイト リストに追加して Cloud App Security によるログ収集や、Cloud App Security コンソールへのアクセスを可能にする必要がある場合があります。 詳細については、「[ネットワーク要件](network-requirements.md)」を参照してください。

- Cloud App Security API の統合によって接続するアプリごとに Cloud App Security 専用の管理サービス アカウントを作成することをお勧めします。  

> [!NOTE]  
>  URL および IP アドレスが変更されときに更新されるようにするには、「[Office 365 の URL および IP アドレス範囲](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)」で説明されているように RSS を購読します。  

アプリ コネクタを使用するには、特定アプリケーションごとに、次に示すものが含まれるかどうかを確認する必要があります。  

|アプリ|ライセンスの種類|User|  
|---------|------------------|----------|  
|ボックス|Enterprise|管理者として Box に接続することを強くお勧めします。共同管理者として接続すると、部分的なデータしか表示されません。 共同管理者として接続する場合は、すべての権限を選択してください。|  
|G Suite|G Suite Unlimited が推奨される<br /><br /> G Suite Enterprise (最低必要)|スーパー管理者|  
|Office 365||グローバル管理者|  
|AWS||新しく作成されたユーザー|  
|ドロップボックス|Business/Enterprise|管理者|  
|Okta|Enterprise (評価版ではない)|管理者|  
|Exchange||グローバル管理者|  
|ServiceNow|Eureka 以降|管理者 +RestAPI のロール|  
|Salesforce||管理者|  


**ExpressRoute**  

Cloud App Security は Azure に展開され、[ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/) に完全に統合されます。 検出ログのアップロードを含む、Cloud App Security アプリとのすべての通信、および Cloud App Security に送信されるトラフィックは、ExpressRoute の**パブリック ピアリング**経由でルーティングされるため、待機時間、パフォーマンス、およびセキュリティが改善されます。 お客様側で設定を行う必要はありません。  
パブリック ピアリングの詳細については、「[ExpressRoute 回線とルーティング ドメイン](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/)」を参照してください。  

## <a name="see-also"></a>参照  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  


## <a name="check-out-this-video"></a>このビデオをご覧ください。
[Microsoft Cloud App Security – REST API とトークン](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)  
