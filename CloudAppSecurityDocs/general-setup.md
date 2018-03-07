---
title: "Cloud App Security ポータルに組織の設定を入力し、最良の結果を得る | Microsoft Docs"
description: "この記事では、Cloud App Security に組織の情報を入力する方法について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/3/2018
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2e7e57b0-db54-4d75-896c-4700dd9abe48
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ff8f123a1bab8831071865422f8afa34e20e416b
ms.sourcegitcommit: c47fd92c71028ede8840e0766f20eb0ad2898e70
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="basic-setup"></a>基本的なセットアップ
ここでは、Cloud App Security ポータルをカスタマイズする手順について説明します。

## <a name="prerequisites"></a>前提条件 
ポータル アクセスの場合、次の IP アドレスをファイアウォールのホワイトリストに追加し、Cloud App Security ポータルにアクセスできるようにする必要があります。  
  
- 104.42.231.28  
  
> [!NOTE]  
>  URL および IP アドレスが変更されときに更新されるようにするには、「[Office 365 の URL および IP アドレス範囲](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)」で説明されているように RSS を購読します。  
  
## <a name="set-up-the-portal"></a>ポータルのセットアップ  
  
1.  Cloud App Security ポータルのメニュー バーで、設定の歯車アイコン ![設定アイコン](./media/settings-icon.png "設定アイコン") をクリックし、**[設定]** を選択して組織の詳細を構成します。     

3.  **[組織の詳細]** に自社の**組織の表示名**を指定することは重要です。 これは、システムから送信される電子メールや Web ページに表示されます。  
  
4. **環境名** (テナント) を指定します。 これは、複数のテナントを管理する場合に特に重要です。  
  
4. システムから送信される電子メールや Web ページで表示する**ロゴ**を指定することもできます。 ロゴには、150 x 50 ピクセル以下のサイズで背景が透明色の png ファイルを使用する必要があります。  

4.  **管理対象ドメイン**のリストを追加します。 これは重要な手順です。管理対象ドメインは、Cloud App Security により、内部ユーザーと外部ユーザー、およびファイルの共有の可否を判別する際に使用されるためです。 これは、レポートとアラートで使用されます。  
> [!NOTE] 
> - 内部として構成されていないドメインのユーザーは、外部として指定され、アクティビティまたはファイルをスキャンされません。

5. Azure Information Protection の統合により統合を行う場合は、「[Azure Information Protection の統合](azip-integration.md)」で詳細を確認してください。 

 >[!NOTE]
 > Azure Information Protection の統合を行うには、[Office 365 用アプリ コネクタ](connect-office-365-to-microsoft-cloud-app-security.md)を有効にする必要があります。
  
6.  ポータル設定は、この画面からいつでもバックアップできます。 **[ポータル設定をエクスポート]** をクリックすると、ポリシー規則やユーザー グループ、IP アドレス範囲などのポータル設定がすべて記述された json ファイルが作成されます。  
  
   
> [!NOTE] 
> ExpressRoute を使用している場合は、Cloud App Security は Azure に展開され、[ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/) に完全に統合されます。 検出ログのアップロードを含む、Cloud App Security アプリとのすべての通信、および Cloud App Security に送信されるトラフィックは、ExpressRoute の**パブリック ピアリング**経由でルーティングされるため、待機時間、パフォーマンス、およびセキュリティが改善されます。 お客様側で設定を行う必要はありません。 <br></br>パブリック ピアリングの詳細については、「[ExpressRoute 回線とルーティング ドメイン](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/)」を参照してください。  
    
## <a name="see-also"></a>参照  
[Cloud Discovery のセットアップ](set-up-cloud-discovery.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  