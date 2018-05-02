---
title: Cloud App Security での過去の更新のアーカイブ | Microsoft Docs
description: このトピックは、Cloud App Security の過去のリリースに加えられた更新を説明するアーカイブです。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 185c3a46-ede8-4d58-b232-111807845c8f
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: f17cf637569007ea3a83e2b360f4e0516f4fe461
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2018
---
*適用対象: Microsoft Cloud App Security*


# <a name="past-release-archive-of-microsoft-cloud-app-security"></a>Microsoft Cloud App Security の過去のリリースのアーカイブ

最新情報の一覧については、「[Microsoft Cloud App Security の新機能](release-notes.md)」をご覧ください。



## <a name="updates-made-in-2017"></a>2017 に加えられた更新

### <a name="cloud-app-security-release-113"></a>Cloud App Security リリース 113
2017 年 12 月 25 日のリリース

-   Cloud App Security で Azure Information Protection との緊密な統合が可能になったことをお知らせいたします。 このパブリック プレビュー機能を使用すると、クラウド アプリのファイルをスキャンし、分類したり、Azure Information Protection ラベルを保護のために自動的に適用したりできます。 この機能は、Box、SharePoint、OneDrive で使用できます。 詳細については、[Azure Information Protection の統合](azip-integration.md)に関するページを参照してください。

-   Cloud Discovery ログ パーサーは汎用形式の LEEF、CEF、W3C 対応になりました。


### <a name="cloud-app-security-release-112"></a>Cloud App Security リリース 112
リリース日: 2017 年 12 月 10 日

-   アクティビティ ログでユーザー名または IP アドレスをクリックすると、関連する分析情報ドロワーにアクセスできるようになりました。 
-   アクティビティを調査する際、時計のアイコンをクリックすると、分析情報ドロワー内の同一期間内のすべてのアクティビティを簡単に表示できるようになりました。これにより、表示しているアクティビティの 48 時間以内に実施されたすべてのアクティビティを確認できるようになります。
-   Juniper SRX の Cloud Discovery ログ パーサーで機能強化が行われました。
-   プロキシによって監視されるアクティビティについて、**アクティビティ オブジェクト**が拡張され、DLP スキャン関連の情報が含まれるようになりました。また、一致するポリシーが拡張され、(存在する場合) DLP 違反が含まれるようになりました。


### <a name="cloud-app-security-release-111"></a>Cloud App Security リリース 111
リリース日: 2017 年 11 月 26 日

-   検出ポリシーで、アプリ タグが条件アクションやガバナンス アクションとしてサポートされるようになりました。 これにより、**人気上昇中アプリ**などの新たに検出されたアプリを、カスタム タグで自動的にタグ化できるようになります。 アプリ タグをフィルターとして使用することもできます。たとえば、“1 日で 'ウォッチリスト' 内のあるアプリのユーザーが 100 名を超えた場合に通知する” などです。

-   **時間**フィルターがさらにユーザー フレンドリになりました。

-   コンテンツ検査により、コンテンツ、メタデータ、ファイル名の区別が可能となり、そのなかから検査対象を選択できるようになります。

-   G スイートの新しいガバナンス アクションが追加されました。 共有ファイルへの**パブリック アクセスを減らす**ことができるようになりました。 これにより、一般に公開されているファイルを共有リンクでのみ使用されるように設定できます。

-   他のアプリケーションに対するすべての OKTA ログオン アクティビティが、OKTA からのアクティビティとして Cloud App Security に表示されるようになりました。 ログインが実行された対象アプリケーションに基づいて、アクティビティの**アクティビティ オブジェクト** フィールドに表示、フィルターできます。


### <a name="cloud-app-security-release-110"></a>Cloud App Security リリース 110
リリース日: 2017 年 11 月 12 日
 
-   一般提供開始: ログ コレクターの新しい展開モードのロールアウトが開始されました。 現在の仮想アプライアンス ベースの展開に加えて、新しい Docker (コンテナー) ベースのログ コレクターを、オンプレミスでも Azure でも、パッケージとして [Ubuntu マシン](discovery-docker.md)にインストールできます。 Docker を使用する場合、ホスティング マシンはお客様が所有していて、このお客様が自由にパッチを適用したり監視したりできます。
-   隅にある新しい青い疑問符を使用して、ポータルのページ内から docs.microsoft.com の関連する Cloud App Security のドキュメント ページにアクセスできるようになりました。 各リンクは状況依存のリンクで、現在のページに基づいて必要な情報にアクセスできます。
-   Cloud App Security ポータルのすべてのページからフィードバックを送信できるようになりました。 これにより、Cloud App Security チームに対して直接バグを報告したり、新機能をリクエストしたり、チームと体験を共有したりできます。
-   Cloud Discovery 機能が改善され、サブドメインを認識して、組織のクラウド使用状況を詳しく調査できるようになりました。 詳しくは、「[検出されたアプリの処理](discovered-apps.md)」をご覧ください。

### <a name="cloud-app-security-release-109"></a>Cloud App Security リリース 109
リリース日: 2017 年 10 月 29 日 

- Microsoft Cloud App Security プロキシ機能のロールアウトが開始されました。 Microsoft Cloud App Security プロキシでは、クラウド環境へのアクセスとクラウド環境内で実行されるアクティビティのリアルタイムの表示と制御を行うのに必要なツールが提供されます。 たとえば、次のように入力します。
    -   データのダウンロードをブロックして、事前にデータ リークを防ぎます。
    -   暗号化によって保護されるように、クラウドでのデータの格納とクラウドからのデータのダウンロードを強制するルールを設定します。
    -   管理されていないデバイスでの実行内容を監視できるように、保護されていないエンドポイントを把握できます。
    -   会社以外のネットワークまたは危険な IP アドレスからのアクセスを制御します。
  
  詳細については、「[プロキシによるアプリの保護](proxy-intro-aad.md)」を参照してください。

-   特定のサービス アクティビティ名に基づくフィルターの機能については、段階的にロールアウトします。 この新しいアクティビティの種類のより細かいフィルターでは、より一般的なアクティビティの種類ではなく、特定のアプリのアクティビティを監視できます。 たとえば、以前は**実行コマンド**をフィルター処理できましたが、現在では特定の EXO コマンドレットをフィルター処理できます。 アクティビティ ドロワーの **[Type (in app)]\(種類 (アプリ)\)** には、アクティビティ名も表示できます。 この機能は最終的には、アクティビティの種類のフィルターに置き換えられます。  

-   Cloud Discovery では、Cisco ASA with FirePOWER がサポートされるようになりました。 

-   ユーザー エクスペリエンスの向上のために、Discovery ユーザーと IP ページのパフォーマンスが改善されました。


### <a name="cloud-app-security-releases-105-106-107-108"></a>Cloud App Security リリース 105、106、107、108
リリース日: 2017 年 9 月/10 月
 
-   Cloud App Security に、ヨーロッパにあるデータ センターが含まれるようになりました。 米国のデータ センターに加え、ヨーロッパのデータ センターを利用することで、Cloud App Security の顧客は新規および今後のヨーロッパ標準と認証に完全に準拠できるようになります。 
-   新しいフィルターが**アプリ コネクタ** ページに追加されました。これにより、より簡単にフィルター処理を行い、洞察を深めることができます。
-   宛先 IP 情報のみを含むログ ファイルの Cloud Discovery が改善されました。
 

### <a name="cloud-app-security-release-104"></a>Cloud App Security リリース 104 
リリース日: 2017 年 8 月 27 日

-   **IP アドレスの範囲 API** を使用してスクリプトを作成することで、複数の IP 範囲を一括で追加できるようになりました。この API は、Cloud App Security ポータルのメニュー バーで、疑問符、**API ドキュメント**の順にクリックすると見つかります。 
-   Cloud Discovery は、合計トランザクションとブロックされたトランザクションの両方を提示することで、ブロックされたトランザクションがわかりやすくなりました。
-   クラウド アプリケーションが **ISO 27017** で認証されているかどうかをフィルターできるようになりました。 この新しいクラウド アプリ カタログのリスク要因によって、パブリック クラウド コンピューティング環境のユーザー情報の処理および保護のために一般的に受け入れられているコントロールとガイドラインを確立するこの認証がアプリケーション プロバイダーに含まれているかが決定されます。
- GDPR 準拠の準備に役立つように、クラウド アプリ カタログにあるクラウド アプリの GDPR 適合状況ステートメントを集めました。 まだアプリ リスクのスコアには影響しませんが、アプリ発行元の GDPR 適合状況ページのリンクを使用できます (提供されている場合)。 この内容について Microsoft は未検証であり、その有効性について責任を追いません。


