---
title: Office 365 クライアントアプリケーションのサポート-証明書ベースの認証
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
search.appverid:
- MET150
description: 証明書ベースの認証のための Office 365 クライアントアプリのサポート。
ms.openlocfilehash: 88bc59934399588f0a5c682c6b136ad0948ecd52
ms.sourcegitcommit: 9c6e31204aa326c31d60befe80e610f702e65800
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "33990925"
---
# <a name="office-365-client-app-support--certificate-based-authentication"></a>Office 365 クライアントアプリケーションのサポート-証明書ベースの認証

証明書ベースの認証を使用すると、Windows、Android、または iOS デバイス上のクライアント証明書を使用して Azure Active Directory に認証できます。 この機能を構成すると、ユーザー名とパスワードの組み合わせを、モバイルデバイス上の特定のメールおよび Microsoft Office アプリケーションに入力する必要がなくなります。

[証明書ベースの認証](https://docs.microsoft.com/azure/active-directory/authentication/active-directory-certificate-based-authentication-get-started)の詳細について説明します。

## <a name="supported-platforms"></a>サポートされるプラットフォーム

 - Windows 10 デスクトップ<sup>2</sup>
 - Windows 10 モダンアプリ
 - Web ブラウザー
 - Android
 - iOS
 - macOS<sup>1</sup> <sup>2</sup>

Office 365 のプラットフォームサポートの詳細については、「 [office 365 のシステム要件](https://products.office.com/office-system-requirements)」を参照してください。

## <a name="supported-clients"></a>サポートされるクライアント

次のクライアントの最新バージョンは、証明書ベースの認証をサポートしています。

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![アクセスアイコン](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![Azure アイコン](media/o365-azure-64x64.png) <br> [Azure AD <br>ポータル](https://azure.microsoft.com/features/azure-portal/) | ![会社のポータルのアイコン](media/o365-microsoft-64x64.png) <br> [会社<br>のポータル](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Delve アイコン](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Dynamics 365 アイコン](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) 
| ![エッジアイコン](media/o365-edge-64x64.png) <br> [エッジ](https://www.microsoft.com/windows/microsoft-edge) | ![[Excel] アイコン](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![フローアイコン](media/o365-flow-64x64.png) <br> [フロー](https://flow.microsoft.com) | ![フォームアイコン](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala アイコン](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Office 365 管理者アイコン](media/o365-o365admin-64x64.png) <br> [Office 365 <br>管理者](https://products.office.com/business/manage-office-365-admin-app) | ![レンズアイコン](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![OneDrive for Business アイコン](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>1</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![OneNote アイコン](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook アイコン](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) 
| ![Planner アイコン](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerApps アイコン](media/o365-powerapps-64x64.png) <br> [PowerApps](https://powerapps.microsoft.com) | ![PowerBI アイコン](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)| ![[PowerPoint] アイコン](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![プロジェクトアイコン](media/o365-project-64x64.png) <br> [プロジェクト](https://products.office.com/project) 
| ![Publisher のアイコン](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![SharePoint アイコン](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) | ![Skype for Business アイコン](media/o365-skypeforbusiness-64x64.png) <br> [Skype for <br> business](https://www.skype.com/business/) | ![付箋アイコン](media/o365-stickynotes-64x64.png) <br> [付箋](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![ストリームアイコン](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) 
| ![Sway アイコン](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Teams アイコン](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![To Do アイコン](media/o365-todo-64x64.png) <br> [To Do](https://todo.microsoft.com) | ![Visio アイコン](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![[Word] アイコン](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) 
| ![Yammer アイコン](media/o365-yammer-64x64.png) <br> [Yammer<sup>2</sup>](https://products.office.com/yammer/yammer-overview) |

## <a name="supported-powershell-modules"></a>サポートされている PowerShell モジュール

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure アイコン](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange アイコン](media/o365-exchange-64x64.png) <br> [Exchange Online <br>の PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint アイコン](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)

> [!NOTE]
> <sup>1</sup>近日中に入手可能な OneDrive 上の OneDrive でサポートされています。 <br>
> <sup>2</sup> Windows デスクトップと macOS でサポートされている Yammer は、まもなくサポートされます。