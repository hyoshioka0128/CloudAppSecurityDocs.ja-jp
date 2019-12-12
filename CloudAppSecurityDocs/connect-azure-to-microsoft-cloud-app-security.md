---
title: Azure を Cloud App Security に接続する
description: この記事では、使用状況を視覚化して制御できるように、API コネクタを使用して Cloud App Security に Azure を接続する方法に関する情報を提供します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: aff0d6d0b554f6b26501591bc03c1e39db789349
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74720047"
---
# <a name="connect-azure-to-microsoft-cloud-app-security"></a>Azure を Microsoft Cloud App Security に接続する

*適用対象: Microsoft Cloud App Security*

この記事では、App Connector API を使用して Microsoft Cloud App Security を既存の Azure アカウントに接続する方法を説明します。 この接続により、Azure の使用状況を視覚化して制御できるようになります。

## <a name="how-to-connect-azure-to-cloud-app-security"></a>Azure を Cloud App Security に接続する方法

> [!NOTE]
>
> - Azure を Microsoft Cloud App Security に接続するには、Azure AD のグローバル管理者である必要があります。
> - Cloud App Security には**すべての**サブスクリプションのアクティビティが表示されます。
> - 現時点では、Cloud App Security は ARM アクティビティのみを監視します。

1. **[接続アプリ]** ページで、[+] ボタン、 **[Microsoft Azure]** の順にクリックします。

    ![Azure の接続](media/connect-azure-menu.png)

2. Azure のポップアップで、 **[Connect Microsoft Azure]\(Microsoft Azure に接続\)** をクリックします。

    ![Azure の接続](media/connect-azure.png)

> [!NOTE]
> Azure を接続すると、データがプルされます。 以降のデータが表示されます。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
