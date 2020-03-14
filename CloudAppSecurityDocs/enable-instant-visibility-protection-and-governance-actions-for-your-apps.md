---
title: アプリを接続して可視性と制御を取得する Cloud App Security |Microsoft Docs
description: この記事では、API コネクタを使用してアプリを組織のクラウド内のアプリに接続するプロセスについて説明します。
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
ms.openlocfilehash: 0aa55a99017a1768bf58fd2c2a40688c1a5c95e6
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285346"
---
# <a name="connect-apps"></a>アプリを接続する

*適用対象: Microsoft Cloud App Security*

アプリコネクタでは、アプリプロバイダーの Api を使用して、接続するアプリを Microsoft Cloud App Security して、可視性と制御を向上させることができます。

Microsoft Cloud App Security は、クラウドプロバイダーによって提供される Api を活用します。 各サービスには、調整、API の制限、動的なタイムシフト API ウィンドウなど、独自のフレームワークと API の制限があります。 Microsoft Cloud App Security、Api の使用を最適化し、最高のパフォーマンスを提供するために、サービスと連携しています。 Api に適用されるさまざまな制限事項を考慮して、Cloud App Security エンジンは許可された容量を使用します。 テナント内のすべてのファイルのスキャンなど、一部の操作では多数の Api が必要になるため、長期間にわたって分散されます。 ポリシーによっては、数時間または数日間にわたって実行される場合があります。

## <a name="multi-instance-support"></a>複数インスタンスのサポート

Cloud App Security は、同一の接続されたアプリの複数のインスタンスをサポートします。 たとえば、Salesforce のインスタンスが複数ある場合 (1 つは営業用、もう1つはマーケティング用)、両方を Cloud App Security に接続できます。 同じコンソールからさまざまなインスタンスを管理して、細かいポリシーを作成し、より詳細な調査を行うことができます。 このサポートは、クラウドで検出されたアプリやプロキシ接続アプリではなく、API 接続アプリにのみ適用されます。

> [!NOTE]
> Office 365 および Azure では、複数インスタンスはサポートされていません。

## <a name="how-it-works"></a>しくみ

Cloud App Security はシステム管理者権限で展開されているため、環境内のすべてのオブジェクトへのフル アクセスができます。

アプリ コネクタのフローは次のとおりです:

1. Cloud App Security スキャンし、認証のアクセス許可を保存します。
2. Cloud App Security はユーザー リストを要求します。 要求が最初に完了したとき、スキャンが完了するまでに時間がかかることがあります。 ユーザーのスキャンが完了すると、Cloud App Security はアクティビティとファイルに進みます。 スキャンが開始されるとすぐに、いくつかのアクティビティが Cloud App Security で利用できるようになります。
3. ユーザーの要求が完了すると、Cloud App Security によって、ユーザー、グループ、アクティビティ、およびファイルが定期的にスキャンされます。 最初のフル スキャンが完了すると、すべてのアクティビティが利用できるようになります。

この接続には、テナントのサイズ、ユーザーの数、スキャンする必要があるファイルのサイズと数に応じて、時間がかかることがあります。

接続しているアプリに応じて、API 接続は次の項目を有効にします。

- **アカウント情報**-ユーザー、アカウント、プロファイル情報、状態 (中断、アクティブ、無効) グループ、および特権を表示します。

- **監査証跡**-ユーザーアクティビティ、管理者アクティビティ、サインインアクティビティの可視性。

- **データスキャン**-2 つのプロセスを使用した非構造化データのスキャン-定期的 (12 時間ごと) とリアルタイムスキャン (変更が検出されるたびにトリガーされます)。

- **アプリのアクセス許可**-発行されたトークンとそのアクセス許可を表示します。

- **アカウントガバナンス**-ユーザーを中断したり、パスワードを取り消したりできます。

- **データガバナンス**-ごみ箱にあるファイルやファイルの上書きなど、ファイルを検疫できます。

- **アプリのアクセス許可ガバナンス**-トークンを削除する機能。

次の表は、クラウド アプリごとの、アプリのコネクタによって使用できるようになる機能のリストです。

