---
title: Office 365 を Cloud App Security に接続する
description: この記事では、使用状況を表示して制御するために、API コネクタを使用して Cloud App Security に Office 365 を接続する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 74b03bd9db046a7637ea84d69914d1e87b47c2ae
ms.sourcegitcommit: 445a7c208455e6ce2c4e13b028c811f4c3486290
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78342847"
---
# <a name="connect-office-365-to-microsoft-cloud-app-security"></a>Office 365 を Microsoft Cloud App Security に接続する

*適用対象: Microsoft Cloud App Security*

この記事では、App connector API を使用して Microsoft Cloud App Security を既存の Microsoft Office 365 アカウントに接続する手順について説明します。 この接続により、Office 365 の使用を可視化し、制御できます。 Cloud App Security が Office 365 を保護する方法については、「 [office 365 を保護](protect-office-365.md)する」を参照してください。
  
Cloud App Security は、従来の office 365 専用プラットフォームと、Office 365 サービス (一般に vNext リリースファミリの Office 365 と呼ばれます) の最新のオファリングをサポートしています。  Cloud App Security は、従来の Microsoft Business 生産性オンライン Standard Suite (BPOS) をサポートしていません。

> [!NOTE]
> 場合によっては、vNext サービスリリースが、標準の Office 365 オファリングの管理レベルと管理レベルで若干異なることがあります。

Cloud App Security は、次の Office 365 アプリをサポートしています。

- Dynamics 365 CRM
- Exchange (Exchange からのアクティビティがポータルで検出された後にのみ表示され、監査を有効にする必要があります)
- Office 365
- OneDrive
- 電力の自動化
- Power BI (ポータルで Power BI のアクティビティが検出された後にのみ表示され、監査を有効にする必要があります)
- SharePoint
- Skype for Business
- チーム (チームのアクティビティがポータルで検出された後にのみ表示されます)
- Yammer

> [!NOTE]
> Cloud App Security は、 [Office 365 の監査ログ](https://docs.microsoft.com/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log?view=o365-worldwide)と直接統合し、PowerApps、Forms、Sway、Stream など、**サポートされているすべてのサービス**からのすべての監査イベントを受け取ります。

## <a name="how-to-connect-office-365-to-cloud-app-security"></a>Office 365 を Cloud App Security に接続する方法  

> [!NOTE]
>
>- Office 365 を Cloud App Security に接続するには、少なくとも1つの Office 365 ライセンスが割り当てられている必要があります。
>- Cloud App Security で Office 365 活動の監視を有効にするには、 [office のセキュリティとコンプライアンスセンター](https://support.microsoft.com/help/4026501/office-auditing-in-office-365-for-admins)で監査を有効にする必要があります。
>- Office 365 で既定で有効になっている exchange 管理者監査ログは、管理者 (または管理者特権が割り当てられているユーザー) が Exchange Online の組織で変更を行ったときに、Office 365 監査ログにイベントを記録します。 Exchange 管理センターを使用するか、Windows PowerShell でコマンドレットを実行することによって行われた変更は、Exchange 管理者監査ログに記録されます。 Exchange の管理者監査ログの詳細については、「[管理者監査ログ](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log)」を参照してください。
>- Exchange Online のユーザーアクティビティがログに記録される前に、ユーザーのメールボックスごとに exchange メールボックスの監査ログをオンにする必要があります。「 [Exchange メールボックスのアクティビティ](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c)」を参照してください。
>- Office アプリが有効になっている場合は、office 365 の一部であるグループも、特定の Office アプリから Cloud App Security するためにインポートされます。たとえば、SharePoint が有効になっている場合、Office 365 グループも SharePoint グループとしてインポートされます。
>- そこからログを取得するには、 [PowerBI で監査を有効](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/)にする必要があります。 監査を有効にすると、Cloud App Security はログの取得を開始します (24-72 時間の遅延があります)。
>- そこからログを取得するには、 [Dynamics 365 で監査を有効](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-use-comprehensive-auditing#enable-auditing)にする必要があります。 監査を有効にすると、Cloud App Security はログの取得を開始します (24-72 時間の遅延があります)。
>- Azure Active Directory が Active Directory オンプレミス環境のユーザーと自動的に同期するように設定されている場合、オンプレミス環境の設定は Azure AD 設定を上書きし、 **Suspend user**ガバナンスアクションの使用は元に戻されます。
>- Azure AD サインインアクティビティの場合、Cloud App Security には、ActiveSync などのレガシプロトコルからの対話型サインインアクティビティとサインインアクティビティのみが含まれます。 非対話型のサインインアクティビティは、Azure AD 監査ログで確認できます。

1. **[接続されたアプリ]** ページで、+ ボタンをクリックし、 **[Office 365]** を選択します。

    ![接続0365](media/connect-0365.png)

2. Office 365 のポップアップで、 **[office 365 の接続]** をクリックします。

    ![接続0365](media/office-connect.png)

3. Office 365 が正常に接続された状態で表示されたら、 **[閉じる]** をクリックします。

> [!NOTE]
> Office 365 に接続すると、Api をプルしている Office 365 に接続されているサードパーティ製アプリケーションも含めて、1週間前のデータが表示されます。 接続前に Api をプルしていないサードパーティ製アプリの場合は、Office 365 に接続した時点からのイベントが表示されます。これは Cloud App Security 既定でオフになっていたすべての Api が有効になるためです。

アプリの接続で問題が発生した場合は、「[アプリコネクタのトラブルシューティング](troubleshooting-api-connectors-using-error-messages.md)」を参照してください。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
