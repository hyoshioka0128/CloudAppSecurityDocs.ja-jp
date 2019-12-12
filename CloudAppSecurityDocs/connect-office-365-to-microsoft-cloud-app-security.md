---
title: Office 365 を Cloud App Security に接続する
description: この記事では、使用状況を視覚化して制御できるように、API コネクタを使用して Cloud App Security に Office 365 を接続する方法に関する情報を提供します。
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
ms.openlocfilehash: 86126d40279acd433066cc76db101061f1a03a93
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74720060"
---
# <a name="connect-office-365-to-microsoft-cloud-app-security"></a>Office 365 を Microsoft Cloud App Security に接続する

*適用対象: Microsoft Cloud App Security*

この記事では、App Connector API を使用して Microsoft Cloud App Security を既存の Microsoft Office 365 アカウントに接続する手順について説明します。  この接続により、Office 365 の使用状況を視覚化して制御できるようになります。
  
Cloud App Security は、従来の Office 365 専用プラットフォームと最新の Office 365 サービス (Office 365 の vNext リリース製品群と呼ばれています) に対応しています。  Cloud App Security は、従来の Microsoft Business Productivity Online Standard Suite (BPOS) に対応していません。 

> [!NOTE]
> vNext サービス リリースは管理レベルで標準的な Office 365 サービスと多少異なる場合があります。

Cloud App Security は、次の Office 365 アプリをサポートしています。

- Office 365
- SharePoint
- OneDrive
- Teams (Teams のアクティビティがポータルで検出された後でのみ表示)
- PowerBI (PowerBI のアクティビティがポータルで検出された後にのみ表示される。監査をオンにすることが必要)
- Exchange (Exchange のアクティビティがポータルで検出された後にのみ表示される。監査をオンにすることが必要)
- Dynamics 365

## <a name="how-to-connect-office-365-to-cloud-app-security"></a>Office 365 を Cloud App Security に接続する方法  

> [!NOTE]
>- Office 365 を Cloud App Security に接続するには、少なくとも 1 つの Office 365 ライセンスが割り当てられている必要があります。
>- Cloud App Security で Office 365 活動の監視を有効にするには、 [office のセキュリティとコンプライアンスセンター](https://support.microsoft.com/help/4026501/office-auditing-in-office-365-for-admins)で監査を有効にする必要があります。
>- Office 365 で既定で有効になる Exchange 管理者監査ログでは、管理者 (または管理者特権が割り当てられているユーザー) が Exchange Online 組織で変更を加えたときに Office 365 監査ログにイベントが記録されます。 Exchange 管理センターを使用するか、Windows PowerShell でコマンドレットを実行して加えられた変更は、Exchange 管理者監査ログに記録されます。 Exchange の管理者監査ログの詳細については、「[管理者監査ログ](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log)」を参照してください。
>- Exchange メールボックスの監査ログは、Exchange Online のユーザー アクティビティをログに記録する前に、ユーザーのメールボックスごとに有効にする必要があります ([Exchange メールボックスのアクティビティ](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c)に関するページをご覧ください)。
>- Office アプリが有効になっている場合、Office 365 の一部であるグループも、特定の Office アプリから Cloud App Security にインポートされます。たとえば、SharePoint が有効になっている場合、Office 365 グループは SharePoint グループとしてもインポートされます。
>- そこからログを取得するには [PowerBI で監査を有効にする](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/)必要があります。 監査を有効にすると、Cloud App Security はログの取得を開始します (24 時間から 72 時間の遅延があります)。
>- そこからログを取得するには、 [Dynamics 365 で監査を有効](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-use-comprehensive-auditing#enable-auditing)にする必要があります。 監査を有効にすると、Cloud App Security はログの取得を開始します (24 時間から 72 時間の遅延があります)。
>- Active Directory オンプレミス環境のユーザーと自動的に同期するように Azure Active Directory が設定されている場合、オンプレミス環境の設定が Azure AD 設定をオーバーライドし、 **[ユーザーの停止]** というガバナンス アクションが元に戻されます。
>- Azure AD サインインアクティビティの場合、Cloud App Security には、ActiveSync などのレガシプロトコルからの対話型サインインアクティビティとサインインアクティビティのみが含まれます。 非対話型のサインインアクティビティは、Azure AD 監査ログで確認できます。

1. **[接続]** アプリページで、[+] ボタン、 **[Office 365]** の順にクリックします。  

      ![O365 を接続する](media/connect-0365.png) 

2. Office 365 ポップアップで、 **[Office 365 に接続する]** をクリックします。

      ![O365 を接続する](media/office-connect.png) 

3. Office 365 が正常に接続されていることが表示されたら、 **[閉じる]** をクリックします。

> [!NOTE]
> Office 365 を接続すると、API をプルしている Office 365 に接続されたすべてのサードパーティ製アプリケーションを含む、1 週間前のデータが表示されます。 接続前に API をプルしていなかったサードパーティ製アプリについては、既定で無効になっていたすべての API が Cloud App Security によって有効になるため、Office 365 に接続した時点からイベントが表示されるようになります。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
