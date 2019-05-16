---
title: Azure と Office 365 との統合
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Office 365 サブスクリプションには、Azure AD へのサブスクリプションが含まれています。 オンプレミス環境でパスワード同期またはシングルサインオンを行う場合は、Office 365 を Azure AD と統合します。
ms.openlocfilehash: 51ed71aa94bc5317d9b5ff76d0aa6af2762c429e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068223"
---
# <a name="azure-integration-with-office-365"></a>Azure と Office 365 との統合

Office 365 では、Azure Active Directory (Azure AD) を使用して、バックグラウンドでユーザー id を管理しています。 Office 365 サブスクリプションには Azure AD への無料サブスクリプションが含まれているため、Office 365 を Azure ad に統合できます。これにより、パスワードを同期したり、シングルサインオンをオンプレミスの環境でセットアップしたりすることができます。 また、高度な機能を購入してアカウントをより適切に管理することもできます。
  
Azure では、Office 365 のサブスクリプションを拡張およびカスタマイズするために使用できる、統合アプリの管理などのその他の機能も提供されています。
  
ガイド付きセットアップおよび構成の手順には、Azure AD 展開アドバイザーを使用できます。
 - [Azure AD Connect advisor](https://aka.ms/aadconnectpwsync)
 - [AD FS 展開アドバイザー](https://aka.ms/adfsguidance)
 - [Azure RMS 展開ウィザード](https://aka.ms/azuremsguidance)
 - [Azure AD Premium セットアップガイド](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a>Azure AD エディションおよび Office 365 id 管理

Office 365 への有料サブスクリプションを所有している場合は、Azure AD への無料サブスクリプションも用意されています。 Azure AD を使用して、ユーザーアカウントとグループアカウントを作成および管理できます。 このサブスクリプションをアクティブ化するには、1回限りの登録を完了する必要があります。 その後、Office 365 管理ポータルから Azure AD にアクセスできます。 手順については、「 [AZURE AD サブスクリプションを登録する](https://go.microsoft.com/fwlink/p/?LinkId=617127)」を参照してください。 
  
> [!TIP]
> 上記の手順に従って、Office 365 のサブスクリプションに同梱されている無料の Azure AD サブスクリプションを登録します。 Azure.microsoft.com に直接アクセスしないと、Office 365 の無料のサブスクリプションとは別の、Microsoft Azure の試用版または有料版サブスクリプションが作成されることになります。 
  
無料サブスクリプションを使用すると、オンプレミスのディレクトリと同期したり、シングルサインオンを設定したり、複数のソフトウェアとサービスアプリケーション (Salesforce、DropBox など) を同期したりできます。
  
拡張された AD DS 機能、双方向同期、およびその他の管理機能が必要な場合は、無料のサブスクリプションを有料プレミアムサブスクリプションにアップグレードできます。 詳細については、「 [Azure Active Directory のエディション](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis)」を参照してください。
  
Office 365 と Azure AD の詳細については、「 [office 365 id と Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9)について」を参照してください。
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a>Office 365 テナントの機能を拡張する

|**機能**|**説明**|
|:-----|:-----|
|統合アプリ  <br/> |Office 365 データ (メール、予定表、連絡先、ユーザー、グループ、ファイル、フォルダーなど) へのアクセスを個別のアプリに許可できます。 また、グローバル管理者レベルでこれらのアプリを承認し、Azure AD にアプリを登録することにより、会社全体でそれらを利用できるようにすることもできます。 詳細については[、「Office 365 管理者向けの統合アプリと AZURE AD」を](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)参照してください。  <br/> [AZURE AD アプリケーションギャラリーおよびシングルサインオン](https://go.microsoft.com/fwlink/p/?LinkId=698604)も参照してください。  <br/> |
|PowerApps  <br/> | Power apps は、SharePoint リストなどの既存のデータソースやその他のデータアプリに接続できるモバイルデバイス用の注目アプリケーションです。 詳細については、「SharePoint Online および[PowerApps ページ](https://powerapps.microsoft.com/)[でリストの Powerapp を作成する](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)」を参照してください。  <br/> |
   
Microsoft Cloud および Office 365 に関するその他のリソースについては、次のリソースを参照してください。
  
- [エンタープライズ アーキテクトのための Microsoft クラウド ID](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [Microsoft Azure での Office 365 ディレクトリ同期 (DirSync) の展開](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

詳細については、「Office 365 管理者および[azure ad アプリケーションギャラリーとシングルサインオン](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)[の統合アプリおよび azure Ad](integrated-apps-and-azure-ads.md) 」を参照してください。

### <a name="power-apps"></a>パワーアプリ
Power apps は、SharePoint リストなどの既存のデータソースやその他のデータアプリに接続できるモバイルデバイス用の注目アプリケーションです。 詳細については、「SharePoint Online および[PowerApps ページ](https://powerapps.microsoft.com/)[でリストの Powerapp を作成する](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)」を参照してください。