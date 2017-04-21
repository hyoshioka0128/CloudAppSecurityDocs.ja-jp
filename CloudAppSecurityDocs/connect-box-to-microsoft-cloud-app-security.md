---
title: "Box を Cloud App Security に接続して使用状況を表示し、管理する | Microsoft Docs"
description: "このトピックでは、API コネクタを使用して Cloud App Security に Box アプリを接続する方法に関する情報を提供します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/19/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b3e4713e-986f-4a5e-9fcc-f8de94dd0df7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 11716fb83acfb893dce29c7f4179788d40bef7a4
ms.sourcegitcommit: 0d4748ea2a71e6ee2b0fa1c0498d9219bfbda29a
translationtype: HT
---
# <a name="connect-box-to-microsoft-cloud-app-security"></a>Box を Microsoft Cloud App Security に接続する
このセクションでは、App Connector API を使用して Cloud App Security を既存の Box アカウントに接続する方法を説明します。  
  
## <a name="how-to-connect-box-to-cloud-app-security"></a>Box を Cloud App Security に接続する方法  
  
> [!NOTE]  
>  管理者アカウントではないアカウントを使用してデプロイすると、API テストでエラーが発生し、Cloud App Security が Box のすべてのファイルをスキャンできません。 この問題が発生する場合は、すべての特権を所有する共同管理者に協力を依頼してデプロイすることができます。しかし、引き続き API テストではエラーが発生し、他の管理者が所有している Box のファイルはスキャンできません。  
  
1.  アプリケーションへのアクセス許可を制限する場合は、この手順を実行します。 それ以外の場合は手順 2 に進みます。  
  
    -   Box 管理コンソールで設定アイコンをクリックし、次に [**Business settings (ビジネスの設定)**] をクリックします。  
  
         ![Box のビジネス設定](./media/box-business-settings.png "Box のビジネス設定")  
  
    -   [**アプリ**] タブをクリックします。  
  
         ![Box アプリ](./media/box-apps.png "Box アプリ")  
  
    -   **[Unpublished Applications]** (未公開のアプリケーション) が選択されている場合は、**[Except for]** (次を除く) テキスト ボックスに Cloud App Security アプリのシリアル番号 `nduj1o3yavu30dii7e03c3n7p49cj2qh` を追加して **[保存]** をクリックします。  
  
         ![Box の [次を除く] 設定](./media/box-settings-except-for.png "Box の [次を除く] 設定")  
  
    > [!NOTE]  
    >  既存の Adallom ユーザーの方でコンソールの URL が Cloud App Security ではなく Adallom のものである場合、このアプリのシリアル番号には bwahmilhdlpbqy2ongkl119o3lrkoshc を使用します。  
  
2.  Cloud App Security ポータルで、**[調査]**、**[接続アプリ]** の順にクリックします。  
  
3.  **[アプリ コネクター]** ページで、[+]、**[Box]** の順にクリックします。  
  
     ![Box の接続](./media/connect-box.png "Box の接続")  
  
4.  **[Box の設定]** ポップアップで、**[リンクに移動]** をクリックします。  
  
5.  Box のログオン ページが開きます。 Cloud App Security がチームの Box アプリにアクセスできるように、資格情報を入力します。  
  
6.  Cloud App Security からチームの情報やアクティビティ ログにアクセスし、任意のチーム メンバーと同様に任意のアクティビティを実行することを許可するかどうかを確認するメッセージが Box で表示されます。 続行するには、[**許可**] をクリックします。  
  
7.  Cloud App Security ポータルに戻ると、Box と正常に接続されたことを示すメッセージが届いています。  
  
8.  [**API のテスト**] をクリックして、正常に接続されたことを確認します。  
  
     テストには数分かかる場合があります。 成功通知を受信したら、 [**閉じる**] をクリックします。  
  
これで、Box が Cloud App Security に接続されました。  
 
Box を接続すると、接続までの 60 日間のイベントを受け取ります。
  
Box を接続すると、Cloud App Security がフル スキャンを実行します。 所有するファイルとユーザーの数に応じて、フル スキャンの実行に時間がかかる場合があります。 ほぼリアルタイムにスキャンできるように、アクティビティの検出対象ファイルがスキャン キューの先頭に移動されます。たとえば、編集、更新、または共有対象のファイルはすぐにスキャンされ、通常のスキャン プロセスが到達するまで待ちません。 これは本質的に変更されないファイル (表示、プレビュー、印刷またはエクスポート対象のファイルなど) には適用されません。
  
## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  