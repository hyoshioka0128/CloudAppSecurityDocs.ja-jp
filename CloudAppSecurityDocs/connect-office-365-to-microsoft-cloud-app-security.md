---
title: "Office 365 の接続 | Microsoft Docs"
description: "このトピックでは、API コネクタを使用して Cloud App Security に Office 365 を接続する方法について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/26/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a79bf393-0d2c-44b6-8dab-86c740fd7333
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6beb9041b338406fb5b16f4bd045dbdc4592c6d9
ms.openlocfilehash: e0ca79daddaaa2cdcbc51308653b3ec05da1b5e2


---

# <a name="connect-office-365-to-microsoft-cloud-app-security"></a>Office 365 を Microsoft Cloud App Security に接続する
このセクションでは、App Connector API を使用して Cloud App Security を既存の Microsoft Office 365 アカウントに接続する手順について説明します。  
  
  

## <a name="how-to-connect-office-365-to-cloud-app-security"></a>Office 365 を Cloud App Security に接続する方法  
  
> [!NOTE]
>- Office 365 を Cloud App Security に接続するには、少なくとも 1 つの Office 365 ライセンスが割り当てられている必要があります。
>-  Office 365 で既定で有効になる Exchange 管理者監査ログでは、管理者 (または管理者特権が割り当てられているユーザー) が Exchange Online 組織で変更を加えたときに Office 365 監査ログにイベントが記録されます。 Exchange 管理センターを使用するか、Windows PowerShell でコマンドレットを実行して加えられた変更は、Exchange 管理者監査ログに記録されます。 Exchange の管理者監査ログの詳細については、「[管理者監査ログ](http://go.microsoft.com/fwlink/p/?LinkID=619225)」を参照してください。
>- Exchange メールボックスの監査ログは、Exchange Online のユーザー アクティビティがログに記録される前にユーザーのメールボックスごとに有効にする必要があります (「[Exchange メールボックスのアクティビティ](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c)」を参照)。
>- Office アプリが有効になっている場合、Office 365 の一部であるグループも特定の Office アプリで作成されます。たとえば、SharePoint が有効になっている場合、Office 365 グループは SharePoint で作成されます。
 
1.  **[接続]** アプリページで、[+] ボタン、**[Office 365]** の順にクリックします。  

2.  Office 365 ポップアップで、[Office 365 に接続する] をクリックします。

      ![O365 を接続する](./media/connect-0365.png) 
 
3.  [今すぐテスト] をクリックして Office 365 への接続をテストします。 テストには数分かかる場合があります。
  
    ![O365 のテスト接続](./media/o365-test-connection.png) 
 
4.   Office 365 が正常に接続されていることが表示されたら、**[閉じる]** をクリックします。
  
     ![接続されている O365](./media/o365-connected.png) 

> [!NOTE] 
> Office 365 を接続すると、API をプルしている Office 365 に接続されたすべてのサードパーティ製アプリケーションを含む、1 週間前のデータが表示されます。 接続前に API をプルしていたサードパーティ製アプリケーションについては、既定で無効になっていたすべての API が Cloud App Security によって有効になるため、Office 365 に接続した時点からイベントが表示されるようになります。

## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->