### <a name="cloud-app-security-release-103"></a>Cloud App Security リリース 103 
リリース日: 2017 年 8 月 13 日

- Office ファイルの .docm、.docx、.dotm、.dotx、.xlam、.xlsb、.xlsm、.xlsx、.xltx、.xps、.potm、.potx、.ppsx、.ppsm、.pptm、.pptx、.thmx、.vsdx、.vsdm、.vssx、.vssm、.vstx、.vstm に関して、Cloud App Security が (汎用的な保護に代わり) Azure Information Protection ネイティブ保護のサポート対象になりました。

- Azure Active Directory のコンプライアンス管理者には、Cloud App Security のアクセス許可と同様のアクセス許可が自動的に与えられます。たとえば、アラートの読み取り専用アクセス、アラートの管理アクセス、ファイル ポリシーの作成許可と変更許可、ファイル ガバナンス アクションの許可が与えられ、また、[データ管理] であらゆる組み込みレポートを表示できます。 

- DLP 違反コンテキストが 40 文字から 100 文字に拡張されました。違反のコンテキストをより良く理解できます。

- Cloud Discovery のカスタム ログをアップロードすると、詳しいエラー メッセージが与えられます。ログ アップローダで発生したエラーを簡単に解決できます。

- Cloud Discovery ブロック スクリプトが拡張され、Zscaler 形式対応になりました。

- クラウド アプリ カタログの新しいリスク要因: アカウントの終了後にデータが保持されます。 クラウド アプリ内のアカウントを終了した後でデータが完全に削除されていることを確認できます。


### <a name="cloud-app-security-release-102"></a>Cloud App Security リリース 102 
リリース日: 2017 年 7 月 30 日
 
