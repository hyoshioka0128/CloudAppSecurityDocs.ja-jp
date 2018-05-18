---
title: Cloud App Security の新機能 | Microsoft Docs
description: このトピックは、Cloud App Security の最新リリースの新機能がわかるように頻繁に更新されます。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/11/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: d418ef3d-76ee-45d5-b5ae-21346e5239a3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 545d7cb0e7152918e8f9b1e37ff1d7a210605342
ms.sourcegitcommit: aebd4dd970465a7f5818329f344c24fe73f616dd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2018
---
*適用対象: Microsoft Cloud App Security*


# <a name="whats-new-with-microsoft-cloud-app-security"></a>Microsoft Cloud App Security の新機能

## <a name="cloud-app-security-release-123"></a>Cloud App Security リリース 123

リリース日: 2018 年 5 月 13 日

- **異常検出ポリシーのスコープ指定**: <br>
異常検出ポリシーに、スコープを指定できるようになりました。 これにより、特定のユーザーまたはグループのみを含めたり、特定のユーザーまたはグループを除外したりするように、各異常検出ポリシーを設定できます。 たとえば、頻度の低い国/地域の検出から頻繁に出張する特定のユーザーを無視するために、アクティビティを設定できます。 


## <a name="cloud-app-security-release-122"></a>Cloud App Security リリース 122
リリース日: 2018 年 4 月 29 日

-   段階的なロールアウト: アプリごとに、**Microsoft Cloud App Security 管理者に管理アクセス許可を設定**できるようになりました。 たとえば、G Suite のみの管理者として、特定のユーザーを設定することができます。 これにより、情報が G Suite だけに関連する場合にのみ、ユーザーは Microsoft Cloud App Security でその情報を表示して変更することができます。 詳細については、「[管理アクセス許可の管理](manage-admins.md)」を参照してください。
- 段階的なロールアウト: Microsoft Cloud App Security で **Okta 管理者ロールが表示される**ようになりました。これらは、**[設定]** > **[ユーザー グループ]** でタグとして、各ロールで利用できます。


## <a name="cloud-app-security-release-121"></a>Cloud App Security リリース 121
リリース日: 2018 年 4 月 22 日

-   **Conditional Access App Control (以前の Cloud App Security プロキシ)** のパブリック プレビューは、さまざまなアプリケーションの深いレベルでの可視性を促進し、それらのアプリケーションを制御する機能を備えるように強化されています。 *[アクティビティの種類]* フィルターを使用してセッション ポリシーを作成し、アプリ固有のさまざまなアクティビティの監視やブロックを行えるようになりました。 この新しいフィルターは、既存のファイル ダウンロード制御機能を補い、組織でアプリケーションを包括的に制御できるようになります。また、Azure Active Directory の条件付きアクセスと連携して、リスクのあるユーザー セッション (B2B コラボレーション ユーザーや管理されていないデバイスからのユーザーとのセッションなど) に対してリアルタイムの可視性と制御を提供します。 詳しくは、「[セッション ポリシー](session-policy-aad.md)」をご覧ください。
-   段階的なロールアウト: Cloud App Security の**異常検出ポリシーが改良され**、ランサムウェア アクティビティと終了させらたユーザーのアクティビティの 2 種類を新たに含むようになりました。 Cloud App Security は、異常検出を含むようにランサムウェア検出機能を拡張し、高度なランサムウェア攻撃に対する包括的な防御を強化しました。 Cloud App Security は、弊社のセキュリティ調査の専門技術を使用して、ランサムウェア アクティビティを反映する行動パターンを識別し、総体的で堅牢な保護を実現します。 終了させられたユーザーのアクティビティでは、終了させられたユーザーのアカウントを監視できます。このようなユーザーは、企業アプリからプロビジョニング解除されている可能性がありますが、多くの場合、特定の企業リソースのアクセスを保持しています。 詳細については、「[行動分析と異常検出を瞬時に取得する](anomaly-detection-policy.md)」を参照してください。


