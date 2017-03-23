---
title: "Cloud App Security でデータの匿名化によりユーザーのプライバシーを保護する | Microsoft ドキュメント"
description: "この記事では、Cloud Discovery データのユーザー名を匿名化する方法について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/19/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: eb250ede-fede-4699-a08b-b8ea4b232f07
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 72228b607c3006101f9f427b38de63b090cdb9a0
ms.sourcegitcommit: 0d4748ea2a71e6ee2b0fa1c0498d9219bfbda29a
translationtype: HT
---
## <a name="cloud-discovery-data-anonymization"></a>Cloud Discovery データの匿名化

Cloud Discovery データを匿名化することで、ユーザーのプライバシーを保護することができます。 データ ログが Cloud App Security ポータルにアップロードされると、ログはサニタイズされ、すべてのユーザー名情報が暗号化されたユーザー名に置き換えられます。 このように、すべてのクラウド アクティビティの匿名が維持されます。 必要に応じて、(セキュリティ違反や疑わしいユーザー アクティビティが発生した場合などに) 特定のセキュリティ調査を行うために、管理者は実際のユーザー名を解決することができます。 管理者は、特定のユーザーを疑う理由がある場合、既知のユーザー名の暗号化されたユーザー名を調べ、暗号化されたユーザー名を使用して調査を開始することもできます。 ユーザー名の各変換はポータルの**ガバナンス ログ**で監査されます。

重要なポイント:
-    個人情報は保存も、表示もされません。 暗号化された情報のみが保存され、表示されます。
-    個人データは、テナントごとに専用のキーで AES-128 を使用して暗号化されます。
-    ユーザー名の解決は、指定の暗号化されたユーザー名を解読することで、ユーザー名ごとに随時実行されます。


データの匿名化のしくみ:

1.    データの匿名化を適用する方法は次の&3; つです。 
    
    - [新しいスナップショット レポートを作成](create-snapshot-cloud-discovery-reports.md)し、**[Anonymize private information (個人情報の匿名化)]** を選択して、特定のログ ファイルのデータを匿名化するように設定できます。
 ![スナップショット データの匿名化](./media/anonymize-log.png)

    - 新しいデータ ソースを追加するときに **「Anonymize private information」** (個人情報の匿名化) を選択し、[新しいデータ ソースの自動アップロード](configure-automatic-log-upload-for-continuous-reports.md)に関するページを参照してデータを匿名化するように設定できます。  
 ![ログ データの匿名化](./media/anonymize-autolog.png)

    - 次のように、アップロードされたログ ファイルからのスナップショット レポートと、ログ コレクタからの継続的レポートの両方からのデータをすべて匿名化するように、Cloud App Security で既定値を設定できます。
     
        1. 「設定」 (歯車アイコン) の **[Cloud Discovery 設定]** を選択します。
     
        2. 既定でユーザー名が匿名化されるようにするには、[匿名化] タブで、**「Anonymize private information by default in new reports and data sources」** (新しいレポートとデータ ソースの個人情報を既定で匿名化する) を選択します。

        3. [暗号化キー] で、**[Use the dedicated key generated for your portal (ポータル用に生成された専用キーを使用する)]** か、**[Use a custom key (カスタム キーを使用する)]** かを選択します。 **[Use a custom key (カスタム キーを使用する)]** を選択した場合は、16 バイト UTF8 暗号化キーを入力します。
        4. **[Save]**(保存) をクリックします。
  ![匿名化](./media/anonymizer1.png)
  

2.    匿名化を選択すると、Cloud App Security はトラフィック ログを解析し、特定のデータ属性を抽出します。
3.    Cloud App Security はユーザー名を暗号化されたユーザー名に置き換えます。
4.    次に、クラウドの使用状況データを分析し、匿名化されたデータに基づいて Cloud Discovery レポートを生成します。
 ![Cloud Discovery ダッシュボードの匿名化](./media/anonymize-dashboard.png)
 

5.    異常な使用量のアラート調査など、特定の調査のために、ポータルで特定のユーザー名を解決し、業務上の正当な理由を示すことができます。 このページは、既知のユーザー名の暗号化されたユーザー名を検索する際にも使用できます。 

    1. 「設定」 (歯車アイコン) の **[Cloud Discovery 設定]** を選択します。
    2. **[匿名化]** タブの **「Anonymize and resolve usernames」** (ユーザー名の匿名化と解決) で、解決策を実行する正当な理由を入力します。
    3. **「Enter username to resolve」** (解決するユーザー名を入力してください) で、**「From anonymized」** (匿名化されたユーザー名を基にする) を選択して匿名化されたユーザー名を入力するか、**「To anonymized」** (匿名化されたユーザー名の実データを基にする) を選択して、解決する元のユーザー名を入力します。 **[解決]** をクリックします。 
![匿名化](./media/anonymizer.png)

6.    アクションはポータルの**ガバナンス ログ**で監査されます。 
![匿名化](./media/anonymize-gov-log.png)




  
      
## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
    
      
  