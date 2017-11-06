---
title: "Cloud App Security でのポリシー テンプレートのリファレンス | Microsoft ドキュメント"
description: "このトピックでは、クラウド アプリの使用を制御するためにポリシーを使用および設定する方法について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/6/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a6658937-57a2-484a-85cb-5a4cdbeeb002
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d9ffe832652885548ddeb49fd782d2a104c7523f
ms.sourcegitcommit: b729e881851cdd8dc3f105ddbf6b4b907b8588dd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2017
---
# <a name="policy-templates"></a>ポリシー テンプレート

Cloud App Security に存在するすべてのポリシー テンプレートの一覧を次に示します。 簡単に使用できるように、可能な限り既存のテンプレートに基づいてポリシーの作成を始めることをお勧めします。

|リスク カテゴリ|テンプレート名|説明|
|-----|----|----|
|Cloud Discovery|Anomalous behavior in discovered users (検出されたユーザーの異常な動作)|検出されたユーザーとアプリで異常な動作 (他のユーザーと比較して大量のアップロード データ、ユーザーの履歴と比較して大量のユーザー トランザクションなど) が検出されたときにアラートを生成します。|
|Cloud Discovery|Anomalous behavior of discovered IP addresses (検出された IP アドレスの異常な動作)|検出された IP アドレスとアプリで異常な動作が検出されたときにアラートを生成します。たとえば、他の IP アドレスに比べて大量のデータがアップロードされている場合や、IP アドレスの履歴に比べてアプリ トランザクションが大きい場合などです。|
|Cloud Discovery|Collaboration app compliance check (コラボレーション アプリのコンプライアンス チェック)|SOC2 および SSAE 16 に準拠しておらず、50 人を超えるユーザーに使用され、毎日の合計使用量が 50 MB を超える新しいコラボレーション アプリが検出されたときにアラートを生成します。|
|Cloud Discovery|Cloud storage app compliance check (クラウド ストレージ アプリのコンプライアンス チェック)|SOC2、SSAE 16、ISAE 3402、PCI DSS に準拠しておらず、50 人を超えるユーザーに使用され、毎日の合計使用量が 50 MB を超える新しいクラウド ストレージ アプリが検出されたときにアラートを生成します。|
|Cloud Discovery|CRM app compliance check (CRM アプリ コンプライアンス チェック)|SOC2、SSAE 16、ISAE 3402、ISO 27001、および HIPAA に準拠しておらず、50 人を超えるユーザーに使用され、毎日の合計使用量が 50 MB を超える新しい CRM アプリが検出されたときにアラートを生成します。|
|Cloud Discovery|New cloud storage app (新しいクラウド ストレージ アプリ)|50 人を超えるユーザーに使用され、毎日の合計使用量が 50 MB を超える新しいクラウド ストレージ アプリが検出されたときにアラートを生成します。|
|Cloud Discovery|New code hosting app (新しいコード ホスティング アプリ)|50 人を超えるユーザーに使用され、毎日の合計使用量が 50 MB を超える新しいコード ホスティング アプリが検出されたときにアラートを生成します。|
|Cloud Discovery|New collaboration app (新しいコラボレーション アプリ)|50 人を超えるユーザーに使用され、毎日の合計使用量が 50 MB を超える新しいコラボレーション アプリが検出されたときにアラートを生成します。|
|Cloud Discovery|New CRM app (新しい CRM アプリ)|50 人を超えるユーザーに使用され、毎日の合計使用量が 50 MB を超える新しい CRM アプリが検出されたときにアラートを生成します。|
|Cloud Discovery|New high volume app (新しい高ボリューム アプリ)|毎日の合計トラフィックが 500 MB を超える新しいアプリが検出されたときにアラートを生成します。|
|Cloud Discovery|New high upload volume app (新しい大量アップロード アプリ)|毎日の合計アップロード トラフィックが 500 MB を超える新しいアプリが検出されたときにアラートを生成します。|
|Cloud Discovery|New Human-Resource Management app (新しい人事管理アプリ)|50 人を超えるユーザーに使用され、毎日の合計使用量が 50 MB を超える新しい人事管理アプリが検出されたときにアラートを生成します。|
|Cloud Discovery|New online meeting app (新しいオンライン会議アプリ)|50 人を超えるユーザーに使用され、毎日の合計使用量が 50 MB を超える新しいオンライン会議アプリが検出されたときにアラートを生成します。|
|Cloud Discovery|New popular app (新しい人気アプリ)|500 人を超えるユーザーが使用する新しいアプリが検出されたときにアラートを生成します。|
|Cloud Discovery|New risky app (リスクが高い新しいアプリ)|リスク スコアが 6 未満で、50 人を超えるユーザーに使用され、毎日の合計使用量が 50 MB を超える新しいアプリが検出されたときにアラートを生成します。|
|Cloud Discovery|New sales app (新しい販売アプリ)|50 人を超えるユーザーに使用され、毎日の合計使用量が 50 MB を超える新しい販売アプリが検出されたときにアラートを生成します。|
|Cloud Discovery|New vendor management system apps (新しいベンダー管理システム アプリ)|50 人を超えるユーザーに使用され、毎日の合計使用量が 50 MB を超える新しいベンダー管理システム アプリが検出されたときにアラートを生成します。|
|DLP|Externally shared source code (外部で共有されたソース コード)|ソース コードを含むファイルが組織外で共有されたときにアラートを生成します。|
|DLP|File containing PCI detected in the cloud (クラウド (組み込みの DLP エンジン) で検出された PCI を含むファイル)|承認されたクラウド アプリで、組み込みのデータ損失防止 (DLP) エンジンによって支払いカード情報 (PCI) を含むファイルが検出されたときにアラートを生成します。|
|DLP|File containing PHI detected in the cloud (クラウド (組み込みの DLP エンジン) で検出された PHI を含むファイル)|承認されたクラウド アプリで、組み込みのデータ損失防止 (DLP) エンジンによって保護されている医療情報 (PHI) を含むファイルが検出されたときにアラートを生成します。|
|DLP|File containing PII detected in the cloud (built-in DLP engine) (クラウド (組み込みの DLP エンジン) で検出された PII を含むファイル)|承認されたクラウド アプリで、組み込みのデータ損失防止 (DLP) エンジンによって個人を特定できる情報 (PII) を含むファイルが検出されたときにアラートを生成します。|
|脅威の検出|Administrative activity from a non-corporate IP address (企業以外の IP アドレスからの管理アクティビティ)|管理者が、企業 IP アドレスの範囲カテゴリに含まれない IP アドレスから管理アクティビティを実行したときにアラートを生成します。 最初に、[設定] ページに移動し**IP アドレス範囲**を設定することで、企業 IP アドレスを構成する必要があります。|
|脅威の検出|General anomaly detection (一般的な異常検出)|承認済みのアプリのいずれかで異常なセッション (不可能な場所移動、ログオン パターン、非アクティブなアカウントなど) が検出されたときにアラートを生成します。|
|脅威の検出|危険な IP アドレスからのログオン|承認済みアプリに危険な IP アドレスのユーザーがログオンすると、アラートを生成します。 危険な IP アドレスのカテゴリには、既定で、匿名プロキシ、TOR、またはボットネットの IP アドレス タグを持つアドレスが含まれます。 IP アドレスの範囲設定ページで、このカテゴリに IP アドレスを追加することができます。|
|脅威の検出|Mass download by a single user (1 人のユーザーによる大量ダウンロード)|1 人のユーザーが 5 分以内に 50 回を超えるダウンロードを実行したときにアラートを生成します。|
|脅威の検出|Multiple failed user log on attempts to an app (複数回失敗したアプリに対するユーザー ログオン)|1 人のユーザーが 1 つのアプリにログオンを試み、5 分以内に失敗回数が 10 回を超えると、アラートを生成します。|
|脅威の検出|ランサムウェア アクティビティの可能性|ランサムウェアに感染している可能性のあるクラウドにユーザーがファイルをアップロードしたときにアラートを生成します。|
|脅威の検出|User logon from a non-categorized IP address (分類されていない IP アドレスからのユーザー ログオン)|特定の IP 範囲カテゴリに含まれていない IP アドレスからユーザーがログオンしたときにアラートを生成します。 IP アドレスを分類するには、[設定] ページに移動し、IP アドレスの範囲を選択します。|
|コントロールの共有|File shared with personal email addresses (個人の電子メール アドレスを含むファイルの共有)|ユーザー個人の電子メール アドレスを含むファイルが共有されたときにアラートを生成します。|
|コントロールの共有|File shared with unauthorized domain (未承認ドメインとのファイル共有)|ファイルが未承認ドメイン (競合他社など) と共有されたときにアラートを生成します。|
|コントロールの共有|Shared digital certificates (file extensions) (デジタル証明書の共有 (ファイル拡張子))|デジタル証明書を含むファイルが公に共有されたときにアラートを生成します。|
|コントロールの共有|Stale externally shared files (外部と共有した古いファイル)|外部と共有したファイルのうち、過去 6 か月間に開かれたり、変更されたりしていないファイルを検索し、自分のドライブから削除します。|



## <a name="see-also"></a>参照  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  