## <a name="cloud-app-security-release-120"></a>Cloud App Security リリース 120
リリース日: 2018 年 4 月 8 日

-   Office 365 と Azure AD では、内部アプリケーションを Office 365 と Azure AD アプリケーション (内部も外部も) によって実行されたユーザー アカウント アクティビティとして検出する機能を段階的にロールアウトしています。 これにより、アプリケーションが予期しない、承認されていないアクティビティを実行した場合にアラートを発するポリシーを作成できるようになります。 
-   アプリのアクセス許可の一覧を CSV にエクスポートするときには、コンプライアンスと調査のプロセスを支援するために、公開元、アクセス許可のレベル、コミュニティの使用などの追加フィールドが含まれます。
-   ServiceNow に接続したアプリが、内部サービスのアクティビティが “ゲスト” によって実行されたものとして登録されず、偽陽性のアラートをトリガーしないように改善されました。 このようなアクティビティはそれ以外のすべての接続アプリと同様に N/A と表示されます。


## <a name="cloud-app-security-release-119"></a>Cloud App Security リリース 119
2018 年 3 月 18 日のリリース

-   IP アドレス範囲のページに、Cloud App Security で検出される組み込みの IP アドレスが含まれています。 これには、Azure や Office 365 のような特定済みのクラウド サービスの IP アドレスだけでなく、脅威インテリジェンスのフィードの IP アドレスも含まれています。脅威インテリジェンスのフィードは IP アドレスが既知の危険な IP アドレスに関する情報によって自動的に拡充されます。 
-   Cloud App Security がファイルに対するガバナンス アクションを実行しようとして、ファイルのロックが原因で失敗した場合、ガバナンス アクションが自動的に再試行されるようになりました。 

## <a name="cloud-app-security-release-118"></a>Cloud App Security リリース 118
2018 年 3 月 4 日のリリース

- Microsoft Cloud App Security のシャドウ IT 検出と監視の機能をユーザー独自のカスタム アプリで実行できるようになりました。 Cloud Discovery にカスタム アプリを追加する新しい機能を使用すると、アプリの使用状況を監視し、使用パターンの変化に関してアラートを受け取ることができます。 詳細については、[カスタム アプリの保護](cloud-discovery-custom-apps.md)に関する記事を参照してください。 この機能は、徐々にロール アウトされていきます。

- Cloud App Security ポータルの **[設定]** ページが再設計されました。 新しい設計では、すべての設定ページの統合、検索機能と強化されたデザインを提供します。 

- Cloud Discovery では、Barracuda F シリーズ ファイアウォールおよび Barracuda F シリーズ ファイアウォール Web ログ ストリーミングがサポートされました。

- ユーザーと IP アドレスのページの検索機能でオートコンプリートが有効になり、探しているものを見つけやすくなりました。

- 除外するエンティティと除外する IP アドレスの設定ページで、一括操作を実行できるようになりました。 これにより、複数のユーザーやグループまたは IP アドレスを選択して、組織内の Cloud Discovery の一部としての監視対象から、より簡単に除外できるようになります。 

## <a name="cloud-app-security-release-117"></a>Cloud App Security リリース 117
2018 年 2 月 20 日のリリース

-   Cloud App Security と Azure Information Protection との統合が深まり、G Suite 内のファイルを保護できるようになりました。 このパブリック プレビュー機能を使用すると、G Suite のファイルをスキャンし、分類したり、Azure Information Protection ラベルを保護のために自動的に適用したりできます。 詳細については、[Azure Information Protection の統合](azip-integration.md)に関するページを参照してください。

