---
title: Office 365 クライアント アプリケーションのサポート - 最新の認証
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/17/2018
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: None
ms.collection: Strat_O365_Enterprise
description: Office 365 クライアント アプリケーションは、最新の認証をサポートします。
ms.openlocfilehash: 73827d1e19556a31c9eb3a11c9fa6617bee3f566
ms.sourcegitcommit: 4e654517825b74a3bbe171b915b134ba49231e2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2018
ms.locfileid: "21541957"
---
# <a name="office-365-client-app-support---modern-authentication"></a>Office 365 クライアント アプリケーションのサポート - 最新の認証

異なるプラットフォーム間で Active Directory 認証ライブラリの ADAL ベース記号で Office クライアント アプリケーションのマイクロソフトの最新の認証機能を有効にします。これにより、多要素認証 (MFA)、スマート カード証明書ベースの認証などの機能にサインインできます。

[多要素認証](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication)と[証明書ベースの認証](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started)の詳細について説明します。

## <a name="supported-platforms"></a>サポートされるプラットフォーム

 - 10 の Windows デスクトップ
 - 新しいアプリが Windows 10
 - Web ブラウザー
 - Android
 - iOS
 - macOS

## <a name="supported-clients"></a>サポートされるクライアント

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![アイコンを説明します。](images/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Dynamics 365 アイコン](images/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![[Excel] アイコン](images/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![フロー アイコン](images/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![フォーム アイコン](images/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | 
| ![Kaizala アイコン](images/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Office 365 管理者アイコン](images/o365-o365admin-64x64.png) <br> [Office 365<br>管理](https://products.office.com/business/manage-office-365-admin-app) | ![レンズ アイコン](images/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![ビジネスのアイコンを OneDrive](images/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote アイコン](images/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote)
| ![Outlook のアイコン](images/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![プランナーのアイコン](images/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerBI アイコン](images/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![[PowerPoint] アイコン](images/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![プロジェクト アイコン](images/o365-project-64x64.png) <br> [Project](https://products.office.com/project) 
| ![SharePoint のアイコン](images/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) | ![Skype ビジネスのアイコン](images/o365-skypeforbusiness-64x64.png) <br> [Skype<br>ビジネス](https://www.skype.com/business/) | ![StaffHub アイコン](images/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software) | ![ストリーム アイコン](images/o365-stream-64x64.png) <br> [ストリーム](https://stream.microsoft.com) | ![アイコンをかきたてる](images/o365-sway-64x64.png) <br> [Sway](https://sway.com)
| ![チーム アイコン](images/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![タスク アイコン](images/o365-todo-64x64.png) <br> [To Do](https://todo.microsoft.com) | ![Visio アイコン](images/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![[Word] アイコン](images/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer のアイコン](images/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)