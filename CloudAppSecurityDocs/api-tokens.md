---
title: Cloud App Security での API トークンの管理 | Microsoft Docs
description: このトピックでは、Cloud App Security 用の API トークンの生成に関して説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4f5e6b1e-6b2c-4358-98f0-945e2993d5fe
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e7ae8a06cc54eaa274b951a0762a589437c13ee0
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44142410"
---
*適用対象: Microsoft Cloud App Security*


# <a name="api-tokens"></a>API トークン
    
Microsoft Cloud App Security API を使うと、REST API エンドポイントからプログラムで Cloud App Security にアクセスできます。 アプリケーションで API を使うことにより、Cloud App Security のデータとオブジェクトに対して読み取りと更新の操作を実行できます。 たとえば、Cloud App Security API は、ユーザー オブジェクトに対する次の一般的な操作をサポートしています。

- Cloud Discovery のログ ファイルをアップロードします
- ブロック スクリプトを生成します
- アクティビティ、アラート、ポリシー レポートを一覧表示します
- アラートを無視または解決します

API の完全なドキュメントを見るには、Cloud App Security ポータルで [ヘルプ] の **[API ドキュメント]** に移動します。

API にアクセスするには、API トークンを作成し、ソフトウェアでそれを使って Cloud App Security API に接続する必要があります。

[API トークン] タブでは、テナントのすべての API トークンを管理できます。 


## <a name="generate-a-token"></a>トークンを生成する

1. **[設定]** メニューから **[セキュリティ拡張機能]**、**[API トークン]** の順に選びます。

2. プラス アイコン **[新しいトークンの生成]** をクリックし、後でトークンの識別に使う名前を指定して、**[次へ]** をクリックします。
   ![Cloud App Security が API トークンを生成する](./media/api-token-gen.png)

3. トークンの値をコピーし、回復するときのためにどこかに保存します。トークンを紛失した場合、再生成する必要があります。 トークンには、それを発行したユーザーの特権が設定されます。 たとえば、セキュリティ閲覧者は、データを変更できるトークンを発行することはできません。

4. 状態 (アクティブ、非アクティブ、生成済み) でトークンをフィルター処理できます。 

   - 生成済みは、まだ使われていないトークンです。 
   - アクティブは、生成されて過去 7 日以内に使われたトークンです。 
   - 非アクティブは、使われたことはあるが、過去 7 日以内にアクティビティがなかったトークンです。
5. 新しいトークンを生成すると、Cloud App Security ポータルへのアクセスに使用する新しい URL が与えられます。 

   ![Cloud App Security API トークン](./media/generate-api-token.png)

ジェネリック ポータル URL は引き続き機能しますが、トークンで与えられるカスタム URL に比べてかなり遅くなります。 URL を忘れた場合、メニューの **?** アイコンに移動し、 **[バージョン情報]** を選択すると表示できます。

## <a name="api-token-management"></a>API トークンの管理

[API トークン] ページには、生成されたすべての API トークンの表が含まれます。

完全な権限を持つ管理者には、このテナントに対して生成されたすべてのトークンが表示されます。 他のユーザーには、自分で生成したトークンだけが表示されます。

表では、トークンが生成された日時と最後に使われた日時に関する詳細がわかり、トークンを取り消すこともできます。 

取り消されたトークンは表から削除され、そのトークンを使っていたソフトウェアは、新しいトークンが提供されるまで API を呼び出すことができません。 

> [!NOTE]
> SIEM コネクタとログ コレクターも API トークンを使います。 これらのトークンは、ログ コレクターおよび SIEM エージェントのセクションから管理する必要があり、この表には表示されません。 





## <a name="see-also"></a>参照  
[SIEM 統合問題のトラブルシューティング](troubleshooting-siem.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  

## <a name="check-out-this-video"></a>このビデオをご覧ください。
[Microsoft Cloud App Security – REST API とトークン](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)  