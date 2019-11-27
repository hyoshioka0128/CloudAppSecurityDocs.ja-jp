---
title: アプリを接続して使用状況を表示し、管理する - Cloud App Security | Microsoft Docs
description: この記事では、API コネクタを使用して、アプリを組織のクラウド内のアプリに接続するプロセスについて説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/12/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e22b7d7f1b59c49470426080bf822fa070a1af6d
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2019
ms.locfileid: "74458180"
---
# <a name="connect-apps"></a>アプリを接続する

*適用対象: Microsoft Cloud App Security*

アプリ コネクタではアプリ プロバイダーの API が使用されるため、Microsoft Cloud App Security による接続先アプリの表示および制御がしやすくなります。

Microsoft Cloud App Security では、クラウド プロバイダーから提供される API が利用されます。 各サービスには、独自のフレームワークと、スロットリング、API 制限、動的タイムシフト API ウィンドウなどの API に関する制限事項があります。 Microsoft Cloud App Security はサービスと連携して、API の使用を最適化し、最高のパフォーマンスを提供します。 Cloud App Security エンジンでは、サービスによって API に適用されるさまざまな制限事項が考慮されて、許容される容量が使用されます。 テナント内のすべてのファイルのスキャンなど、一部の操作には大量の API が必要となるため、長時間にわたって実行されます。 ポリシーによっては、数時間または数日間にわたって実行される場合があります。

## <a name="multi-instance-support"></a>複数インスタンスのサポート

Cloud App Security は接続された同一アプリの複数のインスタンスをサポートします。 たとえば、Salesforce の複数のインスタンスがある場合 (販売用とマーケティング用)、両方を Cloud App Security に接続できます。 同じコンソールから異なるインスタンスを管理して、きめ細かいポリシーを作成し、詳細な調査を行うことができます。 このサポートは API 接続アプリにのみ適用され、クラウドで検出されたアプリやプロキシ接続されたアプリには適用されません。

> [!NOTE]
> Office 365 および Azure では、複数インスタンスはサポートされていません。

## <a name="how-it-works"></a>しくみ

Cloud App Security はシステム管理者権限で展開されているため、環境内のすべてのオブジェクトへのフル アクセスができます。

アプリ コネクタのフローは次のとおりです:

1. Cloud App Security で、認証アクセス許可がスキャンされて保存されます。
2. Cloud App Security はユーザー リストを要求します。 初めて要求が行われる場合、スキャンが完了するまでにいくらか時間がかかることがあります。 ユーザーのスキャンが完了すると、Cloud App Security はアクティビティとファイルに進みます。 スキャンが開始されるとすぐに、いくつかのアクティビティが Cloud App Security で利用できるようになります。
3. ユーザーの要求が完了した後、Cloud App Security ではユーザー、グループ、アクティビティ、ファイルが定期的にスキャンされます。 最初のフル スキャンが完了すると、すべてのアクティビティが利用できるようになります。

スキャンの必要なテナントのサイズ、ユーザーの数、ファイルのサイズと数によっては、この接続に時間がかかる場合があります。

接続先のアプリによっては、API 接続により次の項目を使用できるようになります。

- **アカウント情報** - ユーザー、アカウント、プロファイル情報、状態 (中断、アクティブ、無効) グループ、特権の可視化。

- **監査証跡** - ユーザー アクティビティ、管理者アクティビティ、サインイン アクティビティの可視化。

- **データ スキャン** - 定期スキャン (12 時間ごと) とリアルタイム スキャン (変更が検出されるたびに開始) の 2 つのプロセスを使用した、非構造化データのスキャン。

- **アプリのアクセス許可** - 発行済みトークンとそのアクセス許可の可視化。

- **アカウントのガバナンス** - ユーザーの一時停止、パスワードの取り消しなどの機能。

- **データ ガバナンス** - ごみ箱のファイルを含むファイルの検疫や、ファイルの上書きを行う機能。

- **アプリのアクセス許可のガバナンス** - トークンを削除する機能。

次の表は、クラウド アプリごとの、アプリのコネクタによって使用できるようになる機能のリストです。

