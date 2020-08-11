---
title: Microsoft 365 クライアントアプリケーションのサポート-モダン認証
ms.author: josephd
author: JoeDavies-MSFT
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
f1.keywords:
- NOCSH
description: この記事では、Microsoft 365 の先進認証をサポートするプラットフォーム、クライアント、および Powershell モジュールについて説明します。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 29a579111d04cef444d1f8ad306b940a93517fe6
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606663"
---
# <a name="microsoft-365-client-app-support---modern-authentication"></a>Microsoft 365 クライアントアプリのサポート-モダン認証

*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*

モダン認証を使用すると、さまざまなプラットフォーム間で Office クライアントアプリの Active Directory 認証ライブラリ (ADAL) ベースのサインインが有効になります。 これにより、多要素認証 (MFA)、スマートカード、証明書ベースの認証などのサインイン機能が有効になります。

[多要素認証](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication)と[証明書ベース認証](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started)の詳細について説明します。

## <a name="supported-platforms"></a>サポートされるプラットフォーム

 - Windows 10 デスクトップ
 - Windows 10 モダンアプリ
 - Web ブラウザー<sup>1</sup>
 - Android<sup>2</sup>
 - iOS
 - macOS

Microsoft 365 でのプラットフォームサポートの詳細については、「 [microsoft 365 のシステム要件](https://products.office.com/office-system-requirements)」を参照してください。

## <a name="supported-clients"></a>サポートされるクライアント

最新のバージョンの次のクライアントは、先進認証をサポートしています。

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Access アイコン](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![Azure アイコン](media/o365-azure-64x64.png) <br> [Azure <br> Portal](https://azure.microsoft.com/features/azure-portal/) | ![会社のポータルのアイコン](media/o365-microsoft-64x64.png) <br> [会社の <br> ポータル](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Delve アイコン](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Dynamics 365 アイコン](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) 
| ![エッジアイコン](media/o365-edge-64x64.png) <br> [Edge](https://www.microsoft.com/windows/microsoft-edge) | ![Excel アイコン](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Forms アイコン](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala アイコン](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Office.com アイコン](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) 
| ![Office 365 管理者アイコン](media/o365-o365admin-64x64.png) <br> [Microsoft 365 <br> 管理者](https://products.office.com/business/manage-office-365-admin-app) | ![レンズアイコン](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![OneDrive for Business アイコン](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![OneNote アイコン](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook アイコン](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) 
| ![Planner アイコン](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerApps アイコン](media/o365-powerapps-64x64.png) <br> [PowerApps](https://powerapps.microsoft.com) | ![電源の自動化アイコン](media/o365-flow-64x64.png) <br> [電源の <br> 自動化](https://flow.microsoft.com) | ![PowerBI アイコン](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)| ![PowerPoint アイコン](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) 
| ![Project アイコン](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Publisher アイコン](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![SharePoint アイコン](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) | ![Skype for Business アイコン](media/o365-skypeforbusiness-64x64.png) <br> [Skype for <br> business<sup>1</sup>](https://www.skype.com/business/) | ![StaffHub アイコン](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software)
| ![付箋アイコン](media/o365-stickynotes-64x64.png) <br> [付箋](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Stream アイコン](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Sway アイコン](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Teams アイコン](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![To Do アイコン](media/o365-todo-64x64.png) <br> [やるべきこと](https://todo.microsoft.com) 
| ![Visio アイコン](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Whiteboard アイコン](media/o365-whiteboard-64x64.png) <br> [ホワイトボード<sup>1</sup>、<sup>2</sup>](https://whiteboard.microsoft.com/) | ![Word アイコン](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer アイコン](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview) | ![Yammer アイコン](media/o365-yammer-64x64.png) <br> [Yammer の <br> Notifier](https://products.office.com/yammer/yammer-overview) |  |

## <a name="supported-powershell-modules"></a>サポートされている PowerShell モジュール

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure アイコン](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange アイコン](media/o365-exchange-64x64.png) <br> [Exchange Online の <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint アイコン](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

> [!NOTE]
> <sup>1</sup>すぐに利用可能なホワイトボードと Skype for business のサポートが用意されています。 <br>
> <sup>2</sup>すぐに利用できる、Android 上のホワイトボードのサポート。

## <a name="see-also"></a>関連項目

[Microsoft 365 Enterprise の概要](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
