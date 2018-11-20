---
title: Office 365 管理者向けの統合アプリおよび Azure AD
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 11/19/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: O365 がアプリケーションを統合する方法については登録されているし、Azure AD で管理されています。
ms.openlocfilehash: 6edf22261a40563227862908302d519a7edd6419
ms.sourcegitcommit: 7be23a03daeb42c156220efe7b2112938438ee82
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2018
ms.locfileid: "26618873"
---
# <a name="integrated-apps-and-azure-ad-for-office-365-administrators"></a>Office 365 管理者向けの統合アプリおよび Azure AD

[オンまたはオフは、[統合されたアプリケーションにすること](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114)だけでより統合されたアプリケーションを管理するのにはありません。Office 365 の REST Api の登場によって、ユーザーは、アプリケーション データへのアクセス、Office 365、メール、予定表、連絡先、ユーザー、グループ、ファイル、およびフォルダーのようなを与えることができます。既定では、ユーザーが個別に、各アプリケーションへのアクセス許可を付与する必要がありますですが、これをグローバル管理者レベルで 1 回、アプリケーションを承認し、アプリケーション起動プログラムを組織全体にロールアウトする場合にも。これを行うには、Azure AD でアプリケーションを登録する必要があります。Azure AD でアプリケーションを登録することができ、するのに役立つ背景情報を知っている必要がありますが、Office 365 の組織でのアプリケーションを管理する前に必要ないくつかの手順があります。この資料には、これらのリソースへのリンクがあります。
  
## <a name="azure-ad-resources-for-office-365-admins"></a>Azure AD 向け Office 365 の管理者

Azure AD で、Office 365 アプリケーションを管理する前にこれら 2 つの手順を実行する必要があります。
  
|**前提条件**|**コメント**|
|:-----|:-----|
|[無料の Azure Active Directory サブスクリプションの登録](https://go.microsoft.com/fwlink/?LinkId=617127) <br/> |Office 365 サブスクリプションを購入するすべてが Azure Active Directory への無料サブスクリプションを付属します。Azure AD を使用すると、アプリを管理しを作成し、ユーザーおよびグループ アカウントを管理できます。このサブスクリプションをアクティブにすると、Azure 管理ポータルへのアクセス、登録プロセスを完了する必要です。その後、Office 365 の管理センターから Azure AD に移動することができます。  <br/> |
|[統合アプリをオンまたはオフにする](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |有効にして統合されたアプリケーションで、ユーザーが Office 365 の情報にアクセスするサードパーティのアプリケーションを許可して AD の Azure でアプリケーションを登録します。などのサード ・ パーティ製アプリケーションを使用するときにそのアプリケーションがアクセス許可を要求の予定表にアクセスして、OneDrive の仕事フォルダーにあるファイルを編集するのには。  <br/> |
   
Office 365 アプリケーションを管理するには Azure AD でのアプリケーションの知識を持っている必要があります。これらの資料では、する必要がある背景を提供するのに役立ちます。
  
|**背景資料**|**コメント**|
|:-----|:-----|
|[Office 365 アプリケーション起動プログラムに対応します。](https://support.office.com/article/79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |アプリケーション起動プログラムに新しいなら、する依存関係とは何かそれを使用する方法です。アプリケーション起動プログラムが任意の場所からアプリケーションを取得するために設計された Office 365 にします。  <br/> |
|[追加、更新、およびアプリケーションの削除](https://go.microsoft.com/fwlink/?LinkId=617137) <br/> |このトピックでは、追加、更新、または Active Directory の Azure でアプリケーションを削除する方法を示します。Azure AD と統合するアプリケーションのさまざまな種類について説明しより多くの web Api などの他のリソースにアクセスするアプリケーションを構成する方法です。  <br/> |
|[Office 365 アプリケーション起動プログラムに表示されるアプリがある](https://go.microsoft.com/fwlink/?LinkId=617138)。  <br/> |Office 365 のユーザーを検索してアプリケーションへのアクセスをより容易にアプリケーションの起動プログラムです。この資料では、開発者として表示できるように、アプリケーションをユーザーのアプリケーション ランチャーで表示しても、Office 365 の資格情報を使用してシングル サインオン (SSO) エクスペリエンスを提供する方法について説明します。  <br/> |
|[Office 365 の Api プラットフォームの概要](https://go.microsoft.com/fwlink/?LinkId=617140) <br/> |Office 365 の Api では、重要事項を含む、お客様の Office 365 のデータへのアクセスを提供することができますつまり、メール、カレンダー、連絡先、ユーザー、グループ、ファイル、およびフォルダーです。Azure AD は、Office 365 アプリケーション間の関係を示していますが、この資料では適切なダイアグラムとアプリケーションにアクセスするデータです。  <br/> |
|[Azure Active Directory 内のアプリケーションを統合します。](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Azure Active Directory、およびアプリケーションの登録、登録済みのアプリケーションでは、背後にある概念を理解およびガイドラインのマルチ テナント アプリケーションのブランディングについて学習する方法と統合されているアプリケーションについて説明します。  <br/> |
|[Azure Active Directory 統合のチュートリアル](https://docs.microsoft.com/azure/active-directory/saas-apps/tutorial-list) <br/> |これらのチュートリアルの目的では、サード パーティの SaaS アプリケーションの Azure AD の SSO を構成する方法を示します。  <br/> |
|[Azure AD の認証シナリオ](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD OAuth 2.0 OpenID を接続するなどの業界標準プロトコルのサポートにより、サービスとしての id を提供することによって開発者のための認証を簡略化だけではなく、簡単にコーディングを開始するために別のプラットフォーム用のソースのライブラリを開きます。このドキュメントでは、Azure AD をサポートしを開始する方法を表示するさまざまなシナリオを理解することができます。  <br/> |
|[アプリケーションへのアクセス](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-access-management) <br/> |Azure AD により、今日の一般的なソフトウェアの多くに、サービス (SaaS) アプリケーションとして容易に統合、アイデンティティおよびアクセス管理を提供し、それらがどのようなアプリケーションへのアクセスが検出されると SSO を使用してアプリケーションにアクセスするユーザーのアクセス パネルを提供します。この資料では、Azure AD のアプリケーション アクセスの拡張機能とそれらを投稿する方法の詳細については、関連するリソースへのリンクを提供します。  <br/> |
|[Office 365 の体験をカスタマイズします。](https://support.office.com/article/eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |Office 365 アプリケーション起動プログラムでアプリケーションを切り替えることにより、毎日を使用してアプリケーションへのすばやいアクセスを取得できます。  <br/> |
   

