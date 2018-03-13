---
title: "Cloud App Security の新機能 | Microsoft Docs"
description: "このトピックは、Cloud App Security の最新リリースの新機能がわかるように頻繁に更新されます。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/7/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: d418ef3d-76ee-45d5-b5ae-21346e5239a3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 08a798bb20830afcbdb498c2ac72787873f72fab
ms.sourcegitcommit: 9de7ed2224aeed049fc2a87e52307988f8837eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="whats-new-with-microsoft-cloud-app-security"></a>Microsoft Cloud App Security の新機能


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

-   このリリースでは、ファイル ポリシーで特定のフォルダーを選択するときのエクスペリエンスが向上しました。 複数のフォルダーを表示、選択して、簡単にポリシーに追加できるようになりました。 
-   **[検出されたアプリ]** ページに次の変更が加えられました。 
   - タグの一括追加機能により、(承認されたタグと承認されていないタグに加え) カスタム タグを適用できるようになりました。 
   - **IP アドレス レポートの生成**または**ユーザー レポートの生成**時、エクスポートされたレポートに、トラフィックの送信元が承認されたアプリか、承認されていないアプリかについての情報が表示されるようになりました。 
-   ポータルの **[アプリを接続]** ページから、Microsoft Cloud App Security チームの新しい API App コネクタを直接要求できるようになりました。 


## <a name="cloud-app-security-release-114"></a>Cloud App Security リリース 114
2018 年 1 月 7 日のリリース

- バージョン 114 より、カスタム クエリを作成し、アクティビティ ログのページと検出されたアプリのページで保存する機能を徐々にロールアウトします。 カスタム クエリを使用すると、詳しい調査のために再使用できるフィルター テンプレートを作成できます。 また、**クエリ候補**機能が追加されました。調査テンプレートとして直接利用し、アクティビティや検出されたアプリにフィルター処理を適用できます。 **クエリ候補**には、権限借用アクティビティ、管理者アクティビティ、危険な非準拠クラウド ストレージ アプリ、暗号化の弱いエンタープライズ アプリ、セキュリティ上の問題など、リスクを特定するためのカスタム フィルターが含まれます。 **クエリ候補**をテンプレートとして利用して自分に合うように変更し、新しいクエリとして保存できます。 詳細については、「[アクティビティ フィルターとクエリ](activity-filters-queries.md)」と「[検出されたアプリのフィルターとクエリ](discovered-app-queries.md)」を参照してください。
 
- [status.cloudappsecurity.com](https://status.cloudappsecurity.com) にアクセスするか、ポータル内から直接、**[ヘルプ]**>**[システム ステータス]** の順にクリックすることで、Cloud App Security サービスの現在の状態を確認できます。 
 


## <a name="see-also"></a>参照  

ここに示されるもの以前のリリースについて詳しくは、「[Past releases of Microsoft Cloud App Security](release-note-archive.md)」(Microsoft Cloud App Security の過去のリリース) を参照してください。

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  