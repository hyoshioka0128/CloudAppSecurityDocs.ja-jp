---
title: Cloud App Security の管理者検疫でファイルを保護する
description: この記事では、管理者検疫を使用してデータの違反を管理するシナリオについて説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3fc04cfb-ad4c-4ac2-980a-ee9f4c740d88
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 82398a5fad8f2d5b3da67a7932b9df6857dd9355
ms.sourcegitcommit: 420a0119513e3f4a8651f6a9e66c56fe442a31c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2018
ms.locfileid: "53347256"
---
# <a name="protecting-your-files-with-admin-quarantine"></a>管理者検疫によるファイルの保護

*適用対象:Microsoft Cloud App Security*

[ファイル ポリシー](data-protection-policies.md)は、情報保護ポリシーに対する脅威を見つけるための優れたツールです。 たとえば、クラウド内でユーザーが機密情報、クレジット カード番号、サードパーティの ICAP ファイルを格納した場所を発見するファイル ポリシーを作成します。 Microsoft Cloud App Security を使用すると、クラウドに脆弱な状態で保存されているこのような望ましくないファイルを検出できるだけでなく、直ちに脅威の対象となるファイルの追跡を停止し、ロックする措置を取ることができます。 **管理者検疫**を使用すると、クラウド内のファイルを保護し、問題を修復できるだけでなく、今後の漏えいを防ぐこともできます。

>[!NOTE] 
> - これはプレビュー機能です。
> - 管理者検疫をサポートするアプリの一覧については、[ガバナンス アクション](governance-actions.md)の一覧を参照してください。
 
## <a name="how-quarantine-works"></a>検疫のしくみ 

1. ファイルがポリシーに一致する場合、ファイルに**管理者検疫**のオプションを使用できます。

2. ファイルを検疫するには、次のいずれかのアクションを実行します。
   - **管理者検疫**処理を手動で適用します。
     
     ![検疫処理](./media/quarantine-action.png)

   - ポリシーで自動検疫処理として設定します。 

     ![自動検疫](./media/quarantine-automated.png)

3. **管理者検疫**を適用すると、バックグラウンドで次のことが行われます。

   1. 元のファイルは、設定した管理者検疫フォルダーに移動されます。
   2. 元のファイルは削除されます。
   3. 廃棄標識ファイルは元のファイルの場所にアップロードされています。
      
      ![検疫の廃棄標識](./media/quarantine-tombstone.png)
      
   4. ユーザーは、廃棄標識ファイルにのみアクセスできます。 ファイルでは、IT 担当者から提供されたカスタム ガイドラインを読み、関連付け ID を使用して IT に連絡し、ファイルをリリースすることができます。

4. ファイルが検疫されたというアラートを受け取った場合は、Cloud App Security の **[アラート]** ページでファイルを調査します。
   
   ![検疫のアラート](./media/quarantine-alerts.png)
   
5. また、**[検疫済み]** タブの **[ポリシー レポート]** も調査します。
   
   ![検閲レポート](./media/quarantine-report.png)
    
6. ファイルが検疫された場合、次の手順で脅威の状況を修復します。
    
    1. SharePoint Online の検疫済みフォルダー内にあるファイルを検査します。
    2. 監査ログで、ファイルのプロパティを詳細に調査することもできます。
    3. 会社のポリシーに反するファイルが見つかった場合は、組織のインシデント対応 (IR) プロセスを実行します。
    4. ファイルが無害である場合は、検疫からファイルを復元することができます。 その時点で、元のファイルがリリースされます。つまり、元の場所にコピーして戻され、廃棄標識が削除されて、ユーザーはファイルにアクセスできるようになります。
       
       ![検疫の復元](./media/quarantine-restore.png)
       
7. ポリシーがスムーズに実行されていることを確認します。 その後、ポリシーで自動ガバナンス アクションを使用して今後の漏えいを防ぎ、ポリシーと一致するときに管理者検疫を自動的に適用することができます。

> [!NOTE]
> ファイルが復元された場合:
> - 元の共有は復元され、既定のフォルダー継承が適用されます。
> - 復元されたファイルには、最近のバージョンのみが含まれます。
> - 検疫フォルダーのサイト アクセス管理は、お客様が行ってください。


## <a name="set-up-admin-quarantine"></a>管理者検疫を設定する

1. 違反を検出するファイル ポリシーを設定します。 この種のポリシーの例は次のとおりです。

    - SharePoint Online の分類ラベルなど、メタデータのみのポリシー
    - クレジット カード番号を検索するポリシーなど、ネイティブ DLP ポリシー 
    - Vontu を検索するポリシーなど、ICAP サードパーティ ポリシー。

2. 検疫場所を設定します。
   1. Office 365 SharePoint または OneDrive for Business の場合は、管理者検疫を設定まで、ポリシーの一部として管理者検疫にファイルを入れることはできません (![検疫設定](./media/quarantine-warning.png))。

      管理者検疫設定を指定するには、設定の歯車アイコンをクリックし、**[設定]** に移動します。 検疫されたファイルの場所と、ファイルが検疫されたときにユーザーが受信するユーザー通知を指定します。 
      ![検疫設定](./media/quarantine-settings.png)

   2. Box の場合、検疫フォルダーの場所とユーザー メッセージはカスタマイズできません。 フォルダーの場所は、Box を Cloud App Security に接続した管理者のドライブです。また、ユーザー メッセージは次の通りです:"このファイルは会社のセキュリティとコンプライアンスのポリシーに違反している可能性があるため、管理者のドライブに隔離されました。 支援が必要な場合には IT 管理者にお問い合わせください"。



## <a name="next-steps"></a>次の手順 
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
