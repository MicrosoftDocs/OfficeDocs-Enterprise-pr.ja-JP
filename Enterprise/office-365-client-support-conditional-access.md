---
title: Office 365 クライアントアプリケーションのサポート-条件付きアクセス
ms.author: robmazz
author: robmazz
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
description: 条件付きアクセスに対する Office 365 クライアントアプリのサポートを理解する
ms.openlocfilehash: 86730760f566ec46ad03b78bc0485d067894e371
ms.sourcegitcommit: 9c6e31204aa326c31d60befe80e610f702e65800
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "33976873"
---
# <a name="office-365-client-app-support--conditional-access"></a>Office 365 クライアントアプリケーションのサポート-条件付きアクセス

モダンワークプレースでは、ユーザーはさまざまなデバイスやアプリを使用してどこからでも組織のリソースにアクセスできます。 そのため、リソースにアクセスできるユーザーだけでは十分ではないことに注目してください。 組織は、アクセス制御インフラストラクチャでリソースにアクセスする方法と場所もサポートする必要があります。

Azure AD デバイス、場所、および多要素認証ベースの条件付きアクセスを使用すると、この新しい要件を満たすことができます。 条件付きアクセスとは、環境内のアプリへのアクセスに対して、特定の条件に基づいて管理されたアプリケーションへのアクセスの制御を可能にする Azure Active Directory の機能です。

[条件付きアクセス](https://docs.microsoft.com/azure/active-directory/conditional-access/)について説明します。

## <a name="supported-platforms"></a>サポートされるプラットフォーム

 - Windows 10 デスクトップ
 - Windows 10 モダンアプリ
 - Web ブラウザー
 - Android<sup>1</sup>
 - iOS
 - macOS<sup>2</sup>

Office 365 のプラットフォームサポートの詳細については、「 [office 365 のシステム要件](https://products.office.com/office-system-requirements)」を参照してください。

## <a name="supported-clients"></a>サポートされるクライアント

次のクライアントの最新バージョンは、条件付きアクセスをサポートしています。

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure アイコン](media/o365-azure-64x64.png) <br> [Azure AD <br>ポータル](https://azure.microsoft.com/features/azure-portal/) | ![アクセスアイコン](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![Delve アイコン](media/o365-delve-64x64.png) <br> [Delve<sup>1</sup>](https://products.office.com/business/intelligent-search) | ![Dynamics 365 アイコン](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![エッジアイコン](media/o365-edge-64x64.png) <br> [下辺](https://www.microsoft.com/windows/microsoft-edge) 
| ![Exchange アイコン](media/o365-exchange-64x64.png) <br> [Exchange](https://products.office.com/exchange/exchange-online) | ![[Excel] アイコン](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![フローアイコン](media/o365-flow-64x64.png) <br> [フロー](https://flow.microsoft.com) | ![フォームアイコン](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala アイコン](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![レンズアイコン](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Office 365 管理者アイコン](media/o365-o365admin-64x64.png) <br> [Office 365 <br>管理者](https://products.office.com/business/manage-office-365-admin-app) | ![OneDrive for Business アイコン](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>2</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote アイコン](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook アイコン](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) |
| ![Planner アイコン](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerBI アイコン](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![[PowerPoint] アイコン](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![プロジェクトアイコン](media/o365-project-64x64.png) <br> [プロジェクト](https://products.office.com/project) | ![Publisher のアイコン](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher)
| ![SharePoint アイコン](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) | ![Skype for Business アイコン](media/o365-skypeforbusiness-64x64.png) <br> [Skype for <br> business](https://www.skype.com/business/) | ![付箋アイコン](media/o365-stickynotes-64x64.png) <br> [付箋](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![ストリームアイコン](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Sway アイコン](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) 
| ![Teams アイコン](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![To Do アイコン](media/o365-todo-64x64.png) <br> [To Do](https://todo.microsoft.com) | ![Visio アイコン](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![[Word] アイコン](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer アイコン](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <sup>1</sup>近日中に利用できる、Android での Delve のサポート。 <br>
> <sup>2</sup>近日中に入手可能な OneDrive 上の OneDrive でサポートされています。