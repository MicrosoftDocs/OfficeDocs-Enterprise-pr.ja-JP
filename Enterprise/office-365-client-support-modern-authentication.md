---
title: Office 365 クライアントアプリのサポート-モダン認証
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
ms.collection: Strat_O365_Enterprise
search.appverid:
- MET150
description: モダン認証に対する Office 365 クライアントアプリのサポート。
ms.openlocfilehash: 8118ab6c9a7f62f01cede259b5b38c3242106102
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085356"
---
# <a name="office-365-client-app-support---modern-authentication"></a>Office 365 クライアントアプリのサポート-モダン認証

Microsoft の先進認証機能を使用すると、さまざまなプラットフォーム間で Office クライアントアプリの Active Directory 認証ライブラリ (ADAL) ベースのサインインが有効になります。これにより、多要素認証 (MFA)、スマートカード、証明書ベースの認証などのサインイン機能が有効になります。

[多要素認証](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication)と[証明書ベース認証](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started)の詳細について説明します。

## <a name="supported-platforms"></a>サポートされるプラットフォーム

 - Windows 10 デスクトップ
 - Windows 10 モダンアプリ
 - Web ブラウザー
 - Android
 - iOS
 - macOS

office 365 のプラットフォームサポートの詳細については、「 [office 365 のシステム要件](https://products.office.com/office-system-requirements)」を参照してください。

## <a name="supported-clients"></a>サポートされるクライアント

最新のバージョンの次のクライアントは、先進認証をサポートしています。

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure アイコン](media/o365-azure-64x64.png) <br> [Azure AD <br>ポータル](https://azure.microsoft.com/features/azure-portal/) | ![会社のポータルのアイコン](media/o365-microsoft-64x64.png) <br> [会社<br>のポータル](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Delve アイコン](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Dynamics 365 アイコン](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![[Excel] アイコン](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) |
| ![フローアイコン](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![フォームアイコン](media/o365-forms-64x64.png) <br> [フォーム](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala アイコン](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Office 365 管理者アイコン](media/o365-o365admin-64x64.png) <br> [Office 365 <br>管理者](https://products.office.com/business/manage-office-365-admin-app) | ![レンズアイコン](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | 
| ![OneDrive for business アイコン](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![OneNote アイコン](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook アイコン](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Planner アイコン](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerBI アイコン](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)
| ![[PowerPoint] アイコン](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![プロジェクトアイコン](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![SharePoint アイコン](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) | ![Skype for business アイコン](media/o365-skypeforbusiness-64x64.png) <br> [Skype for <br> business](https://www.skype.com/business/) | ![StaffHub アイコン](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software)
| ![付箋アイコン](media/o365-stickynotes-64x64.png) <br> [付箋](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![ストリームアイコン](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Sway アイコン](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Teams アイコン](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![To do アイコン](media/o365-todo-64x64.png) <br> [To Do](https://todo.microsoft.com)
| ![Visio アイコン](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![[Word] アイコン](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) |![Yammer アイコン](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview) | ![Yammer アイコン](media/o365-yammer-64x64.png) <br> [Yammer <br>の Notifier](https://products.office.com/yammer/yammer-overview) |  |

## <a name="supported-powershell-modules"></a>サポートされている PowerShell モジュール

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure アイコン](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange アイコン](media/o365-exchange-64x64.png) <br> [Exchange Online <br>の PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint アイコン](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)