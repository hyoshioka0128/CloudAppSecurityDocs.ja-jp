---
title: Office 365 を Cloud App Security に接続して使用状況を表示し、管理する | Microsoft Docs
description: このトピックでは、API コネクタを使用して Cloud App Security に Office 365 を接続する方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/30/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a79bf393-0d2c-44b6-8dab-86c740fd7333
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 1960d9801ad24b880bd2f4eaad3947b26d87437e
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44144467"
---
*適用対象: Microsoft Cloud App Security*



# <a name="connect-office-365-to-microsoft-cloud-app-security"></a>Office 365 を Microsoft Cloud App Security に接続する
このセクションでは、App Connector API を使用して Microsoft Cloud App Security を既存の Microsoft Office 365 アカウントに接続する手順について説明します。  
  
Cloud App Security は、従来の Office 365 専用プラットフォームと最新の Office 365 サービス (Office 365 の vNext リリース製品群と呼ばれています) に対応しています。  Cloud App Security は従来の Microsoft Business Productivity Online Standard Suite に対応していません。 

> [!NOTE]
> vNext サービス リリースは管理レベルで標準的な Office 365 サービスと多少異なる場合があります。

Cloud App Security は、次の Office 365 アプリをサポートしています。

- Office 365
- SharePoint
- OneDrive
- Teams (Teams のアクティビティがポータルで検出された後でのみ表示)
- PowerBI (PowerBI のアクティビティがポータルで検出された後にのみ表示される。監査をオンにすることが必要)
- Exchange (Exchange のアクティビティがポータルで検出された後にのみ表示される。監査をオンにすることが必要)

 
## <a name="how-to-connect-office-365-to-cloud-app-security"></a>Office 365 を Cloud App Security に接続する方法  
  
> [!NOTE]
>- Office 365 を Cloud App Security に接続するには、少なくとも 1 つの Office 365 ライセンスが割り当てられている必要があります。
>-  Office 365 で既定で有効になる Exchange 管理者監査ログでは、管理者 (または管理者特権が割り当てられているユーザー) が Exchange Online 組織で変更を加えたときに Office 365 監査ログにイベントが記録されます。 Exchange 管理センターを使用するか、Windows PowerShell でコマンドレットを実行して加えられた変更は、Exchange 管理者監査ログに記録されます。 Exchange の管理者監査ログの詳細については、「[管理者監査ログ](http://go.microsoft.com/fwlink/p/?LinkID=619225)」を参照してください。
>- Exchange メールボックスの監査ログは、Exchange Online のユーザー アクティビティをログに記録する前に、ユーザーのメールボックスごとに有効にする必要があります ([Exchange メールボックスのアクティビティ](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c)に関するページをご覧ください)。
>- Office アプリが有効になっている場合、Office 365 の一部であるグループも、特定の Office アプリから Cloud App Security にインポートされます。たとえば、SharePoint が有効になっている場合、Office 365 グループは SharePoint グループとしてもインポートされます。
>- そこからログを取得するには [PowerBI で監査を有効にする](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/)必要があります。 監査を有効にすると、Cloud App Security はログの取得を開始します (24 時間から 72 時間の遅延があります)。
> Active Directory オンプレミス環境のユーザーと自動的に同期するように Azure Active Directory が設定されている場合、オンプレミス環境の設定が Azure AD 設定をオーバーライドし、**[ユーザーの停止]** というガバナンス アクションが元に戻されます。 
 
1.  **[接続]** アプリページで、[+] ボタン、**[Office 365]** の順にクリックします。  

      ![O365 を接続する](./media/connect-0365.png) 

2.  Office 365 ポップアップで、**[Office 365 に接続する]** をクリックします。

      ![O365 を接続する](./media/office-connect.png) 
 
3.   Office 365 が正常に接続されていることが表示されたら、**[閉じる]** をクリックします。
  
> [!NOTE] 
> Office 365 を接続すると、API をプルしている Office 365 に接続されたすべてのサードパーティ製アプリケーションを含む、1 週間前のデータが表示されます。 接続前に API をプルしていなかったサードパーティ製アプリについては、既定で無効になっていたすべての API が Cloud App Security によって有効になるため、Office 365 に接続した時点からイベントが表示されるようになります。

## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  