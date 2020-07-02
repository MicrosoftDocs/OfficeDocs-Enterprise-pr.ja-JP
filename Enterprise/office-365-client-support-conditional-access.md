---
title: Microsoft 365 クライアントアプリケーションのサポート-条件付きアクセス
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
f1.keywords:
- NOCSH
description: 条件付きアクセスに対する Microsoft 365 クライアントアプリケーションのサポートを理解する
ms.openlocfilehash: 6081af2ad3bca69978a10baabeae0a13d783f0ae
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998505"
---
# <a name="microsoft-365-client-app-support--conditional-access"></a>Microsoft 365 クライアントアプリケーションのサポート-条件付きアクセス

モダンワークプレースでは、ユーザーはさまざまなデバイスやアプリを使用してどこからでも組織のリソースにアクセスできます。 そのため、リソースにアクセスできるユーザーだけでは十分ではないことに注目してください。 組織は、アクセス制御インフラストラクチャでリソースにアクセスする方法と場所もサポートする必要があります。

Azure Active Directory (Azure AD) デバイス、場所、および多要素認証ベースの条件付きアクセスを使用すると、この新しい要件を満たすことができます。 条件付きアクセスとは、環境内のアプリへのアクセスを特定の条件に基づいて制御する、中央の場所から管理される Azure AD の機能のことです。

詳細については「[Azure AD 条件付きアクセス](https://docs.microsoft.com/azure/active-directory/conditional-access/)」を参照してください。

## <a name="supported-platforms"></a>サポートされるプラットフォーム

 - Windows 10 デスクトップ
 - Windows 10 モダンアプリ
 - Web ブラウザー
 - Android
 - iOS
 - macOS<sup>1</sup>

Microsoft 365 でのプラットフォームサポートの詳細については、「 [microsoft 365 のシステム要件](https://products.office.com/office-system-requirements)」を参照してください。

## <a name="supported-clients"></a>サポートされるクライアント

次のクライアントの最新バージョンは、条件付きアクセスをサポートしています。

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure アイコン](media/o365-azure-64x64.png) <br> [Azure AD <br> ポータル](https://azure.microsoft.com/features/azure-portal/) | ![Access アイコン](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![会社のポータルのアイコン](media/o365-microsoft-64x64.png) <br> [会社の <br> ポータル](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)  | ![Cortana アイコン](media/o365-cortana-64x64.png) <br> [Cortana](https://www.microsoft.com/cortana) | ![Delve アイコン](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) 
| ![Dynamics 365 アイコン](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![エッジアイコン](media/o365-edge-64x64.png) <br> [Edge](https://www.microsoft.com/windows/microsoft-edge) | ![Exchange アイコン](media/o365-exchange-64x64.png) <br> [Exchange](https://products.office.com/exchange/exchange-online) | ![Excel アイコン](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Forms アイコン](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) 
| ![Kaizala アイコン](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Office.com アイコン](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) | ![レンズアイコン](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Office 365 管理者アイコン](media/o365-o365admin-64x64.png) <br> [Microsoft 365 <br> 管理者](https://products.office.com/business/manage-office-365-admin-app) | ![OneDrive for Business アイコン](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>1</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) 
| ![OneNote アイコン](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook アイコン](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Planner アイコン](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerApps アイコン](media/o365-powerapps-64x64.png) <br> [PowerApps](https://powerapps.microsoft.com) | ![電源の自動化アイコン](media/o365-flow-64x64.png) <br> [電源の <br> 自動化](https://flow.microsoft.com)
| ![PowerBI アイコン](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![PowerPoint アイコン](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Project アイコン](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Publisher アイコン](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![SharePoint アイコン](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) 
| ![Skype for Business アイコン](media/o365-skypeforbusiness-64x64.png) <br> [Skype for <br> business](https://www.skype.com/business/) | ![付箋アイコン](media/o365-stickynotes-64x64.png) <br> [付箋](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Stream アイコン](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Sway アイコン](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Teams アイコン](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) 
| ![To Do アイコン](media/o365-todo-64x64.png) <br> [やるべきこと](https://todo.microsoft.com) | ![Visio アイコン](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word アイコン](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer アイコン](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

## <a name="supported-powershell-modules"></a>サポートされている PowerShell モジュール

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure アイコン](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange アイコン](media/o365-exchange-64x64.png) <br> [Exchange Online の <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint アイコン](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

> [!NOTE]
> <sup>1</sup>近日中に入手可能な OneDrive 上の OneDrive でサポートされています。

## <a name="see-also"></a>関連項目

[Microsoft 365 Enterprise の概要](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
