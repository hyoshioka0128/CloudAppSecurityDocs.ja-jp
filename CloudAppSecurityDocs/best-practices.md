---
title: 組織を保護するためのベストプラクティス-Cloud App Security
description: この記事では、組織を保護するための一連のベストプラクティスについて説明します。
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: best-practice
ms.date: 10/24/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: e90a340c206c0bfb1c01542dd184664d1fe87dfe
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74143467"
---
# <a name="cloud-app-security-best-practices"></a>Cloud App Security のベストプラクティス

*適用対象: Microsoft Cloud App Security*

この記事では、Microsoft Cloud App Security を使用して組織を保護するためのベストプラクティスについて説明します。 これらのベストプラクティスは、Cloud App Security と、お客様のエクスペリエンスに関する経験から得られたものです。

この記事で説明するベストプラクティスは次のとおりです。

> [!div class="checklist"]
> * [クラウドアプリの検出と評価](#discover-and-assess-cloud-apps)
> * [クラウドガバナンスポリシーを適用する](#apply-cloud-governance-policies)
> * [共有データの公開を制限し、コラボレーションポリシーを適用する](#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
> * [クラウドに格納されている規制対象の機密データを検出、分類、ラベル付け、保護する](#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
> * [クラウドに格納されているデータに DLP ポリシーとコンプライアンスポリシーを適用する](#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
> * [管理されていないデバイスまたは危険なデバイスへの機密データのダウンロードをブロックおよび保護する](#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices)
> * [リアルタイムセッション制御を適用することにより、外部ユーザーとの共同作業をセキュリティで保護する](#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls)
> * [クラウドの脅威、侵害されたアカウント、悪意のある内部関係者、ランサムウェアを検出する](#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
> * [フォレンジック調査のためにアクティビティの監査証跡を使用する](#use-the-audit-trail-of-activities-for-forensic-investigations)
> * [IaaS サービスとカスタムアプリをセキュリティで保護する](#secure-iaas-services-and-custom-apps)

## <a name="discover-and-assess-cloud-apps"></a>クラウド アプリの検出と評価

Cloud App Security と Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) を統合することで、企業ネットワークやセキュリティで保護された web ゲートウェイ以外で Cloud Discovery を使用できるようになります。 ユーザーとコンピューターの情報を組み合わせることで、危険なユーザーやコンピューターを特定し、使用しているアプリを確認し、Microsoft Defender ATP ポータルでさらに調査することができます。

**ベストプラクティス**: MICROSOFT Defender ATP を使用して Shadow IT Discovery を有効にする  
**詳細**: Cloud Discovery は、MICROSOFT Defender ATP によって収集されたトラフィックログを分析し、特定されたアプリをクラウドアプリカタログに対して評価して、コンプライアンスとセキュリティに関する情報を提供します。 Cloud Discovery を構成することにより、クラウドの使用状況、シャドウ IT、ユーザーによって使用されている承認されていないアプリの継続的な監視を把握できます。  
**詳細情報**:

* [Cloud App Security との Microsoft Defender ATP 統合](wdatp-integration.md)
* [Cloud Discovery のセットアップ](set-up-cloud-discovery.md)
* [ネットワーク内のシャドウ IT の検出と管理](tutorial-shadow-it.md)

---

**ベストプラクティス**: アプリ検出ポリシーを構成して、リスクの高い、準拠していない、およびトレンドのアプリを事前に特定します。  
**詳細**: アプリ検出ポリシーを使用すると、組織内で検出された重要なアプリケーションを追跡しやすくなり、これらのアプリケーションを効率的に管理できるようになります。 リスク、非対応、傾向、または高ボリュームとして識別された新しいアプリを検出したときにアラートを受け取るポリシーを作成します。  
**詳細情報**:

* [Cloud Discovery ポリシー](cloud-discovery-policies.md)
* [Cloud Discovery 異常検出ポリシー](cloud-discovery-anomaly-detection-policy.md)
* [瞬間的な行動分析と異常検出を取得する](anomaly-detection-policy.md)

---

**ベストプラクティス**: ユーザーによって承認された OAuth アプリを管理する  
**詳細**: 多くのユーザーが、アカウント情報にアクセスするために、サードパーティのアプリに OAuth アクセス許可を付与しています。そのため、誤って他のクラウドアプリ内のデータへのアクセスを許可することも決然たる攻撃者ます。 通常は、これらのアプリを可視化することはできません。そのため、アプリのセキュリティリスクを、提供されている生産性の利点と比較するのが難しくなります。

Cloud App Security には、ユーザーが付与したアプリのアクセス許可を調査および監視する機能が用意されています。 この情報を使用すると、疑わしい可能性のあるアプリを識別できます。危険であると判断した場合は、アクセスを禁止することができます。  
**詳細情報**:

* [OAuth アプリの管理](manage-app-permissions.md)
* [OAuth アプリのポリシー](app-permission-policy.md)

---
---
---
---

## <a name="apply-cloud-governance-policies"></a>クラウド ガバナンス ポリシーを適用する

**ベストプラクティス**: アプリにタグを付けて、ブロックスクリプトをエクスポートする  
**詳細**: 組織内で検出されたアプリの一覧を確認した後、不要なアプリの使用に対して環境をセキュリティで保護することができます。 承認**済みタグは、組織**によって承認されているアプリと **、未承認のタグが**アプリに適用できます。 検出フィルターを使用して承認されていないアプリを監視したり、オンプレミスのセキュリティアプライアンスを使用して承認されていないアプリをブロックするスクリプトをエクスポートしたりできます。 タグとエクスポートスクリプトを使用すると、安全なアプリへのアクセスのみを許可することで、アプリを整理し、環境を保護することができます。  
**詳細情報**:

* [検出されたアプリの管理](governance-discovery.md)

---
---
---
---

## <a name="limit-exposure-of-shared-data-and-enforce-collaboration-policies"></a>共有データの公開を制限し、コラボレーション ポリシーを適用する

**ベストプラクティス**: Office 365 に接続する  
**詳細**: office 365 を Cloud App Security に接続すると、ユーザーのアクティビティ、アクセスしているファイル、および office 365、SharePoint、OneDrive、Teams、Power BI、Exchange、および Dynamics のガバナンスアクションをすぐに確認できます。  
**詳細情報**:

* [アプリの接続](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)
* [Office 365 を Microsoft Cloud App Security に接続する](connect-office-365-to-microsoft-cloud-app-security.md)

---

**ベストプラクティス**: サードパーティ製アプリを接続する  
**詳細**: サードパーティ製アプリを Cloud App Security に接続することにより、ユーザーのアクティビティ、脅威検出、ガバナンス機能に関する洞察が向上します。 次のサードパーティ製アプリ Api がサポートされています:[アマゾンウェブサービス (AWS)](connect-aws-to-microsoft-cloud-app-security.md)、 [Box](connect-box-to-microsoft-cloud-app-security.md)、 [Dropbox](connect-dropbox-to-microsoft-cloud-app-security.md)、 [G Suite](connect-google-apps-to-microsoft-cloud-app-security.md)、 [Okta](connect-okta-to-microsoft-cloud-app-security.md)、 [Salesforce](connect-salesforce-to-microsoft-cloud-app-security.md)、 [ServiceNow](connect-servicenow-to-microsoft-cloud-app-security.md)、 [WebEx](connect-webex-to-microsoft-cloud-app-security.md)、および[Workday](connect-workday-to-microsoft-cloud-app-security.md)。  
**詳細情報**:

* [アプリの接続](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)

---

**ベストプラクティス**: 組織のデータの漏洩を確認する  
**詳細**: ファイル公開レポートを使用して、ユーザーがクラウドアプリでファイルを共有する方法を把握します。 次のレポートが使用可能であり、Microsoft Power BI などのツールで詳細な分析を行うためににエクスポートできます。

* **データ共有の概要**: 各クラウドアプリに格納されているアクセス許可によってファイルが一覧表示されます。
* **ドメイン別の送信共有**: 従業員が会社のファイルを共有しているドメインの一覧を表示します。
* **共有ファイルの所有者**: 外部と企業のファイルを共有しているユーザーの一覧を表示します。  
**詳細情報**:

* [データ管理レポートを生成する](built-in-reports.md)

---

**ベストプラクティス**: 個人アカウントを使用して共有を削除するポリシーを作成する  
**詳細**: office 365 を Cloud App Security に接続すると、ユーザーのアクティビティ、アクセスしているファイル、および office 365、SharePoint、OneDrive、Teams、Power BI、Exchange、および Dynamics のガバナンスアクションをすぐに確認できます。  
**詳細情報**:

* [接続されているアプリの管理](governance-actions.md)

---
---
---
---

## <a name="discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud"></a>クラウドに格納されている規制対象の機密データを検出、分類、ラベル付け、保護する

**ベストプラクティス**: Azure Information Protection との統合  
**詳細**: Azure Information Protection との統合により、分類ラベルを自動的に適用し、必要に応じて暗号化保護を追加する機能が提供されます。 統合が有効になると、ガバナンスアクションとしてラベルを適用したり、分類別にファイルを表示したり、分類レベルでファイルを調査したり、分類されたファイルが適切に処理されるように詳細なポリシーを作成したりすることができます。 統合を有効にしないと、クラウド内のファイルを自動的にスキャン、ラベル付け、暗号化する機能を利用できません。  
**詳細情報**:

* [Azure Information Protection の統合](azip-integration.md)
* [チュートリアル: Azure Information Protection 分類ラベルを自動的に適用する](use-case-information-protection.md)

---

**ベストプラクティス**: データ漏えいポリシーを作成する  
**詳細**: ファイルポリシーを使用して、情報共有を検出し、クラウドアプリの機密情報をスキャンします。 データの露出が検出されたときにアラートを生成するために、次のファイルポリシーを作成します。

* 機密データを含む外部で共有されるファイル
* 外部で共有され、**社外秘**としてラベル付けされたファイル
* 承認されていないドメインと共有されるファイル
* SaaS アプリで機密性の高いファイルを保護する

**詳細情報**:

* [コンテンツ検査](content-inspection.md)
* [ファイル ポリシー](data-protection-policies.md)
* [情報保護ポリシー](policies-information-protection.md)

---

**ベストプラクティス**: **[ファイル]** ページでレポートを確認する  
**詳細**: アプリコネクタを使用してさまざまな SaaS アプリに接続すると、Cloud App Security はこれらのアプリによって保存されたファイルをスキャンします。 さらに、ファイルが変更されるたびに、ファイルが再度スキャンされます。 **[ファイル]** ページを使用して、クラウドアプリに格納されているデータの種類を理解し、調査することができます。 調査に役立つように、ドメイン、グループ、ユーザー、作成日、拡張子、ファイル名と種類、ファイル ID、分類ラベルなどでフィルター処理できます。 これらのフィルターを使用すると、どのようにファイルを調査するかを制御し、データが危険にさらされないようにすることができます。 データがどのように使用されているかをよりよく理解したら、これらのファイル内の機密コンテンツをスキャンするポリシーを作成できます。  
**詳細情報**:

* [アプリの接続](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)
* [ファイル フィルター](file-filters.md)
* [コンテンツ検査](content-inspection.md)

---
---
---
---

## <a name="enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud"></a>クラウドに格納されているデータに DLP ポリシーとコンプライアンス ポリシーを適用する

**ベストプラクティス**: 外部ユーザーと共有されないように機密データを保護する  
**詳細**: ユーザーが**機密**分類ラベルを持つファイルを組織の外部のユーザーと共有しようとしたときに、そのガバナンスアクションを構成して外部ユーザーを削除しようとしたときに検出するファイルポリシーを作成します。 このポリシーにより、機密データが組織の外に出ることがなくなり、外部ユーザーはアクセスできなくなります。  
**詳細情報**:

* [接続されているアプリの管理](governance-actions.md)

---
---
---
---

## <a name="block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices"></a>管理されていないデバイスまたは危険なデバイスへの機密データのダウンロードをブロックおよび保護する

**ベストプラクティス**: 危険度の高いデバイスへのアクセスを管理および制御する  
**詳細**: SaaS アプリのコントロールを設定するにはアプリの条件付きアクセス制御を使用します。 セッションポリシーを作成して、危険度の高い、信頼度の低いセッションを監視できます。 同様に、管理されていないデバイスまたは危険なデバイスから機密データにアクセスしようとしているユーザーが、ダウンロードをブロックして保護するためのセッションポリシーを作成することもできます。 危険度の高いセッションを監視するためのセッションポリシーを作成しない場合、web クライアントでのダウンロードをブロックおよび保護する機能に加えて、Microsoft とサードパーティのアプリの両方で低信頼のセッションを監視する機能が失われます。  
**詳細情報**:

* [Microsoft Cloud App Security Conditional Access App Control でアプリを保護する](proxy-intro-aad.md)
* [セッション ポリシー](session-policy-aad.md)

---
---
---
---

## <a name="secure-collaboration-with-external-users-by-enforcing-real-time-session-controls"></a>リアルタイム セッション制御を適用することにより、外部ユーザーとの共同作業をセキュリティで保護する

**ベストプラクティス**: アプリの条件付きアクセス制御を使用して外部ユーザーとのセッションを監視する  
**詳細**: 環境内のコラボレーションをセキュリティで保護するために、内部ユーザーと外部ユーザーの間のセッションを監視するためのセッションポリシーを作成できます。 これにより、ユーザー間のセッションを監視し、セッションのアクティビティが監視されていることを通知できるだけでなく、特定のアクティビティも制限することができます。 アクティビティを監視するためのセッションポリシーを作成する場合は、監視するアプリとユーザーを選択できます。  
**詳細情報**:

* [Microsoft Cloud App Security Conditional Access App Control でアプリを保護する](proxy-intro-aad.md)
* [セッション ポリシー](session-policy-aad.md)

---
---
---
---

## <a name="detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware"></a>クラウドの脅威、侵害されたアカウント、悪意のある内部関係者、ランサムウェアを検出する

**ベストプラクティス**: 異常ポリシーの調整、IP 範囲の設定、アラートのフィードバックの送信  
**詳細**: 異常検出ポリシーは、すぐに使用できるユーザーとエンティティの行動分析 (UEBA) と機械学習 (ML) を提供します。これにより、クラウド環境全体で高度な脅威検出をすぐに実行できます。

異常検出ポリシーは、環境内のユーザーによって実行される異常なアクティビティがある場合にトリガーされます。 Cloud App Security は、ユーザーのアクティビティを継続的に監視し、UEBA と ML を使用してユーザーの*通常*の動作を学習し、理解します。 ポリシー設定は、組織の要件に合わせて調整できます。たとえば、ポリシーの感度を設定したり、ポリシーのスコープを特定のグループに限定したりすることができます。

* **異常検出ポリシーを調整してスコープ**を設定する: たとえば、不可能な移動アラート内の偽陽性の数を減らすには、ポリシーの感度スライダーを [低] に設定します。 組織内のユーザーが会社の旅行を頻繁に使用している場合は、それらをユーザーグループに追加し、ポリシーのスコープ内でそのグループを選択することができます。

* **Ip 範囲の設定**: ip アドレス範囲が設定されると、Cloud App Security で既知の ip アドレスを識別できます。 IP アドレス範囲を構成すると、ログとアラートの表示と調査の方法をタグ付けして分類し、カスタマイズすることができます。 IP アドレス範囲を追加することで、偽陽性の検出を減らし、アラートの精度を向上させることができます。 IP アドレスを追加しないことを選択した場合は、誤検知の数が増え、調査するアラートが表示されることがあります。

* **アラートに関するフィードバックを送信する**

    アラートを破棄または解決するときは、アラートを破棄した理由または解決方法についてフィードバックを送信してください。 この情報は、アラートを改善し、誤検知を減らすために Cloud App Security 役立ちます。

**詳細情報**:

* [瞬間的な行動分析と異常検出を取得する](anomaly-detection-policy.md)
* [IP 範囲とタグの使用](ip-tags.md)
* [Cloud App Security でのアラートの監視](monitor-alerts.md)

---

**ベストプラクティス**: 予期しない場所または国からのアクティビティの検出  
**詳細**: ユーザーが予期しない場所または国からサインインしたときに通知するアクティビティポリシーを作成します。 これらの通知は、発生前に脅威を検出して修復できるように、環境内で侵害された可能性のあるセッションを警告することがあります。  
**詳細情報**:

* [脅威保護ポリシー](policies-threat-protection.md)

---

**ベストプラクティス**: OAuth アプリポリシーを作成する  
**詳細**: oauth アプリポリシーを作成して、oauth アプリが特定の条件を満たしたときに通知します。 たとえば、高いアクセス許可レベルを必要とする特定のアプリが100人を超えるユーザーによってアクセスされた場合に通知を受け取るように選択できます。  
**詳細情報**:

* [OAuth アプリのポリシー](app-permission-policy.md)

---
---
---
---

## <a name="use-the-audit-trail-of-activities-for-forensic-investigations"></a>フォレンジック調査のためにアクティビティの監査証跡を使用する

**ベストプラクティス**: アラートを調査するときにアクティビティの監査証跡を使用する  
**詳細**: ユーザー、管理者、またはサインインアクティビティがポリシーに準拠していない場合に、アラートがトリガーされます。 アラートを調査して、環境に脅威が発生していないかどうかを把握することが重要です。

アラートを調査するには、 **[アラート]** ページでアラートを選択し、そのアラートに関連するアクティビティの監査証跡を確認します。 監査証跡を使用すると、同じ種類のアクティビティ (同じユーザー、同じ IP アドレス、および場所) を表示できるので、アラートの全体像を把握できます。 アラートによってさらなる調査が保証される場合は、組織内のこれらのアラートを解決する計画を作成します。

アラートを消去するときは、アラートが重要ではない理由を調査して理解することが重要です。 このようなアクティビティが大量にある場合は、アラートをトリガーするポリシーを確認して調整することもできます。  
**詳細情報**:

* [アクティビティ](activity-filters.md)

---
---
---
---

## <a name="secure-iaas-services-and-custom-apps"></a>IaaS サービスとカスタム アプリをセキュリティで保護する

**ベストプラクティス**: AZURE と AWS に接続する  
**詳細**: これらのクラウドストレージアプリを Cloud App Security に接続することで、脅威検出機能を向上させることができます。 これらのサービスの管理およびサインインアクティビティを監視することで、ブルートフォース攻撃の可能性、特権を持つユーザーアカウントの悪意のある使用、および環境内のその他の脅威について、検出され、通知を受けることができます。 たとえば、Vm の異常な削除や、これらのアプリでの偽装アクティビティなどのリスクを識別できます。  
**詳細情報**:

* [Azure を Microsoft Cloud App Security に接続する](connect-azure-to-microsoft-cloud-app-security.md)
* [AWS を Microsoft Cloud App Security に接続する](connect-aws-to-microsoft-cloud-app-security.md)

---

**ベストプラクティス**: AZURE と AWS のセキュリティ構成の評価を確認する  
**詳細**: Azure Security Center との統合により、Azure 環境のセキュリティ構成を評価できます。 この評価では、不足している構成とセキュリティ制御に関する推奨事項が提供されます。 これらの推奨事項を確認することで、環境内の異常や潜在的な脆弱性を特定し、Azure セキュリティポータルで関連する場所に直接移動して解決することができます。

AWS を使用すると、セキュリティ構成に関する推奨事項を把握して、クラウドのセキュリティを向上させることができます。 これらの推奨事項を使用して、AWS アカウントのコンプライアンス対応状態を監視できます。  
**詳細情報**:

* [Azure のセキュリティ構成](security-config.md)
* [AWS のセキュリティ構成](security-config-aws.md)

---

**ベストプラクティス**: カスタムアプリをオンボードする  
**詳細**: 基幹業務アプリからのアクティビティをさらに可視化するために、カスタムアプリを Cloud App Security にオンボードできます。 カスタムアプリの構成が完了すると、それらを使用している情報、使用されている IP アドレス、およびアプリとの間で送受信されるトラフィックの量が表示されます。

また、カスタムアプリをアプリの条件付きアクセス制御アプリとしてオンボードして、信頼度の低いセッションを監視することもできます。  
**詳細情報**:

* [Cloud Discovery にカスタム アプリを追加する](cloud-discovery-custom-apps.md)
* [アプリのアプリの条件付きアクセス制御をオンボードしてデプロイする](proxy-deployment-any-app.md)