> [!div class="mx-tableFixed"]
>
> | | AWS | Box | ドロップボックス | GCP | G Suite | Office 365 | Okta | Service Now | Salesforce | Webex | Workday |
> |-|-|-|-|-|-|-|-|-|-|-|-|
> | **アカウントの一覧表示** | ✔ | ✔ | ✔ | サブジェクト G Suite 接続 | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
> | **グループの一覧表示** | ✔ | ✔ | ✔ | サブジェクト G Suite 接続 | ✔ | ✔ | ✔ | ✔ | ✔ | | プロバイダーはサポートしていません |
> | **権限の一覧表示** | | ✔ | ✔ | サブジェクト G Suite 接続 | ✔ | ✔ | プロバイダーはサポートしていません | ✔ | ✔ | ✔ | プロバイダーによって pported されていません |
> | **ユーザー ガバナンス** | | ✔ | 近日中にご利用になれます | サブジェクト G Suite 接続 | ✔ | ✔ | | 近日中にご利用になれます | ✔ | 近日中にご利用になれます | プロバイダーでサポートされる t |
> | **ログオン アクティビティ** | ✔ | ✔ | ✔ | サブジェクト G Suite 接続 | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
> | **ユーザーの利用状況** | 適用できません | ✔ | ✔ | ✔ | ✔-Google Business または Enterprise が必要です | ✔ | ✔ | 一部 | Lesforce シールドでサポートされています | ✔ | ✔ |
> | **管理者アクティビティ** | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | 一部 | ✔ | ✔ | プロバイダーはサポートしていません |
> | **DLP-定期スキャン** | | ✔ | 近日中にご利用になれます | 適用できません | ✔ | ✔ | 適用できません | | | | Ovider ではサポートされていません |
> | **DLP-ほぼリアルタイムのスキャン** | | ✔ | ✔ | 適用できません | ✔-Google Business Enterprise が必要です | ✔ | 適用できません | ✔ | ✔ | ✔ | プロバイダーはサポートしていません |
> | **コントロールの共有** | ✔ | ✔ | ✔ | 適用できません | ✔ | ✔ | 適用できません | 適用できません | | ✔ | Ovider ではサポートされていません |
> | **ファイルガバナンス** | ✔ | ✔ | ✔ | 適用できません | ✔ | ✔ | 適用できません | | ✔ | | プロバイダーはサポートしていません |
> | **アプリのアクセス許可の表示** | 適用できません | プロバイダーはサポートしていません | 今後 | 適用できません | ✔ | ✔ | 適用できません | | ✔ | 適用できません | 適用できません |
> | **アプリのアクセス許可の取り消し** | 適用できません | プロバイダーはサポートしていません | 近日にご連絡ください | 適用できません | ✔ | ✔ | 適用できません | | ✔ | 適用できません | 適用できません |
> | **Azure Information Protection ラベルを適用する** | 適用できません | ✔ | | 適用できません | ✔ | ✔ | 適用できません | | | 適用できません | 適用できません |

## <a name="prerequisites"></a>前提条件

- アプリによっては、Cloud App Security がログを収集し、Cloud App Security コンソールにアクセスできるようにするために、IP アドレスをホワイトリストに表示する必要がある場合があります。 詳細については、「[ネットワーク要件](network-requirements.md)」を参照してください。

- Cloud App Security API の統合によって接続するアプリごとに Cloud App Security 専用の管理サービス アカウントを作成することをお勧めします。

> [!NOTE]
> URL および IP アドレスが変更されときに更新されるようにするには、「[Office 365 の URL および IP アドレス範囲](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)」で説明されているように RSS を購読します。

アプリコネクタを使用するには、特定のアプリごとに次のものがあることを確認する必要があります。

| アプリ | ライセンスの種類 | ユーザー |
|-----|--------------|------|
| Azure | | グローバル管理者 |
| AWS | | 新しく作成されたユーザー |
| Box | Enterprise | Box に管理者として接続することを強くお勧めします。Coadmin として接続すると、データの部分的な可視性だけが得られます。 Coadmin として接続する場合は、必ず [すべてのアクセス許可] を選択してください。 |
| ドロップボックス | Business/Enterprise | [管理] |
| GCP | | 「 [Connect GCP の前提条件](connect-google-gcp-to-microsoft-cloud-app-security.md#prerequisites)」を参照してください。 |
| G Suite | G Suite Business または Enterprise (推奨)<br /><br />G Suite Enterprise (最低必要) | スーパー管理者 |
| Office 365 | | グローバル管理者 |
| Okta | Enterprise (評価版ではない) | [管理] |
| Salesforce | | [管理] |
| ServiceNow | Eureka 以降 | Admin + RestAPI ロール |
| Webex | | 管理者 + コンプライアンス管理者 |
| Workday | | [接続 Workday の前提条件](connect-workday-to-microsoft-cloud-app-security.md#prerequisites)を確認する |

### <a name="expressroute"></a>ExpressRoute

Cloud App Security は Azure に展開され、[ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/) に完全に統合されます。 検出ログのアップロードを含む、Cloud App Security アプリと Cloud App Security に送信されるトラフィックはすべて、ExpressRoute**パブリックピアリング**経由でルーティングされ、待機時間、パフォーマンス、およびセキュリティが向上します。 お客様側で設定を行う必要はありません。
パブリック ピアリングの詳細については、「[ExpressRoute 回線とルーティング ドメイン](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/)」を参照してください。

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>こちらのビデオをご覧ください。

> [!div class="nextstepaction"]
> [Microsoft Cloud App Security – REST API とトークン](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)
