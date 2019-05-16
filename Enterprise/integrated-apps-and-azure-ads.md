---
title: Office 365 管理者の統合アプリおよび Azure AD
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection: M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: Azure AD で O365 統合アプリを登録および管理する方法について説明します。
ms.openlocfilehash: 01bd932ed12e040a0e6dae517d7b4fd360b5da80
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067253"
---
# <a name="integrated-apps-and-azure-ad-for-office-365-administrators"></a>Office 365 管理者の統合アプリおよび Azure AD

統合アプリ[の管理は、統合アプリをオンまたはオフにするだけでは](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114)ありません。 Office 365 REST Api の出現により、ユーザーは、メール、予定表、連絡先、ユーザー、グループ、ファイル、およびフォルダーなどの Office 365 データへのアクセスをアプリに許可できます。 既定では、ユーザーは各アプリに対して個別にアクセス許可を付与する必要がありますが、アプリケーションをグローバル管理者レベルで承認し、アプリ起動ツールを使用して組織全体にロールアウトする場合は、これは適切ではありません。 これを行うには、Azure AD にアプリを登録する必要があります。 Azure AD にアプリを登録するために必要ないくつかの手順があります。また、Office 365 組織のアプリの管理に役立つ可能性があるいくつかのバックグラウンド情報を知る必要があります。 この記事では、これらのリソースについて説明します。
  
## <a name="azure-ad-resources-for-office-365-admins"></a>Office 365 管理者向けの Azure AD リソース

Azure AD で Office 365 アプリを管理する前に、これらの2つの手順を実行する必要があります。
  
|**前提条件**|**コメント**|
|:-----|:-----|
|[無料の Azure Active Directory サブスクリプションの登録](https://go.microsoft.com/fwlink/?LinkId=617127) <br/> |Office 365 へのすべての有料サブスクリプションには、Azure Active Directory への無料サブスクリプションが付属しています。 Azure AD を使用して、アプリを管理したり、ユーザーアカウントおよびグループアカウントを作成および管理したりできます。 このサブスクリプションをアクティブ化して Azure 管理ポータルにアクセスするには、1 度限りの登録プロセスを完了する必要があります。 その後、Office 365 管理センターから Azure AD に移動できます。  <br/> |
|[統合アプリをオンまたはオフにする](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |サードパーティ製アプリが Office 365 情報にアクセスできるようにし、Azure AD でアプリを登録するには、ユーザーに対して統合アプリを有効にする必要があります。 たとえば、ユーザーがサードパーティ製のアプリを使用している場合、そのアプリは予定表にアクセスするためのアクセス許可や、OneDrive for Business フォルダー内のファイルを編集するためのアクセス許可を要求することがあります。  <br/> |
   
Office 365 アプリを管理するには、Azure AD のアプリに関する知識を持っている必要があります。 これらの記事は、必要な背景を提供するのに役立ちます。
  
|**背景記事**|**コメント**|
|:-----|:-----|
|[Office 365 アプリ起動ツールに会う](https://support.office.com/article/79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |アプリ起動ツールを初めて使用する場合は、その機能とその使用方法について疑問があるかもしれません。 アプリ起動ツールは、Office 365 のどこからでもアプリを利用できるように設計されています。  <br/> |
|[アプリケーションの追加、更新、および削除](https://go.microsoft.com/fwlink/?LinkId=617137) <br/> |このトピックでは、Azure Active Directory でアプリケーションを追加、更新、または削除する方法について説明します。 Azure AD と統合できるさまざまな種類のアプリケーションと、web Api などの他のリソースにアクセスするようにアプリケーションを構成する方法について説明します。  <br/> |
|[アプリが Office 365 アプリ起動ツールに表示されるように](https://go.microsoft.com/fwlink/?LinkId=617138)します。  <br/> |Office 365 のアプリ起動ツールを使用すると、ユーザーが自分のアプリを簡単に検索してアクセスできるようになります。 この記事では、アプリを開発者がユーザーのアプリ起動ツールに表示する方法と、Office 365 資格情報を使用してシングルサインオン (SSO) の機能を提供する方法について説明します。  <br/> |
|[Office 365 API プラットフォームの概要](https://go.microsoft.com/fwlink/?LinkId=617140) <br/> |Office 365 Api を使用すると、多くのお客様の Office 365 データに、メール、予定表、連絡先、ユーザーとグループ、ファイル、およびフォルダーなどの情報を提供できます。 この記事では、Office 365 アプリ、Azure AD、およびアプリがアクセスするデータ間の関係を示す図があります。  <br/> |
|[Azure Active Directory でのアプリケーションの統合](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Azure Active Directory と統合されているアプリケーションについて、およびアプリケーションの登録方法、登録済みアプリケーションの概念を理解する方法、マルチテナントアプリケーションのブランド化ガイドラインについて説明します。  <br/> |
|[Azure Active Directory 統合のチュートリアル](https://docs.microsoft.com/azure/active-directory/saas-apps/tutorial-list) <br/> |これらのチュートリアルの目的は、サードパーティの SaaS アプリケーション用に Azure AD SSO を構成する方法を示すことです。  <br/> |
|[Azure AD の認証シナリオ](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD では、アイデンティティをサービスとして提供することにより、OAuth 2.0 や OpenID Connect などの業界標準のプロトコルをサポートし、また、コーディングをすばやく開始できるようにさまざまなプラットフォーム用のオープンソースライブラリをサポートすることで、開発者のための認証を簡略化しています。 このドキュメントでは、Azure AD がサポートするさまざまなシナリオについて理解し、使用を開始する方法を示します。  <br/> |
|[アプリケーションアクセス](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-access-management) <br/> |Azure AD を使用すると、今日の人気のあるソフトウェアの多くがサービス (SaaS) アプリケーションとして簡単に統合されます。これにより、id とアクセス管理が提供され、ユーザーはアクセスパネルを使用して、どのアプリケーションにアクセスするか、どのアプリケーションに SSO を使用してアプリケーションにアクセスできるかを検出できます。 この記事では、Azure AD のアプリケーションアクセスの拡張機能と、それらに投稿する方法について詳しく知ることができる関連リソースへのリンクを提供します。  <br/> |
|[Office 365 の環境をカスタマイズする](https://support.office.com/article/eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |Office 365 アプリ起動ツールでアプリを追加または削除することによって、毎日使用するアプリにすばやくアクセスできます。  <br/> |
   