-   Cloud Discovery で [Digital Arts i-FILTER](http://www.daj.jp/en/products/if/) がサポートされました。

-   SIEM エージェント テーブルには、管理を簡単にする詳細が含まれています。

## <a name="cloud-app-security-release-116"></a>Cloud App Security リリース 116
2018 年 2 月 4 日のリリース
- Cloud App Security の異常検出ポリシーが拡張され、ありえない移動、疑わしい IP アドレスからのアクティビティ、複数回のログイン試行の失敗など、新しい**シナリオ ベースの検出**が追加されました。 新しいポリシーは自動的に有効になり、設定不要の脅威検出機能がクラウド環境全体で利用できます。 また、この新しいポリシーは、調査プロセスを加速し、進行中の脅威を阻止するのに役立つ Cloud App Security 検出エンジンからのさらに多くのデータを公開します。 詳細については、「[行動分析と異常検出を瞬時に取得する](https://docs.microsoft.com/en-us/cloud-app-security/anomaly-detection-policy)」を参照してください。

- 段階的なロールアウト: Cloud App Security は SaaS アプリ全体でユーザーとユーザー アカウントを関連付けるようになります。 これにより、関連するさまざまな SaaS アプリすべてで、使用したアプリやアカウントに関係なく、ユーザーのすべてのアクティビティを簡単に調査できます。  

-   段階的なロールアウト: Cloud App Security は接続された同一アプリの複数のインスタンスをサポートするようになります。 たとえば、Salesforce の複数のインスタンスがある場合 (営業用とマーケティング用など)、その両方を Cloud App Security に接続し、詳細にポリシーを作成して調査し、同じコンソールから管理することができます。 

- Cloud Discovery パーサーが、2 つの追加のチェックポイント形式、XML と KPC をサポートするようになりました。



## <a name="cloud-app-security-release-115"></a>Cloud App Security リリース 115
2018 年 1 月 21 日のリリース

- このリリースでは、ファイル ポリシーで特定のフォルダーを選択するときのエクスペリエンスが向上しました。 複数のフォルダーを表示、選択して、簡単にポリシーに追加できるようになりました。 
- **[検出されたアプリ]** ページに次の変更が加えられました。 
  - タグの一括追加機能により、(承認されたタグと承認されていないタグに加え) カスタム タグを適用できるようになりました。 
  - **IP アドレス レポートの生成**または**ユーザー レポートの生成**時、エクスポートされたレポートに、トラフィックの送信元が承認されたアプリか、承認されていないアプリかについての情報が表示されるようになりました。 
- ポータルの **[アプリを接続]** ページから、Microsoft Cloud App Security チームの新しい API App コネクタを直接要求できるようになりました。 


## <a name="cloud-app-security-release-114"></a>Cloud App Security リリース 114
2018 年 1 月 7 日のリリース

- バージョン 114 より、カスタム クエリを作成し、アクティビティ ログのページと検出されたアプリのページで保存する機能を徐々にロールアウトします。 カスタム クエリを使用すると、詳しい調査のために再使用できるフィルター テンプレートを作成できます。 また、**クエリ候補**機能が追加されました。調査テンプレートとして直接利用し、アクティビティや検出されたアプリにフィルター処理を適用できます。 **クエリ候補**には、権限借用アクティビティ、管理者アクティビティ、危険な非準拠クラウド ストレージ アプリ、暗号化の弱いエンタープライズ アプリ、セキュリティ上の問題など、リスクを特定するためのカスタム フィルターが含まれます。 **クエリ候補**をテンプレートとして利用して自分に合うように変更し、新しいクエリとして保存できます。 詳細については、「[アクティビティ フィルターとクエリ](activity-filters-queries.md)」と「[検出されたアプリのフィルターとクエリ](discovered-app-queries.md)」を参照してください。
 
- [status.cloudappsecurity.com](https://status.cloudappsecurity.com) にアクセスするか、ポータル内から直接、**[ヘルプ]**>**[システム ステータス]** の順にクリックすることで、Cloud App Security サービスの現在の状態を確認できます。 
 


## <a name="see-also"></a>参照  

ここに示されるもの以前のリリースについて詳しくは、「[Past releases of Microsoft Cloud App Security](release-note-archive.md)」(Microsoft Cloud App Security の過去のリリース) を参照してください。

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  