> [!div class="mx-tableFixed"]
>
> | | AWS | ボックス | ドロップボックス | GCP | G Suite | Office 365 | Okta | 今すぐサービス | Salesforce | Webex | Workday |
> |-|-|-|-|-|-|-|-|-|-|-|-|
> | **アカウントの一覧表示** | ✔ | ✔ | ✔ | サブジェクト G Suite 接続 | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
> | **グループの一覧表示** | ✔ | ✔ | ✔ | サブジェクト G Suite 接続 | ✔ | ✔ | ✔ | ✔ | ✔ | | プロバイダーはサポートしていません |
> | **権限の一覧表示** | | ✔ | ✔ | サブジェクト G Suite 接続 | ✔ | ✔ | プロバイダーはサポートしていません | ✔ | ✔ | ✔ | プロバイダーによって pported されていません |
> | **ユーザー ガバナンス** | | ✔ | 近日中にご利用になれます | サブジェクト G Suite 接続 | ✔ | ✔ | | 近日中にご利用になれます | ✔ | 近日中にご利用になれます | プロバイダーでサポートされる t |
> | **ログオン アクティビティ** | ✔ | ✔ | ✔ | サブジェクト G Suite 接続 | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
> | **ユーザーの利用状況** | 適用なし | ✔ | ✔ | ✔ | ✔ - Google の Business または Enterprise が必要 | ✔ | ✔ | 一部 | Lesforce シールドでサポートされています | ✔ | ✔ |
> | **管理者アクティビティ** | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | 一部 | ✔ | ✔ | プロバイダーはサポートしていません |
> | **DLP-定期スキャン** | | ✔ | 近日中にご利用になれます | 適用なし | ✔ | ✔ | 適用なし | | | | Ovider ではサポートされていません |
> | **DLP-ほぼリアルタイムのスキャン** | | ✔ | ✔ | 適用なし | ✔-Google Business Enterprise が必要です | ✔ | 適用なし | ✔ | ✔ | ✔ | プロバイダーはサポートしていません |
> | **コントロールの共有** | ✔ | ✔ | ✔ | 適用なし | ✔ | ✔ | 適用なし | 適用なし | | ✔ | Ovider ではサポートされていません |
> | **ファイルガバナンス** | ✔ | ✔ | ✔ | 適用なし | ✔ | ✔ | 適用なし | | ✔ | | プロバイダーはサポートしていません |
> | **アプリのアクセス許可の表示** | 適用なし | プロバイダーはサポートしていません | 今後 | 適用なし | ✔ | ✔ | 適用なし | | ✔ | 適用なし | 適用なし |
> | **アプリのアクセス許可の取り消し** | 適用なし | プロバイダーはサポートしていません | 近日にご連絡ください | 適用なし | ✔ | ✔ | 適用なし | | ✔ | 適用なし | 適用なし |
> | **Azure Information Protection ラベルの適用** | 適用なし | ✔ | | 適用なし | ✔ | ✔ | 適用なし | | | 適用なし | 適用なし |

## <a name="prerequisites"></a>必須コンポーネント

- アプリによっては、IP アドレスをホワイト リストに追加して Cloud App Security によるログ収集や、Cloud App Security コンソールへのアクセスを可能にする必要がある場合があります。 詳細については、「[ネットワーク要件](network-requirements.md)」をご覧ください。

- Cloud App Security API の統合によって接続するアプリごとに Cloud App Security 専用の管理サービス アカウントを作成することをお勧めします。

> [!NOTE]
> URL および IP アドレスが変更されときに更新されるようにするには、「[Office 365 の URL および IP アドレス範囲](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)」で説明されているように RSS を購読します。

アプリ コネクタを使用するには、特定のアプリごとに、次のものがあることを確認する必要があります。

| アプリ | ライセンスの種類 | ユーザー |
|-----|--------------|------|
| Azure | | グローバル管理者 |
| AWS | | 新しく作成されたユーザー |
| ボックス | Enterprise | Box に管理者として接続することを強くお勧めします。Coadmin として接続すると、データの部分的な可視性だけが得られます。 共同管理者として接続する場合は、すべてのアクセス許可を選択してください。 |
| ドロップボックス | Business/Enterprise | 管理 |
| GCP | | 「 [Connect GCP の前提条件](connect-google-gcp-to-microsoft-cloud-app-security.md#prerequisites)」を参照してください。 |
| G Suite | G Suite Business または Enterprise を推奨<br /><br />G Suite Enterprise (最低必要) | スーパー管理者 |
| Office 365 | | グローバル管理者 |
| Okta | Enterprise (評価版ではない) | 管理 |
| Salesforce | | 管理 |
| ServiceNow | Eureka 以降 | Admin + RestAPI ロール |
| Webex | | 管理者 + コンプライアンス管理者 |
| Workday | | [接続 Workday の前提条件](connect-workday-to-microsoft-cloud-app-security.md#prerequisites)を確認する |

### <a name="expressroute"></a>ExpressRoute

Cloud App Security は Azure に展開され、[ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/) に完全に統合されます。 検出ログのアップロードを含む、Cloud App Security アプリとのすべての通信、および Cloud App Security に送信されるトラフィックは、ExpressRoute の**パブリック ピアリング**経由でルーティングされるため、待機時間、パフォーマンス、およびセキュリティが改善されます。 お客様側で設定を行う必要はありません。
パブリック ピアリングの詳細については、「[ExpressRoute 回線とルーティング ドメイン](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/)」を参照してください。

## <a name="next-steps"></a>次の手順

[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>このビデオをご覧ください。

[Microsoft Cloud App Security – REST API とトークン](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)