-   IP アドレスの情報はほぼすべての調査にとって非常に重要であるため、アクティビティ ドロワーでは IP アドレスについての詳細情報を見ることができます。 特定のアクティビティ内から、[IP アドレス] タブをクリックして、特定の IP アドレスに対して発生中のアラート、最近のアクティビティの傾向グラフ、場所のマップなど、IP アドレスに関する統合されたデータを表示できます。 これにより、あり得ない移動アラートを調査するときなどに簡単にドリルダウンし、IP アドレスが使われた場所、および不審なアクティビティに含まれていたかどうかを、簡単に把握できます。 また、IP アドレス ドロワーでアクションを直接実行し、IP アドレスに危険、VPN、または企業のタグを付けて、後で簡単に調査やポリシー作成を行えるようにすることもできます。 詳しくは、[IP アドレスの洞察](activity-filters.md#ip-address-insights)に関するページをご覧ください。

-   Cloud Discovery では、[自動ログ アップロード](discovery-docker.md)用に[カスタム ログ形式](custom-log-parser.md)も使えるようになりました。 これにより、Splunk サーバーなどの SIEM または他のサポートされない形式からのログのアップロードを簡単に自動化できます。 
 
-   新しいユーザー調査アクションでは、ユーザー調査への追加レベルのドリルダウンを使用できます。 **[Investigation]\(調査\)** ページから、アクティビティ、ユーザー、またはアカウントを右クリックし、新しいフィルター **[関連アクティビティの表示]**、**[関連するガバナンスの表示]**、**[関連するアラートの表示]**、**[View owned files]\(所有されているファイルの表示\)**、**[View files shared with this user]\(このユーザーと共有されているファイルの表示\)** のいずれかを適用して、さらに調査とフィルター処理を行うことができます。

-   クラウド アプリ カタログに、アカウント終了後のデータ保持のための新しいフィールドが含まれるようになりました。 このリスク要因により、クラウド アプリ内のアカウントを終了した後でデータを完全に削除できます。

-   Cloud App Security は、潜在顧客、取引先企業、キャンペーン、営業案件、プロファイル、サポート案件など、Salesforce オブジェクトに関するアクティビティの可視性が拡張されました。 たとえば、アカウント ページのアクセスの可視性では、ユーザーが異常に多数のアカウント ページを表示した場合にアラートを生成するポリシーを構成できます。 これは、Salesforce で Salesforce Event Monitoring を有効にすると Salesforce App Connector で使用できます (Salesforce Shield の一部)。

- プライベート プレビューのお客様は、Do Not Track を使用できるようになりました。 処理するアクティビティ データのユーザーを制御できるようになりました。 これにより、Cloud App Security で特定のグループを "Do Not Track " として設定することができます。 たとえば、ドイツまたは特定のコンプライアンス法によって強制されていない国にいるユーザーのすべてのアクティビティ データを処理しないようにすることができます。 これは、Cloud App Security 内のすべてのアプリ、特定のアプリ、または特定のサブアプリに実装できます。 さらに、この機能を利用して、Cloud App Security の段階的な展開を容易にできます。 この機能の詳細、またはこの機能のプライベート プレビューへの参加については、サポートまたはアカウント担当者にお問い合わせください。 



### <a name="cloud-app-security-release-100"></a>Cloud App Security リリース 100 
リリース日: 2017 年 7 月 3 日
 

#### <a name="new-features"></a>新機能
-   **セキュリティ拡張機能:** セキュリティ拡張機能は、API トークン管理、SIEM エージェント、外部 DLP コネクタを含む、Cloud App Security のすべてのセキュリティ拡張機能を一元的に管理するための新しいダッシュボードです。 新しいダッシュ ボードは、Cloud App Security の [設定] にあります。 
    - API トークン －RESTful API を使用してサード パーティ製ソフトウェアに Cloud App Security を統合するための、自分の [API トークン](api-tokens.md)を生成し、管理します。 
    - SIEM エージェント – 以前は [SIEM 統合](siem.md)が [設定] のすぐ下にありましたが、セキュリティ拡張機能のタブとして使用できるようになりました。
    - 外部 DLP (プレビュー) – Cloud App Security では、データ損失防止 (DLP) ソリューションのような[サードパーティ製分類システムの既存の投資を活用](icap-stunnel.md)できるようになり、環境内で実行されている既存の展開を使用してクラウドのアプリケーションの内容をスキャンできるようになりました。 プレビューに参加するには、アカウント管理者に連絡してください。 
-   **自動的な承認/非承認:** 新しいアプリ検出ポリシーにより、Cloud Discovery がアプリに承認/非承認のラベルを自動的に設定できるようになりました。 これにより、組織のポリシーや規制に違反しているアプリを自動的に特定し、そのようなアプリに生成したブロック スクリプトを追加できるようになります。
-   **Cloud App Security ファイル ラベル:** Cloud App Security ファイル ラベルを適用して、スキャンされるファイルの内容をより詳しく把握できるようになりました。 Cloud App Security DLP でスキャンされるファイルごとに、ファイルの暗号化または破損によってファイルの検査がブロックされていないかどうかがわかるようになりました。 たとえば、アラートを生成するポリシーを設定して、外部で共有されているパスワード保護されたファイルの検疫を行うことができます。 この機能は 2017 年 7 月 3 日以降にスキャンされたファイルで使用できます。

    このようなファイルは、フィルターの、**[Classification labels]\(分類ラベル\)** > **[Cloud App Security]** を使用すると、フィルター処理できます。 
    - **[Azure RMS encrypted]\(Azure RMS 暗号化\)** – Azure RMS 暗号化が設定されているために内容が検査されなかったファイル。
    - **[Password encrypted]\(パスワード暗号化\)** – ユーザーによってパスワード保護されているために内容が検査されなかったファイル。
    - **[Corrupt file]\(ファイルの破損\)** – 内容の読み取りができなかったため、内容が検査されなかったファイル。
-   **ユーザーの洞察**: 調査機能がアップグレードされ、アクション中のユーザーに関するそのまま利用可能な洞察が可能になりました。 ユーザーが接続している場所、ユーザーに関連する未処理のアラートの件数とそのメタデータ情報など、アクティビティ ドロワーにあるユーザーの包括的な概要をワンクリックで見ることができます。
-   **アプリ コネクタの洞察:** **[アプリ コネクタ]** の下の、接続されている各アプリのテーブルにアプリ ドロワーが含まれるようになり、アプリの状態のドリルダウンが簡単になりました。 提供される詳細には、アプリ コネクタに接続された日時、およびコネクタの前回のヘルス チェックの日時が含まれています。 アプリごとに、DLP で検査されたファイルの合計数やリアルタイム スキャンのステータス (要求されたスキャンと実際のスキャン) など、DLP スキャンの状態を監視することもできます。 リアルタイムで Cloud App Security がスキャンしたファイルの割合が要求された数を下回っているかどうか、テナントがその容量を超え、DLP の結果で遅延が生じる可能性があるかどうかも確認できます。
-   **クラウド アプリ カタログのカスタマイズ:** 
    - **アプリ タグ**: アプリのカスタム タグを作成できるようになりました。 これらのタグは、調査する特定の種類のアプリをより詳しく調べるためのフィルターとして使うことができます。 たとえば、カスタム ウォッチ リスト、特定の事業単位への割り当て、“法務により承認済み” のようなカスタム承認などです。
    - **カスタム ノート**: 環境全体で検出されたさまざまなアプリケーションをレビューして評価する際に、結論と洞察をメモに保存できるようになりました。
    - **カスタム リスク スコア**: アプリのリスク スコアを上書きできるようになりました。 たとえば、アプリのリスク スコアが 8 で、そのアプリが組織で却下されている場合、その組織に対してリスク スコアを 10 に変更することができます。 誰かがそのアプリをレビューしたときに変更の理由をクリアにするためのノートも追加できます。
-   **新しいログ コレクターの展開モード:** 新しい展開モードがロールアウトされ、ログ コレクターで使用できるようになりました。 現在の仮想アプライアンス ベースの展開に加えて、新しい Docker (コンテナー) ベースのログ コレクターを、パッケージとしてオンプレミスと Azure の Windows および Ubuntu マシンにインストールできます。 Docker を使用する場合、ホスティング マシンはお客様が所有していて、このお客様が自由にパッチを適用したり監視したりできます。

#### <a name="announcements"></a>お知らせ: 
-   クラウド アプリ カタログは、15,000 以上の探索可能なアプリをサポートしています。
-   コンプライアンス: Cloud App Security は Azure によって SOC1/2/3 を正式に認定されています。 認定の完全な一覧については、「[Compliance Offerings](https://www.microsoft.com/trustcenter/compliance/complianceofferings)」(コンプライアンスの提供内容) を参照し、Cloud App Security で結果をフィルターしてください。

#### <a name="other-improvements"></a>その他の機能強化: 
-   **解析の向上:** Cloud Discovery のログ解析メカニズムで機能強化が行われました。 内部エラーが発生する可能性が大幅に低下しました。
-   **使用できるログ形式:** Cloud Discovery のログに使用できるログ形式の例として、Syslog 形式と FTP 形式の両方が提供されるようになりました。
-   **ログ コレクターのアップロード状態:** ログ コレクターの状態をポータルで確認し、ポータル内ステータス通知とシステム アラートを使用して、より早くエラーのトラブルシューティングができるようになりました。


### <a name="cloud-app-security-release-99"></a>Cloud App Security リリース 99 
リリース日: 2017 年 6 月 18 日

#### <a name="new-features"></a>新機能

- 不審なユーザー アクティビティのアラートと危険な状態のアカウントを素早く効果的に修復するために、ユーザーが Office 365 と Azure AD のすべてのアプリに再度ログインしなければならなくなりました。 新しいガバナンスは、ポリシー設定と、[ユーザーの停止] オプションの横にあるアラート ページで確認できます。
- アクティビティ ログの **[Add impersonation role assignment]\(偽装ロール割り当ての追加\)** アクティビティをフィルター処理できるようになりました。 このアクティビティでは、管理者が **[Application Impersonation]\(アプリケーション偽装\)** ロールをユーザーまたはシステム アカウントに付与した場合に、コマンドレット **New-ManagementRoleAssignment** を使用して検出することができます。 このロールにより、偽装者が、偽装者のアカウントに関連付けられたアクセス許可ではなく、偽装したアカウントに関連付けられているアクセス許可を使用して操作を実行できるようになります。
  Cloud Discovery の機能強化:
- Cloud Discovery のデータを、Azure Active Directory のユーザー名データを使用して強化できるようになりました。 この機能を有効にすると、検出トラフィック ログで受け取ったユーザー名が Azure AD のユーザー名と照合され、置き換えられることで、次の新機能が有効になります。
  - Azure Active Directory のユーザーによるシャドウ IT の使用を調査できます。
  - 検出されたクラウド アプリの使用と API で収集されたアクティビティを関連付けることができます。
  - Azure AD ユーザー グループに基づくカスタム ログを作成できるようになります。 たとえば、特定のマーケティング部門のシャドウ IT レポートなどです。
- Juniper の syslog パーサーの機能強化が行われました。 welf および sd-syslog 形式がサポートされるようになりました。
- Palo Alto パーサーの機能強化が行われ、アプリケーションの検出精度が向上しました。
- ログが正常にアップロードされていることを確認するため、Cloud App Security ポータルで、ログ コレクターの状態を閲覧できます。 

#### <a name="general-improvements"></a>全般的な改善点:
-   組み込みの IP アドレス タグとカスタム IP タグの階層が考慮され、カスタム IP タグが組み込みの IP タグよりも優先されるようになりました。 たとえば、脅威インテリジェンスに基づいてある IP アドレスに **[危険]** のタグが付いているが、**[企業]** と識別されているカスタム IP タグがある場合、カスタム カテゴリおよびタグが優先されます。


### <a name="cloud-app-security-release-98"></a>Cloud App Security リリース 98 
リリース日: 2017 年 6 月 4 日
 
Cloud Discovery の更新内容:
-   検出されたアプリに高度なフィルター処理を実行して、検出された特定の種類のアプリからのアップロード トラフィックの量や、検出されたアプリの特定のカテゴリを使用したユーザーの数など、使用状況に基づいたアプリのフィルター処理のような詳細な調査を実行できるようになりました。 また、左側のパネルで複数選択を実行して、複数のカテゴリを選択できるようになりました。 
-   "非対応のクラウド記憶域アプリ" のようなよく使用される検索に基づいた、Cloud Discovery の新しいテンプレートがロールアウトされました。 これらの基本フィルターをテンプレートとして使用することで、検出されたアプリの分析を実行することができます。
-   複数のアプリの承認/非承認のようなアクションが 1 回で実行できるようになり、使いやすさが向上しました。
-   Azure Active Directory ユーザー グループに基づいてカスタム検出レポートを作成するための機能がロールアウトされました。 たとえば、マーケティング部門のクラウドの使用状況を確認したい場合は、ユーザー グループのインポート機能を使用してマーケティング グループをインポートして、このグループにカスタム レポートを作成できます。

新機能:
-   セキュリティ閲覧者の RBAC のロールアウトが完了しました。この機能では、管理者に付与したアクセス許可を Cloud App Security コンソール内で管理できます。 既定で、Azure Active Directory と Office 365 の全体管理者とセキュリティ管理者はいずれも、ポータル内でフル アクセス許可を持っています。また、Azure Active Directory と Office 365 のセキュリティ閲覧者はいずれも、Cloud App Security 内で読み取り専用アクセス権を持ちます。 [アクセスの管理] オプションを使用することで、管理者を追加したり、アクセス許可を上書きしたりできます。 詳細については、「[Managing admin access](manage-admins.md)」 (管理アクセス許可の管理) を参照してください。
-   Microsoft インテリジェント セキュリティ グラフによって検出された危険な IP アドレスの詳細な脅威インテリジェンス レポートがロールアウトされました。アクティビティがボットネットによって実行されると、そのボットネット名が (存在する場合は) 表示され、特定のボットネットに関する詳細なレポートへのリンクが示されます。
 
### <a name="cloud-app-security-release-97"></a>Cloud App Security リリース 97
リリース日: 2017 年 5 月 24 日

#### <a name="new-features"></a>新機能
-   ファイルおよびポリシー違反を調査します。[ファイル] ページにポリシーの一致がすべて表示されます。 さらに、ファイルのアラート ページが改善され、特定のファイルの履歴が別のタブとして含まれるようになったため、特定のファイルのすべてのポリシーの違反履歴をドリルダウンすることができます。 すべての履歴イベントに、アラート発生時のファイルのスナップショットが含まれています。 ファイルが削除または検疫されたかどうかが示されます。
-   Office 365 SharePoint および OneDrive for Business のファイルのプライベート プレビューで、[管理者検疫](use-case-admin-quarantine.md)を実行できるようになりました。 この機能では、ポリシーに一致するファイルの検疫、またはファイルを検疫してユーザーの SharePoint ディレクトリから削除するか、選択した管理者検疫の場所に元のファイルをコピーするかの、検疫の自動アクションの設定が可能になります。
        
#### <a name="cloud-discovery-improvements"></a>Cloud Discovery の機能強化

-   Cloud Discovery の Cisco Meraki ログのサポートが改善されました。
-   Cloud Discovery の機能強化を提案するオプションにより、新しいリスク要因を提案できるようになりました。
-   カスタム ログ パーサーが改善され、日付と時刻の設定を分離することによりログ形式がサポートされ、タイムスタンプの設定オプションが提供されるようになりました。
-   Azure Active Directory ユーザー グループに基づいてカスタム検出レポートを作成するための機能がロールアウトされました。 たとえば、マーケティング部門のクラウドの使用状況を確認したい場合は、ユーザー グループのインポート機能を使用してマーケティング グループをインポートして、このグループにカスタム レポートを作成できます。

**その他の更新内容**

-   Cloud App Security で、Office 365 監査ログでサポートされている Microsoft Power BI アクティビティがサポートされるようになりました。 この機能は、徐々にロール アウトされていきます。 [Power BI ポータルでこの機能を](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/)有効にする必要があります。
-   アクティビティ ポリシーで、接続されているすべてのアプリのユーザーに実行される通知および一時停止アクションを設定できるようになりました。 たとえば、接続されているアプリでユーザーがログインを複数回失敗した場合に、常にユーザーの管理者に通知し、そのユーザーを即座に一時停止するようなポリシーを設定できます。
 
### <a name="oob-release"></a>OOB リリース
-   世界中で広がっているランサムウェアに迅速に対応するため、Cloud App Security チームは、WannaCrypt の署名拡張子が含まれる新しい[潜在的ランサムウェア アクティビティの検出ポリシー](use-case-ransomware.md) テンプレートをポリシーに追加しました。 このポリシーは直ちに設定することをお勧めします。

### <a name="cloud-app-security-release-96"></a>Cloud App Security リリース 96
リリース日: 2017 年 5 月 8 日

新機能:

-   セキュリティ閲覧者アクセス許可の段階的なロールアウトが継続されます。これにより、Cloud App Security コンソール内で管理者に付与するアクセス許可を管理できます。 既定で、Azure Active Directory と Office 365 の全体管理者とセキュリティ管理者はいずれも、ポータル内でフル アクセス許可を持っています。また、Azure Active Directory と Office 365 のセキュリティ閲覧者はいずれも、Cloud App Security 内で読み取り専用アクセス権を持ちます。 詳細については、「[Managing admin access](manage-admins.md)」 (管理アクセス許可の管理) を参照してください。
-   CSV ベースのログ用のユーザー定義ログ パーサーについて、Cloud Discovery サポートのロールアウトを完了しました。 Cloud App Security に付属するツールを使用して、どの列がどのデータに対応するかを示すことで、以前はサポートされていなかったアプライアンス用のパーサーを構成できます。 詳細については、「[カスタム ログ パーサーの使用](custom-log-parser.md)」を参照してください。

機能強化:

-   Cloud Discovery で Juniper SSG アプライアンスがサポートされるようになりました。
-   Cloud Discovery の Cisco ASA ログのサポートが改善され、可視性が強化されました。
-   Cloud App Security ポータル テーブルで一括処理をより簡単に実行し、複数のレコードを選択できるようになりました。ページの長さが長くなり、一括処理が改善されました。
-   Salesforce データに対して、**[ドメイン別の送信共有]** および **[共有ファイルの所有者]** 組み込みレポートを実行できるようになりました。
-   追加の Salesforce アクティビティのロールアウトを開始しており、アクティビティ データから抽出した興味深い情報を追跡できるようにしています。 たとえば、アカウント、潜在顧客、案件、さまざまな興味深い Salesforce オブジェクトの表示と編集が含まれます。
-   Exchange 用に新しいアクティビティが追加され、ユーザーのメールボックスまたはメールボックス フォルダーに付与されたアクセス許可を監視できるようになりました。 たとえば、次のようなアクティビティです。
    -   受信者のアクセス許可を追加する
    -   受信者のアクセス許可を削除する
    -   メールボックス フォルダーのアクセス許可を追加する
    -   メールボックス フォルダーのアクセス許可を削除する
    -   メールボックス フォルダーのアクセス許可を設定する

    たとえば、他のユーザーのメールボックスに対して **SendAs** アクセス許可が付与されたユーザーを監視し、その結果としてそのユーザー名で電子メールを送信できるようになりました。


### <a name="cloud-app-security-release-95"></a>Cloud App Security リリース 95
リリース日: 2017 年 4 月 24 日

**更新内容**
- **[アカウント]** ページは更新され、リスクをより簡単に検知できるようになりました。 内部アカウントおよび外部アカウントのフィルター処理が簡単になり、ユーザーに管理者権限が割り当てられているかどうかがひとめでわかるようになり、各アカウントでアプリごとにアクションを簡単に実行できるようになりました (アクセス許可の削除、ユーザーのコラボレーションの削除、ユーザーの停止など)。 また、アカウントごとにインポートされた[ユーザー グループ](user-groups.md)が表示されます。 

- Microsoft の職場アカウント (Office 365 や Azure Active Directory) の場合、Cloud App Security は、さまざまなユーザー識別子 (プロキシ アドレス、エイリアス、SID、および単一アカウント下でのその他の識別子) をグループ別に分類します。 アカウントに関連するエイリアスはすべて、プライマリ電子メール アドレスの下に表示されます。 ユーザー識別子の一覧に基づき、アクターがユーザー識別子であるアクティビティの場合はアクターがプライマリ ユーザー名 UPN (ユーザー プリンシパル名) として表示されます。 UPN に基づいて、グループが割り当てられ、ポリシーが適用されます。 これにより、アクティビティの調査機能が強化され、関連するすべてのアクティビティが、同じセッションに融合され、異常の検出およびグループ ベースのポリシーの適用が行われます。 この機能は来月中に徐々に展開されます。

- ブラウザー使用の組み込みレポートに、考えられるリスク要因としてロボット タグが追加されました。 これで、ブラウザーの使用が期限切れとしてタグ付けされることに加えて、ブラウザーの使用がロボットによって実行された日時を確認できます。 
- コンテンツ検査ファイル ポリシーを作成すると、一致件数が 50 件以上のファイルのみを含めるようにフィルターを設定できます。



### <a name="cloud-app-security-release-94"></a>Cloud App Security リリース 94
リリース日: 2017 年 4 月 2 日

**新機能:**
-   Cloud App Security は、Azure RMS と統合されました。 Cloud App Security ポータルから直接、Microsoft Rights Management を使用して Office 365 OneDrive および Sharepoint Online のファイルを保護できます。 これは **[ファイル]** ページから行います。 詳細については、[Azure Information Protection との統合](azip-integration.md)に関するページを参照してください。 その他のアプリケーションは今後のバージョンでサポートされるようになります。
-   これまでは、ロボットやクローラーのアクティビティが自分のネットワーク上で発生しても、そうしたアクティビティはそのネットワークのユーザーによるものではないため、認識するのは非常に困難でした。 気づかぬうちに、ロボットやクローラーがお使いのコンピューターで悪意のあるツールを実行していることもありえます。 そこで Cloud App Security では、ロボットやクローラーがお使いのネットワークでアクティビティを実行していることがわかるツールを提供します。 新しいユーザー エージェント タグを使用して、アクティビティ ログのアクティビティをフィルター処理することができます。 ユーザー エージェント タグでは、ロボットによって実行されるすべてのアクティビティをフィルター処理することができ、それを使用して、この種のアクティビティが検出されるたびに通知するポリシーを作成することができます。 このリスクを伴うアクティビティが、異常検出アラートの埋め込みとして今後のリリースに追加されたら、お知らせします。 
-   新しい統合されたアプリのアクセス許可ページでは、ユーザーがサード パーティのアプリに与えた権限をより簡単に調査することができます。 **[調査]** > **[アプリのアクセス許可]** とクリックすると、ユーザーによってサード パーティのアプリに与えられたアクセス許可のすべてを一覧表示することができます。接続されているアプリごとにアプリのアクセス許可のページが表示されており、さまざまなアプリと付与されたアクセス許可をわかりやすく見比べることができます。  詳細については、[アプリのアクセス許可の管理](manage-app-permissions.md)に関するページを参照してください。
-   テーブル ドロワーから直接データをフィルター処理して、調査を簡単にすることができます。
**アクティビティ ログ**では、調査プロセスにおけるピボット操作をはるかに簡単にする新しいコンテキスト アクションで、**[ファイル]** テーブルと **[アプリのアクセス許可]** ページが強化されました。 構成ページへのクイック リンクと、シングル クリックでデータをコピーする機能も追加しました。 詳細については、[ファイルおよびアクティビティ ドロワーの作業](file-filters.md)に関する情報を参照してください。
-   Microsoft Teams to Office 365 アクティビティ ログおよびアラートのロールアウトのサポートは完了しました。
 



### <a name="cloud-app-security-release-93"></a>Cloud App Security リリース 93
リリース日: 2017 年 3 月 20 日

**新機能:**
-   インポートされたユーザー グループの追加または除外に対してポリシーを適用できるようになりました。 
-   Cloud App Security Anonymization により、カスタム暗号化キーを構成できるようになりました。 詳細については、[Cloud Discovery の匿名化](cloud-discovery-anonymizer.md)に関するページを参照してください。
-   ユーザーとアカウント管理の制御を強化するために、**[アカウント]** ページの中から各ユーザーの横にある歯車アイコンをクリックすることで、各ユーザーとそのアカウントの Azure AD アカウント設定に直接アクセスできるようになりました。 これにより、高度なユーザー管理機能、MFA の構成、ユーザー サインインの詳細およびサインインをブロックする機能に簡単にアクセスできるようになりました。 
-   Cloud App Security API を通じて、承認されていないアプリをブロックするスクリプトをエクスポートできるようになりました。 メニュー バーの疑問符をクリックして、Cloud App Security ポータルの API の詳細と、それに続く **API のドキュメント** を参照してください。
-   ServiceNow 用 Cloud App Security アプリ コネクタは、ジュネーブ、ヘルシンキ、イスタンブールで導入されているのと同様に、OAuth トークンについてもサポートされるようになりました。 これにより、ServiceNow への API 接続がより堅牢になり、ユーザーのデプロイに依存することがなくなりました。 詳細については、「[ServiceNow を Microsoft Cloud App Security に接続する](connect-servicenow-to-microsoft-cloud-app-security.md)」を参照してください。 既存のお客様は、ServiceNow App コネクタのページで設定を更新できます。
-   サード パーティ製の DLP を追加で構成した場合は、各コネクタの状態が独立して表示され、DLP のスキャン状態が見やすくなっています。
-   Cloud App Security で、Office 365 監査ログでサポートされている Microsoft Teams アクティビティがサポートされるようになりました。 この機能は、徐々にロール アウトされていきます。
-   Exchange Online の偽装イベントについては、代理、管理者、または代理管理者の中から、使用するアクセス許可レベル別にフィルター処理ができるようになりました。**[アクティビティ オブジェクト]** > **[項目]** を検索することで、関心のある偽装レベルのイベントを **[アクティビティ ログ]** で検索して表示できるようになりました。
-   Office 365 アプリの **[アプリの権限]** タブのアプリ ドロワーで、各アプリの**発行元**を確認できるようになりました。 また、発行元をフィルターとして使用して、同一の発行元からアプリが追加された際に、そのアプリを調査することもできます。
-   危険な IP アドレスが、一般的な**場所**のリスク要因として重み付けされるのではなく、独立したリスク要因として表示されるようになりました。 
-   Azure Information Protection ラベルがファイルで無効になると、無効になったラベルは Cloud App Security でも無効であると表示されます。 無効になったラベルは表示されません。
 
**その他の Salesforce サポート:**
-   Cloud App Security で、Salesforce のユーザー停止、および停止の解除ができるようになりました。 これは、Salesforce Connector の **[アカウント]** タブで、特定のユーザーの行の末尾にある歯車アイコンをクリックして、**[一時停止]** または **[一時停止を解除]** を選択することで実行できます。また、ポリシーの一部のガバナンス アクションとして適用することもできます。 Cloud App Security で実行された一時停止のアクティビティおよび一時停止の解除のアクティビティはすべて、[ガバナンス ログ](governance-actions.md)でログに記録されます。 
-   Salesforce コンテンツ共有の可視性が向上: パブリックに共有されているファイル、グループで共有されているファイル、Salesforce ドメイン全体で共有されているファイルを含め、どのファイルが誰に共有されたかを確認できるようになりました。 この可視性の向上は Salesforce アプリの中で新しいアプリおよび現在のアプリに遡及的にロール アウトされていきます。1 回目の更新が行われるまで時間がかかる場合があります。
-   次の Salesforce イベントの対象範囲を広げ、**[ユーザーの管理]** アクティビティから分離しました。 
    - アクセス許可の編集
    - ユーザーの作成
    - ロールの変更
    - パスワードの再設定

### <a name="cloud-app-security-release-90-91-92"></a>Cloud App Security リリース 90、91、92
2017 年 2 月のリリース

**特別なお知らせ**

Cloud App Security が、ISO、HIPAA、CSA STAR、EU モデル条項などの Microsoft コンプライアンスで正式に認定されました。 認定の完全な一覧については、「[Microsoft Compliance Offerings](https://www.microsoft.com/trustcenter/compliance/complianceofferings)」 (Microsoft コンプライアンスの提供内容) に移動し、Cloud App Security を選択してください。

**新機能**

-  **ユーザー グループのインポート (プレビュー)** API コネクタを使用してアプリを接続するときに、Cloud App Security を使用して Office 365 および Azure Active Directory からユーザー グループをインポートできるようになりました。 インポートしたユーザー グループを利用する一般的なシナリオには、HR のユーザーが閲覧するドキュメントの調査、経営グループ内で通常とは異なるイベントが発生していないかのチェック、管理者グループのユーザーが米国外でアクティビティを実行していないかのチェックなどがあります。 詳細および手順については、[ユーザー グループのインポート](user-groups.md) を参照してください。

-  アクティビティ ログでは、特定のユーザーによって実行されたアクティビティ、および特定のユーザーに対して実行されたアクティビティを表示するように、ユーザーとグループ内のユーザーをフィルター処理できます。 たとえば、ユーザーが他のユーザーに偽装したアクティビティや、他のユーザーによってユーザーが偽装されたアクティビティを調査できます。 詳細については、「[アクティビティ](activity-filters.md)」を参照してください。

- **[ファイル]** ページでファイルを調査するときに特定のファイルの **[グループ作業者]** をドリルダウンすると、グループ作業者が内部ユーザーか外部ユーザーか、作成者か閲覧者か (ファイルのアクセス許可)、グループとのファイルの共有日時などの詳細を確認したり、グループのメンバーである全ユーザーを表示したりできます。 これにより、グループ メンバーが外部ユーザーかどうかを確認できます。

-  IPv6 のサポートがすべてのアプライアンスで利用できるようになりました。

-   Cloud Discovery で Baracuda アプライアンスがサポートされるようになりました。

-   Cloud App Security のシステム アラートが SIEM 接続エラーに対応しました。 詳細については、「[SIEM の統合](siem.md)」を参照してください。

-   Cloud App Security で、次のアクティビティのサポートが含まれるようになりました。

     **Office 365、SharePoint/OneDrive**: アプリケーションの構成の更新、グループからの所有者の削除、サイトの削除、フォルダーの作成

     **Dropbox**: グループへのメンバーの追加、グループからのメンバーの削除、グループの作成、グループ名の変更、チーム メンバー名の変更

     **Box**: グループからのアイテムの削除、アイテムの共有の更新、グループへのユーザーの追加、グループからのユーザーの削除


### <a name="cloud-app-security-release-89"></a>Cloud App Security リリース 89
2017 年 1 月 22 日のリリース

**新機能**
-   Microsoft では、Cloud App Security で Office 365 セキュリティとコンプライアンス センターの DLP イベントを表示するための機能のロールアウトを開始します。 Office 365 セキュリティとコンプライアンス センターで DLP ポリシーを構成した場合、ポリシーの条件に一致するものが検出されると、Cloud App Security アクティビティ ログでそれを確認できます。 アクティビティ ログの情報には、ポリシーの条件との一致を引き起こしたファイルまたはメール、またはそれらがポリシーの条件に一致したことを示すアラートが含まれます。 **セキュリティ イベント** アクティビティを使用すると、Cloud App Security アクティビティ ログに含まれる Office 365 DLP ポリシーの条件との一致を確認することができます。 この機能を使用すると、次のことができます。
    -   Office 365 DLP エンジンに由来するすべての DLP の条件との一致項目を確認します。
    -   特定のファイル、SharePoint サイト、またはポリシーについて、Office 365 DLP ポリシーの条件との一致を通知します。
    -   さまざまなコンテキストで DLP ポリシーの条件との一致を調査します (たとえば、DLP ポリシーの条件との一致をトリガーしたファイルにアクセスまたはファイルをダウンロードした外部のユーザー)。
 
-   アクティビティの説明が改善され、わかりやすさと一貫性が向上しました。 各アクティビティにフィードバック ボタンが追加されました。理解できない内容やご質問がある場合は、このボタンを利用して Microsoft までお知らせください。 
 
**機能強化**  
- ファイルのすべての外部ユーザーを削除するための新しい管理アクションが Office 365 に追加されました。 たとえば、この機能を利用すると、**内部専用分類を使用してファイルから外部共有を削除する**ポリシーを実装できます。
- SharePoint Online での外部ユーザーの識別機能が向上しました。 "外部ユーザー" グループに対してフィルターを適用すると、app@"sharepoint" システム アカウントは表示されなくなります。



### <a name="cloud-app-security-release-88"></a>Cloud App Security リリース 88
2017 年 1 月 8 日のリリース
 
**新機能**
- SIEM を Cloud App Security に接続します。 SIEM エージェントを構成することで目的の SIEM にアラートとアクティビティを自動的に送信できるようになりました。 パブリック プレビューとして利用できるようになりました。  完全なドキュメントおよび詳細については、「Integrating with SIEM」 (SIEM との統合) を参照してください。
- Cloud Discovery で IPv6 がサポートされるようになりました。 Palo Alto および Juniper のサポートをロールアウトしました。今後のリリースでは、さらにアプライアンスがロールアウトされる予定です。
 
**機能強化**
- Cloud App Catalog には、新たなリスク要因が存在します。 アプリがユーザー認証を必要とするかどうかに基づいてアプリを評価できるようになりました。 認証を強制し、匿名の使用を許可しないアプリのリスク スコアは、より正常性が高くなります。
- 新しいアクティビティの説明をロールアウトして、使いやすさと一貫性を向上します。 アクティビティを検索する場合は、この影響を受けません。
- ユーザー デバイスの識別機能を強化しました。これにより、Cloud App Security は、デバイス情報を使用して多くのイベントをより具体的に示すことができます。

## <a name="updates-made-in-2016"></a>2016 に加えられた更新
 
### <a name="cloud-app-security-release-87"></a>Cloud App Security リリース 87
リリース日: 2016 年 12 月 25 日

**新機能**
-   ユーザーのプライバシーを保護した状態で、Cloud Discovery をご利用いただけるように、[データの匿名化](cloud-discovery-anonymizer.md)を順次適用しています。 データの匿名化は、ユーザー名情報を暗号化することによって実行されます。
-   Cloud App Security から追加のアプライアンスへのブロック スクリプトのエクスポート機能を順次適用しています。 このスクリプトを使用すれば、未承認アプリへのトラフィックをブロックし、シャドウ IT を簡単に減らすことができます。 以下に対してこのオプションを使用できるようになりました。 
    -   BlueCoat ProxySG
    -   Cisco ASA
    -   Fortinet
    -   Juniper SRX
    -   Palo Alto
    -   Websense
-   ファイルまたはフォルダーに設定されている固有のアクセス許可を削除し、ファイルが親からアクセス許可を強制的に継承するように指定できる新しいファイル ガバナンス アクションが追加されました。 このファイル ガバナンス アクションでは、ファイルまたはフォルダーのアクセス許可を親フォルダーから継承するように変更できます。 
-   "外部" という新しいユーザー グループが追加されました。 これは、内部ドメインに含まれないユーザーをすべて含めるために Cloud App Security で事前構成された既定のユーザー グループです。 このユーザー グループをフィルターとして使用することができます。たとえば、外部ユーザーによって実行されるアクティビティを検索することができます。
-   Cloud Discovery 機能で Sophos Cyberoam アプライアンスがサポートされるようになりました。
 
**バグ修正**
-   SharePoint Online および OneDrive for Business ファイルが、個人ではなく内部として、[ファイル] ページおよびファイル ポリシー レポートに表示されていました。 これは修正されました。
 


### <a name="cloud-app-security-release-86"></a>Cloud App Security リリース 86
リリース日: 2016 年 12 月 13 日

**新機能**
- すべての Cloud App Security スタンドアロン ライセンスで、全般設定から Azure Information Protection スキャンを有効にできるようになりました (ポリシーの作成は不要)。 
 
**機能強化**
- ファイル名のファイル フィルターと、ファイルとポリシーの MIME 型フィルターで "or" を使用できるようになりました。 これにより、PII でポリシーを作成する際に「"passport" OR "driver"」などと入力できるようになり、ファイル名に "passport" または "driver" を含むファイルがすべて一致します。 
- 既定では、DLP コンテンツ検査ポリシーの実行時に、違反と見なされたデータがマスクされます。 違反の最後の 4 文字のマスクを解除できるようになりました。 

**細かな改善点**
- ルールの転送およびメールボックスの委任アクセス許可の追加や削除にかかわる、Office 365 (Exchange) 関連のイベントが新しくなりました。
- 新しいイベントでは、Azure Active Directory の新しいアプリに対する同意の許可が監査されます。 




### <a name="cloud-app-security-release-85"></a>Cloud App Security リリース 85
リリース日: 2016 年 11 月 27 日

**新機能**
- 承認済みアプリと接続アプリが区別されるようになりました。 承認と非承認はタグになりました。タグは、アプリ カタログの検出されたアプリと任意のアプリに適用できます。 接続アプリは、API コネクタを使用して接続されたアプリで、可視性と管理性が向上しました。 承認または非承認としてアプリにタグを付けられるようになりました。また、可能な場合はアプリ コネクタを使用してアプリを接続できるようになりました。 
 
- この変更の一環で、承認済みアプリ ページは再設計された **[接続アプリ]** ページで置き換えられ、コネクタに関する状態データは別のページに表示されるようになりました。 
 
- ログ コレクターは **[設定]** メニューの **[ソース]** で行を指定して簡単にアクセスできるようになりました。 
- アクティビティ ポリシー フィルターを作成するときに、同じユーザーが同じ対象オブジェクトに対して実行した反復されるアクティビティを無視するように選択することで、誤検出を減らすことができるようになりました。たとえば、同じユーザーが同じファイルを何度もダウンロードしようとしても、アラートはトリガーされません。 
- アクティビティ ドロワーが改善されました。 アクティビティ ドロワーでアクティビティ オブジェクトをクリックして、詳細情報をドリルダウンできるようになりました。

**機能強化**
- あり得ない移動アラートなど、異常検出エンジンが改善され、アラートの説明で IP 情報を確認できるようになりました。
- 同じフィルターを複数回追加して、フィルターされた結果を微調整できるように複合フィルターが改善されました。 
- 見やすさを改善するため、Dropbox のファイル アクティビティとフォルダー アクティビティが分けられました。 
  
**バグ修正**
- 誤検出が生成されるシステム アラート メカニズムのバグが修正されました。

### <a name="cloud-app-security-release-84"></a>Cloud App Security リリース 84
リリース日: 2016 年 11 月 13 日

**新機能**
-   Cloud App Security で、Microsoft Azure Information Protection Azure がサポートされるようになりました。これには、統合の強化と自動プロビジョニングも含まれます。 ファイルをフィルター処理し、タグのセキュリティ分類を使用してファイル ポリシーを設定した後、表示する分類ラベルを設定できます。 ラベルは、分類が組織内のユーザーまたは別のテナント (外部) のユーザーによって設定されたものかどうかも示します。 Azure Information Protection の分類ラベルに基づいてアクティビティ ポリシーを設定し、Office 365 で分類ラベルの自動スキャンを有効化することもできます。 このすばらしい新機能を活用する方法の詳細については、「[Azure Information Protection の統合](azip-integration.md)」を参照してください。
 
**機能強化**
- Cloud App Security のアクティビティ ログでは、以下の点が強化されました。 
  -    Security and Compliance Center からの Office 365 イベントが、Cloud App Security に統合され、**アクティビティ ログ**に表示されるようになりました。
  -    Cloud App Security のすべてのアクティビティは、管理者アクティビティとして Cloud App Security アクティビティ ログに登録されます。
- ファイルに関連したアラートの調査に役立てるため、ファイル ポリシーによって生じる各アラートに、一致するファイル上で実行されたアクティビティのリストを表示できるようになりました。
- 小さなテナントに対してより良いサポートを提供するため、異常検出エンジンでのあり得ない移動アルゴリズムが改善されました。 
 
**細かな改善点**
-   **アクティビティのエクスポート制限**が 10,000 に引き上げられました。 
-   Cloud Discovery 手動ログのアップロード プロセスで**スナップショット レポート**を作成すると、ログの処理にかかる正確な予想時間を受け取れるようになりました。 
-   ファイル ポリシーの**削除コラボレーター** ガバナンス アクションがグループで機能するようになりました。
-   **[アプリの権限]** ページにも細かな改善が加えられています。 
-   Office 365 に接続するアプリへのアクセス許可が付与されたユーザーが 10,000 を超えると、リストの読み込みが遅くなっていました。 これが修正されました。
-   **アプリ カタログ**に Payment Card Industry (PCI) に関する属性が追加されました。


### <a name="cloud-app-security-release-83"></a>Cloud App Security リリース 83
リリース日: 2016 年 10 月 30 日

**新機能**
-   [アクティビティ ログ](activity-filters.md)と[ファイル ログ](file-filters.md)のフィルター処理を簡略化するために、類似するフィルターが統合されました。 アクティビティ フィルターは、アクティビティ オブジェクト、IP アドレス、およびユーザーに使用します。 対象を厳密に検索するには、[コラボレーター] ファイル フィルターを使用します。
-   アクティビティ ログ ドロワーの **[ソース]** で、**[View raw data]** (生データの表示) リンクをクリックすると、アクティビティ ログの生成用の生データをダウンロードし、アプリ イベントをより詳細に調べることができます。 
-   Okta の別のログイン アクティビティのサポートが追加されました。 [プライベート プレビュー]
-   Salesforce の別のログイン アクティビティのサポートが追加されました。 

**機能強化**
-   Cloud Discovery のスナップショットのレポート機能とトラブルシューティングの使いやすさが向上しました。
-   複数アプリでのアラートをまとめたアラート リストの見やすさが向上しました。
-   Cloud Discovery の継続的レポートを新規に作成する場合の使いやすさが向上しました。
-   ガバナンス ログの使いやすさが向上しました。



### <a name="cloud-app-security-release-82"></a>Cloud App Security リリース 82
リリース日: 2016 年 10 月 9 日

**機能強化**

- アクティビティ **Change email** (電子メールを変更する) および **Change password** (パスワードを変更する) は、Salesforce の汎用的な **Manage users** (ユーザーを管理する) アクティビティから独立しました。
- SMS の 1 日あたりのアラート制限を明確にしました。 1 日 (UTC) あたり、1 つの電話番号について最大 10 個のメッセージが送信されます。
- Safe Harbor に代わる Privacy Shield の Cloud Discovery 属性に、新しい証明書が追加されました (米国のベンダーのみに関係します)。
- API コネクタのエラー メッセージに問題の修復を容易にするトラブルシューティングが追加されました。
- Office 365 サードパーティ製アプリのスキャンの更新頻度が向上しました。
- Cloud Discovery ダッシュボードが改良されました。
- Checkpoint Syslog パーサーが強化されました。
- サードパーティ製アプリの禁止と禁止解除に関するガバナンス ログが改善されました。
 
**バグ修正**
 
- ロゴのアップロードのプロセスが改善されました。
 
### <a name="cloud-app-security-release-81"></a>Cloud App Security リリース 81
リリース日: 2016 年 9 月 18 日

**機能強化**
- Cloud App Security が Office 365 のファーストパーティ アプリになりました。 今後は、1 回のクリックで Office 365 を Cloud App Security に接続できます。

- ガバナンス ログの表示が新しくなりました。アクティビティ ログとファイルのテーブルと同じ明確で便利な表示にアップグレードされました。 新しいフィルターを使用して、必要なものを簡単に検索し、管理アクションを監視できます。 
- 複数のログイン失敗とその他のリスク要因に関する異常検出エンジンの機能強化が行われました。
- Cloud Discovery のスナップショットのレポート機能強化が行われました。
- アクティビティ ログの管理アクティビティが改善されました。パスワードの変更、ユーザーの更新、パスワードのリセットが、管理アクティビティとしてアクティビティが実行されたかどうかを示すようになりました。
- システム アラートのアラート フィルターが改善されました。 
- アラート内のポリシーのラベルがポリシー レポートにリンクするようになりました。
- Dropbox のファイルに所有者が指定されていない場合、設定されている受信者に電子メール通知が送信されます。 
- Cloud App Security がサポートする言語が 24 個追加され、全部で 41 の言語をサポートするように拡張されました。  


### <a name="cloud-app-security-release-80"></a>Cloud App Security リリース 80
リリース日: 2016 年 9 月 4 日 

**機能強化**
- DLP スキャンが失敗した場合、Cloud App Security がファイルをスキャンできなかった理由が提供されるようになりました。 詳細については、「[コンテンツ検査](https://aka.ms/aka.ms/cas-contentinspection)」をご覧ください。
- あり得ない移動アラートの改善など、異常検出エンジンの機能強化が行われました。
- アラート消去エクスペリエンスが改善されました。フィードバックを Cloud App Security の検出の向上に使用できるように、アラートが役に立ったかどうかとその理由を Cloud App Security チームに伝えられるフィードバックも追加されました。
- Cisco ASA Cloud Discovery パーサーが改善されました。
- Cloud Discovery ログの手動アップロードの完了時に、電子メール通知を受け取るようになりました。
   



### <a name="cloud-app-security-release-79"></a>Cloud App Security リリース 79
リリース日: 2016 年 8 月 21 日 

**新機能**

- **新しい Cloud Discovery ダッシュボード**  
組織におけるクラウド アプリの利用状況を詳細に理解できるように設計されている新しい Cloud Discovery ダッシュボードを使用できるようになりました。 使用されているアプリの種類、未処理のアラート、組織のアプリのリスク レベルをひとめで確認できます。 また、組織の上位アプリ ユーザーがわかり、アプリの本社の場所の地図が提供されます。
新しいダッシュボードには、データをフィルターで絞り込むためのさまざまなオプションがあります。最も関心のある項目に基づき、特定のビューを生成できます。グラフィックスはわかりやすく、全体像がひとめでわかります。

- **新しい Cloud Discovery レポート**: Cloud Discovery の結果を見るため、スナップショット レポートと継続レポートの 2 種類のレポートを生成できるようになりました。
スナップショット レポートは、ファイアウォールやプロキシから手動でアップロードするトラフィック ログのセットに対するアドホックな可視性を提供します。 継続レポートには、Cloud App Security のログ コレクターを使用してネットワークから転送されるすべてのログの結果が表示されます。 これらの新しいレポートでは、すべてのデータの向上した可視性、Cloud App Security の機械学習異常検出エンジンによって識別される異常な使用の自動識別、堅牢で詳細なポリシー エンジンを使用して定義された異常な使用の識別が提供されます。 詳細については、「[Cloud Discovery セットアップ](set-up-cloud-discovery.md)」をご覧ください。
 
**機能強化**
- [ポリシー]、[全般設定]、[メールの設定] の各ページの一般的な使いやすさが改善されました。
- アラート テーブルでは、読まれたアラートと読まれていないアラートを簡単に区別できるようになりました。 読まれたアラートは、既に読んだことがわかるように左側に青い線が付いてグレー表示になります。
- アクティビティ ポリシーの **[反復アクティビティ]** パラメーターが更新されました。 
- アカウント] ページにユーザーの **[種類]** 列が追加され、各ユーザーのユーザー アカウントの種類を確認できるようになりました。 ユーザーの種類はアプリ固有です。 
- OneDrive と SharePoint のファイル関連のアクティビティに、ほぼリアルタイムのサポートが追加されました。 ファイルが変化すると、Cloud App Security はほぼ瞬時にスキャンをトリガーします。


### <a name="cloud-app-security-release-78"></a>Cloud App Security リリース 78
リリース日: 2016 年 8 月 7 日

**機能強化**
- 特定のファイルから、右クリックして 「**Find related**」 (関連項目を検索) を選択できるようになりました。 アクティビティ ログからは、ターゲット オブジェクト フィルターを使用した後、特定のファイルを選択できます。

- Juniper と Cisco ASA の追加など、Cloud Discovery のログ ファイル パーサーが機能強化されました。
- Cloud App Security では、アラートを消去するときに、アラート向上のためのフィードバックを提供できるようになりました。 アラートを消去する理由 (関心がない、似たアラートが多すぎる、実際の重要度が低い、アラートが正確ではない、など) を伝えることにより、Cloud App Security のアラート機能の品質向上に役立ちます。
ファイル ポリシー ビューで、ファイルを表示すると、またはファイル ドロアーを開くと、一致したポリシーへの新しいリンクが追加されます。 それをクリックすると、すべての一致を表示し、すべてを消去できるようになりました。 
- ユーザーが属する組織単位が、すべての関連するアラートに追加されるようになりました。
- ログの手動アップロードの処理完了を知らせる電子メール通知が送信されるようになりました。


### <a name="cloud-app-security-release-77"></a>Cloud App Security リリース 77
リリース日: 2016 年 7 月 24 日

**機能強化**
- Cloud Discovery の [エクスポート] ボタン アイコンが使いやすくなりました。
- アクティビティを調査するとき、ユーザー エージェントが解析されない場合、生データを参照できるようになりました。
- 異常検出エンジンに 2 つの新しいリスク要因が追加されました。 
    - Cloud App Security は、リスクの計算の一部として、ボットネットに関連付けられた IP アドレス タグと匿名 IP アドレスを使うようになりました。 
    - 高ダウンロード率に対して Office 365 のアクティビティが監視されるようになりました。 Office 365 のダウンロード率が、組織または特定ユーザーの通常のダウンロード率よりはるかに高い場合、異常検出アラートがトリガーされます。 
- Cloud App Security は、Dropbox の新しい [Secure Sharing 機能](https://blogs.dropbox.com/dropbox/2016/06/new-dropbox-productivity-tools/) API と互換性を持つようになりました。 
- 検出ログ解析エラーの詳細が追加されました (クラウド関連のトランザクションがない、すべてのイベントが古い、破損したファイル、ログ形式不一致など)。
- アクティビティ ログ日付フィルターが強化され、時刻でフィルター処理する機能が追加されました。
- IP アドレス範囲ページが使いやすくなりました。
- Cloud App Security に Microsoft Azure Information Protection (プレビュー バージョン) のサポートが含まれるようになりました。 ファイルをフィルター処理し、タグのセキュリティ分類を使用してファイル ポリシーを設定した後、表示する分類ラベルのレベルを設定できます。 ラベルは、分類が組織内のユーザーまたは別のテナント (外部) のユーザーによって設定されたものかどうかも示します。 



### <a name="cloud-app-security-release-76"></a>Cloud App Security リリース 76
リリース日: 2016 年 7 月 10 日

**機能強化**

- 組み込みレポートのユーザーのリストをエクスポートできるようになりました。
- 集計アクティビティ ポリシーの使いやすさが向上しました。
- TMG W3C ファイアウォール ログ メッセージ パーサーのサポートが強化されました。
- ファイル ガバナンス アクション ドロップダウンの使いやすさが改善されました。コラボレーション、セキュリティ、調査の各アクションに分離されるようになりました。
- Exchange Online のメール送信アクティビティのあり得ない移動の検出が向上しました。
- [アラート] ページと [ポリシー] ページの先頭に新しいタイトル リスト (階層リンク) が追加され、ナビゲーションが容易になりました。

**バグ修正:**
- ファイル ポリシーの DLP 設定のクレジット カードの事前設定された式が、All: Finance: Credit Card に変更されました。


### <a name="cloud-app-security-release-75"></a>Cloud App Security リリース 75
リリース日: 2016 年 6 月 27 日


**新機能:**
* レポート、共有リンク、コンテンツ配布、権限を借用したログイン、その他の詳細情報を提供するイベントなど、サポートされる Salesforce のイベントが追加されました。
* Cloud App Security ダッシュボードの接続されたアプリ アイコンが、過去 30 日間を反映するように、ダッシュボードに表示されるアプリの状態と合わせられました。
* 全画面がサポートされるようになりました。


**バグ修正:**
* SMS アラートの電話番号が、入力時に検証されるようになりました。

### <a name="cloud-app-security-release-74"></a>Cloud App Security リリース 74
リリース日: 2016 年 6 月 13 日
* アラート画面は、すべてのユーザー アクティビティ、アクティビティの地図、関連するユーザー ガバナンス ログ、アラートがトリガーされた理由、ユーザー ページから取得したその他のグラフや地図などの詳細な情報をひとめで確認できるように更新されました。 
* Cloud App Security で生成されたイベントには、イベントの種類、形式、ポリシー グループ、関連するオブジェクト、およびその説明が含まれるようになりました。
* Office 365 ProPlus、OneNote、Office Online および Exchange Online Protection に新しい IP アドレス タグが追加されました。
* メイン検出メニューからログをアップロードするオプションが追加されました。
* IP アドレス カテゴリのフィルターが改良されました。 null の IP アドレス カテゴリの名前が [未分類] という名前になり、また IP アドレスのデータが含まれないアクティビティすべてを含む [No value (値なし)] という名前の新しいカテゴリが追加されました。
* Cloud App Security のセキュリティ グループが、Active Directory のセキュリティ グループとの混同を避けるためにユーザー グループという名称になりました。
* IP アドレスごとにフィルターを適用し、IP アドレスが含まれないイベントをフィルターで除外できるようになりました。 
* アクティビティ ポリシーおよびファイル ポリシーとの一致が検出されたときに送信される通知メールの設定が変更されました。 通知の CC に受信者のメール アドレスを追加できるようになりました。


### <a name="cloud-app-security-release-73"></a>Cloud App Security リリース 73
リリース日: 2016 年 5 月 29 日

* アラート機能の更新: メールによって送信またはテキスト メッセージとして送信するように、ポリシーごとにアラートを設定することができます。
* アラート ページ: より高度な解決オプションとインシデント管理を有効にするために、デザインが向上されました。
* ポリシーの調整: アラートに基づいてより簡単に微調整できるように、アラート解決オプションから直接ポリシー設定ページに移動できるようになりました。
* お客様のフィードバックに基づいて、異常検出リスク スコアの計算が向上され、誤検知の割合が削減されました。
* アクティビティ ログのエクスポートに、イベント ID、イベント カテゴリ、およびイベントの種類名が含まれるようになりました。
* ポリシー作成のガバナンス アクションの外観と使いやすさが向上しました。
* Office 365 の簡略化された調査とコントロール - Office 365 の選択は、自動的に Office 365 スイートの一部であるすべてのアプリを選択します。
* 通知が、接続済みのアプリに設定されているメール アドレスに送信されるようになりました。 
* 接続エラーにおいて、エラーの詳細な説明が、クラウド アプリによって提供されるようになりました。
* ファイルがポリシーに一致すると、ファイルにアクセスするための URL は、ファイル ドロアーで提供されるようになりました。
* アクティビティ ポリシーまたは異常検出ポリシーからアラートがトリガーされると、新しい詳細な通知がされ、一致に関する情報を提供します。 
* アプリ コネクタが切断されると、自動化されたシステム アラートがトリガーされます。
* アラート ページ内から 1 つのアラートまたはアラートの一括選択を破棄または解決できるようになりました。

### <a name="cloud-app-security-release-72"></a>Cloud App Security リリース 72
リリース日: 2016 年 5 月 15 日

*  全般的な外観とインフラストラクチャの強化。次のとおりです。
    * Cloud Discovery 手動ログのアップロード プロセスを使用して、さらにアシスタンスを提供する新しい図。
    * ファイルが追加のレビューを必要とすることを知らせ、データが利用可能になると通知を受けるポップアップなど、不明な ("その他") ログ ファイルを更新するプロセスの向上。
    * 更新されたブラウザーとオペレーティング システムのアクティビティとファイル ログを調査するときに、より多くのアクティビティとファイルの違反が強調表示されます。
* Cisco ASA、Cisco FWSM、Cisco Meraki および W3C の追加など、Cloud Discovery ログ ファイル パーサーが向上されました。
* Cloud Discovery の既知の問題の改善。
* 新しいアクティビティ フィルターが、所有者のドメインと内部/外部の所属に追加されました。
* 任意の Office 365 オブジェクト (ファイル、フォルダー、URL) を検索できるように、新しいフィルターが追加されました。
* 異常検出ポリシーの低リスク スコアを構成する機能が追加されました。
* ポリシーに違反したときに送信されるようにアラートを設定した場合、警告する必要のある最低限のセキュリティ レベルを設定できます。 これに組織の既定の設定を使用するように選択し、組織の既定値として特定のアラート設定を設定できます。

### <a name="see-also"></a>参照  

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  