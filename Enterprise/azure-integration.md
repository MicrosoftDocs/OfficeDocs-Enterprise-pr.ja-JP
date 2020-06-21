---
title: Microsoft 365 との Azure の統合
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/09/2019
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Microsoft 365 サブスクリプションには、Azure AD へのサブスクリプションが含まれています。 オンプレミス環境でのパスワード同期またはシングルサインオンを行う場合は、Microsoft 365 を Azure AD と統合します。
ms.openlocfilehash: 40426c20f12cf17955457c38d809926550efa188
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774842"
---
# <a name="azure-integration-with-microsoft-365"></a>Microsoft 365 との Azure の統合

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

Microsoft 365 では、Azure Active Directory (Azure AD) を使用して、バックグラウンドでユーザー id を管理しています。 Microsoft 365 サブスクリプションには、Azure AD への無料サブスクリプションが含まれているため、Microsoft 365 を Azure ad に統合できます。これにより、パスワードを同期したり、シングルサインオンをオンプレミス環境でセットアップしたりすることができます。 また、高度な機能を購入してアカウントをより適切に管理することもできます。
  
Azure では、Microsoft 365 サブスクリプションの拡張とカスタマイズに使用できる統合アプリの管理などのその他の機能も提供しています。
  
ガイド付きのセットアップと構成の機能を実現するために、Azure AD 展開アドバイザーを使用することができます (Microsoft 365 にサインインする必要があります)。

 - [Azure AD Connect advisor](https://aka.ms/aadconnectpwsync)
 - [AD FS 展開アドバイザー](https://aka.ms/adfsguidance)
 - [Azure AD Premium セットアップガイド](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-microsoft-365-identity-management"></a>Azure AD エディションと Microsoft 365 id 管理

Microsoft 365 への有料サブスクリプションを保有している場合は、Azure AD への無料サブスクリプションも用意されています。 Azure AD を使用して、ユーザーアカウントとグループアカウントを作成および管理できます。 このサブスクリプションをアクティブ化するには、1回限りの登録を完了する必要があります。 その後、Microsoft 365 管理センターから Azure AD にアクセスできます。 

手順については、「 [Free AZURE AD サブスクリプションを使用する](https://go.microsoft.com/fwlink/p/?LinkId=617127)」を参照してください。 指示に従って、Microsoft 365 へのサブスクリプションに同梱されている無料の Azure AD サブスクリプションを登録します。 Azure.microsoft.com に直接アクセスしてサインアップしないでください。 microsoft Azure の試用版または有料版サブスクリプションを使用して、Microsoft 365 の無料のサブスクリプションとは別のものにすることができます。 
  
無料サブスクリプションを使用すると、オンプレミスのディレクトリと同期したり、シングルサインオンを設定したり、複数のソフトウェアとサービスアプリケーション (Salesforce、DropBox など) を同期したりできます。
  
拡張された Active Directory ドメインサービス (AD DS) 機能、双方向同期、およびその他の管理機能が必要な場合は、無料のサブスクリプションを有料プレミアムサブスクリプションにアップグレードできます。 詳細については、「 [Azure Active Directory のエディション](https://azure.microsoft.com/pricing/details/active-directory/)」を参照してください。
  
Microsoft 365 と Azure AD の詳細については、「 [microsoft 365 Identity と Azure Active Directory](about-office-365-identity.md)について」を参照してください。
  
## <a name="extend-the-capabilities-of-your-microsoft-365-tenant"></a>Microsoft 365 テナントの機能を拡張する

|**機能**|**説明**|
|:-----|:-----|
|統合アプリ  <br/> |メール、予定表、連絡先、ユーザー、グループ、ファイル、およびフォルダーなど、Microsoft 365 データへの個別のアプリのアクセスを許可することができます。 また、グローバル管理者レベルでこれらのアプリを承認し、Azure AD にアプリを登録することにより、会社全体でそれらを利用できるようにすることもできます。 詳細については[、「Microsoft 365 管理者向けの統合アプリと AZURE AD」を](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)参照してください。  <br/> また、「[アプリケーションへのシングルサインオン](https://go.microsoft.com/fwlink/p/?LinkId=698604)」も参照してください。  <br/> |
|PowerApps  <br/> | Power apps は、SharePoint リストなどの既存のデータソースやその他のデータアプリに接続できるモバイルデバイス用の注目アプリケーションです。 詳細については、「SharePoint Online および[PowerApps ページ](https://powerapps.microsoft.com/)[でリストの Powerapp を作成する](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)」を参照してください。  <br/> |
   
詳細については、「Microsoft 365 管理者と[azure ad アプリケーションギャラリーおよびシングルサインオン](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)[の統合アプリと azure ad](integrated-apps-and-azure-ads.md) 」を参照してください。

## <a name="see-also"></a>関連項目

[Microsoft 365 Enterprise の概要](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
