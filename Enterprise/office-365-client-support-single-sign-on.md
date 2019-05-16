---
title: Office 365 クライアントアプリケーションのサポート-シングルサインオン
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
description: シングルサインオンの Office 365 クライアントアプリサポート。
ms.openlocfilehash: 1ab1a2d7c461c1ae44f0fefba4b9a3663753fb97
ms.sourcegitcommit: 9c6e31204aa326c31d60befe80e610f702e65800
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "33990923"
---
# <a name="office-365-client-app-support--single-sign-on"></a>Office 365 クライアントアプリケーションのサポート-シングルサインオン

シングルサインオン (SSO) を使用すると、ユーザーが Azure Active Directory (Azure AD) のアプリケーションにサインオンするときに、セキュリティと利便性が向上します。 シングルサインオンを使用すると、ユーザーは1つのアカウントでサインインし、ドメインに参加しているデバイス、会社のリソース、サービス (SaaS) アプリケーション、および web アプリケーションにアクセスできます。

[シングルサインオン](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)の詳細については、こちらを参照してください。

## <a name="supported-platforms"></a>サポートされるプラットフォーム

 - Windows 10 デスクトップ
 - Windows 10 モダンアプリ
 - Web ブラウザー
 - Android
 - iOS<sup>1</sup>
 - macOS

Office 365 のプラットフォームサポートの詳細については、「 [office 365 のシステム要件](https://products.office.com/office-system-requirements)」を参照してください。

## <a name="supported-clients"></a>サポートされるクライアント

次のクライアントの最新バージョンは、シングルサインオンをサポートしています。

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![アクセスアイコン](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![会社のポータルのアイコン](media/o365-microsoft-64x64.png) <br> [会社<br>のポータル](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![エッジアイコン](media/o365-edge-64x64.png) <br> [エッジ](https://www.microsoft.com/windows/microsoft-edge) | ![[Excel] アイコン](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![フローアイコン](media/o365-flow-64x64.png) <br> [フロー](https://flow.microsoft.com) 
| ![レンズアイコン](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![OneDrive for Business アイコン](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![OneNote アイコン](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook アイコン](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Planner アイコン](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) 
| ![PowerBI アイコン](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)| ![[PowerPoint] アイコン](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![プロジェクトアイコン](media/o365-project-64x64.png) <br> [プロジェクト](https://products.office.com/project) | ![Publisher のアイコン](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![SharePoint アイコン](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) 
| ![Skype for Business アイコン](media/o365-skypeforbusiness-64x64.png) <br> [Skype for <br> business](https://www.skype.com/business/) | ![付箋アイコン](media/o365-stickynotes-64x64.png) <br> [付箋](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Sway アイコン](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Teams アイコン](media/o365-teams-64x64.png) <br> [Teams<sup>1</sup>](https://products.office.com/microsoft-teams/group-chat-software) | ![To Do アイコン](media/o365-todo-64x64.png) <br> [To Do](https://todo.microsoft.com) 
| ![Visio アイコン](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![[Word] アイコン](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer アイコン](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview) |

## <a name="supported-powershell-modules"></a>サポートされている PowerShell モジュール

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure アイコン](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange アイコン](media/o365-exchange-64x64.png) <br> [Exchange Online <br>の PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint アイコン](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)

> [!NOTE]
> <sup>1</sup> iOS のみの Teams でサポートされています。 <br>