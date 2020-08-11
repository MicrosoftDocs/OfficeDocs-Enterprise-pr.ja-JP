---
title: Microsoft 365 管理者向けの統合アプリおよび Azure AD
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection: M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: Azure AD で Office 365 統合アプリを登録および管理する方法について説明します。これにより、グローバル管理者レベルでアプリの承認が可能になります。
ms.openlocfilehash: 66b552848e53b8a93ccffdef11e17c897f30e44f
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606363"
---
# <a name="integrated-apps-and-azure-ad-for-microsoft-365-administrators"></a>Microsoft 365 管理者向けの統合アプリおよび Azure AD

統合アプリ[の管理は、統合アプリをオンまたはオフにするだけでは](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114)ありません。 Microsoft 365 REST Api の導入により、ユーザーはメール、予定表、連絡先、ユーザー、グループ、ファイル、およびフォルダーなどの Microsoft 365 データへのアクセスをアプリに許可することができます。 既定では、ユーザーは各アプリに対して個別にアクセス許可を付与する必要がありますが、アプリケーションをグローバル管理者レベルで承認し、アプリ起動ツールを使用して組織全体にロールアウトする場合は、これは適切ではありません。 これを行うには、Azure AD にアプリを登録する必要があります。 Azure AD にアプリを登録する前に、いくつかの手順を実行する必要があります。これには、Microsoft 365 組織でのアプリの管理に役立つ情報が記載されています。 この記事では、これらのリソースについて説明します。
  
## <a name="azure-ad-resources-for-microsoft-365-admins"></a>Microsoft 365 管理者向けの Azure AD リソース

Azure AD で Microsoft 365 アプリを管理する前に、これらの2つの手順を実行する必要があります。
  
|**前提条件**|**コメント**|
|:-----|:-----|
|[無料の Azure Active Directory サブスクリプションを使用する](https://docs.microsoft.com/microsoft-365/compliance/use-your-free-azure-ad-subscription-in-office-365) <br/> |Microsoft 365 へのすべての有料サブスクリプションには、Azure Active Directory (Azure AD) への無料サブスクリプションが付属しています。 Azure AD を使用して、アプリを管理したり、ユーザーアカウントおよびグループアカウントを作成および管理したりできます。 Azure AD を使用するには、Azure ポータルに移動し、Microsoft 365 アカウントを使用してサインインします。  <br/> |
|[統合アプリをオンまたはオフにする](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |サードパーティ製アプリが Microsoft 365 情報にアクセスできるようにし、Azure AD にアプリを登録するには、ユーザーに対して統合アプリを有効にする必要があります。 たとえば、ユーザーがサードパーティ製のアプリを使用している場合、そのアプリは予定表にアクセスするためのアクセス許可や、OneDrive for Business フォルダー内のファイルを編集するためのアクセス許可を要求することがあります。  <br/> |
   
Microsoft 365 アプリを管理するには、Azure AD のアプリについての知識を持っている必要があります。 これらの記事は、必要な背景を提供するのに役立ちます。
  
|**背景記事**|**コメント**|
|:-----|:-----|
|[Microsoft 365 アプリ起動ツールに会う](https://support.microsoft.com/office/meet-the-microsoft-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |アプリ起動ツールを初めて使用する場合は、その機能とその使用方法について疑問があるかもしれません。 アプリ起動ツールは、Microsoft 365 のどこからでもアプリを利用できるように設計されています。  <br/> |
|[Office 365 管理 API の概要](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview) <br/> |Microsoft 365 Api を使用すると、多くの場合、メール、予定表、連絡先、ユーザーとグループ、ファイル、およびフォルダーを含む、Microsoft 365 データへのアクセスを提供することができます。 この記事には、Microsoft 365 アプリ、Azure AD、およびアプリがアクセスするデータの関係を示す図があります。  <br/> |
|[Azure Active Directory でのアプリケーションの統合](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Azure AD と統合されたアプリケーションについて、およびアプリケーションの登録方法、登録済みアプリケーションの概念を理解する方法、マルチテナントアプリケーションのブランド化ガイドラインについて説明します。  <br/> |
|[カスタムタイルをアプリ起動ツールに追加する](https://docs.microsoft.com/office365/admin/manage/customize-the-app-launcher)  <br/> |Microsoft 365 のアプリ起動ツールを使用すると、ユーザーが自分のアプリを見つけてアクセスすることが容易になります。 この記事では、アプリを開発者がユーザーのアプリ起動ツールに表示する方法と、Microsoft 365 資格情報を使用してシングルサインオン (SSO) の機能を提供する方法について説明します。  <br/> |
|[Azure Active Directory 統合のチュートリアル](https://docs.microsoft.com/azure/active-directory/saas-apps/tutorial-list) <br/> |これらのチュートリアルの目的は、サードパーティの SaaS アプリケーション用に Azure AD SSO を構成する方法を示すことです。  <br/> |
|[Azure AD の認証シナリオ](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD では、アイデンティティをサービスとして提供することにより、OAuth 2.0 や OpenID Connect などの業界標準のプロトコルをサポートし、また、コーディングをすばやく開始できるようにさまざまなプラットフォーム用のオープンソースライブラリをサポートすることで、開発者のための認証を簡略化しています。 このドキュメントでは、Azure AD がサポートするさまざまなシナリオについて理解し、使用を開始する方法を示します。  <br/> |
|[アプリケーションアクセス](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-access-management) <br/> |Azure AD を使用すると、今日の人気のあるソフトウェアの多くがサービス (SaaS) アプリケーションとして簡単に統合されます。これにより、id とアクセス管理が提供され、ユーザーはアクセスパネルを使用して、どのアプリケーションにアクセスするか、どのアプリケーションに SSO を使用してアプリケーションにアクセスできるかを検出できます。 この記事では、Azure AD のアプリケーションアクセスの拡張機能と、それらに投稿する方法について詳しく知ることができる関連リソースへのリンクを提供します。  <br/> |
|[Office 365 の環境をカスタマイズする](https://support.office.com/article/eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |Microsoft 365 アプリ起動ツールでアプリを追加または削除することによって、毎日使用するアプリにすばやくアクセスできます。  <br/> |
   

