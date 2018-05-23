---
title: Project Server の GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: オンプレミスの Project Server で GDPR の要件に対応する方法について説明します。
ms.openlocfilehash: 6a630dc4cef2c4117e0ba25497f898d0b8da221b
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-project-server"></a>Project Server の GDPR

Project Server では、Project Web App でユーザー データをエクスポートしたり編集したりするために、カスタム スクリプトが使用されます。基本的な処理は、次のとおりです。

1.  ファーム内で Project Web App のサイトを検索します。

2.  各サイトの中で、ユーザーが含まれているプロジェクトを検索します。

3.  確認対象となるタイプのデータをエクスポートし、確認します。

4.  必要に応じてデータを編集します。

これらの手順について、以下の記事で詳細に説明します。

- [Project Server からユーザー データをエクスポートする](/Project/export-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)

- [Project Server からユーザー データを削除する](/Project/delete-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)


Project Server は SharePoint Server 上に構築されており、SharePoint ULS のログおよび利用状況データベースにイベントのログが出力されることに注意してください。
