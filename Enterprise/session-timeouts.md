---
title: Office 365 のセッションのタイムアウト
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
description: Securtiy と Office 365 クライアント アプリケーションでのアクセスの容易さのバランスをとるには、セッションのタイムアウトが使用されます。
ms.openlocfilehash: dda13f280149c969354ae1f0eac336f1d8ed23e7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541637"
---
# <a name="session-timeouts-for-office-365"></a>Office 365 のセッションのタイムアウト

セッションの有効期間は、Office 365 の認証の重要な部分であり、セキュリティと資格情報のユーザーが表示されたら回数のバランスの重要なコンポーネントです。
  
## <a name="session-times-for-office-365-services"></a>Office 365 サービスのセッション時間

ユーザーは、Office 365 の web アプリケーションやモバイル アプリケーションのいずれかで認証、セッションが確立されます。セッションが終了するまで、ユーザーは再認証する必要はありません。セッションは、ブラウザーやタブを閉じるとき、またはなど、パスワードをリセットすると、他の理由により、認証トークンの有効期限が切れると、ユーザーがアクティブになっている場合に期限が切れることができます。Office 365 サービスでは、各サービスの一般的な使用に対応する別のセッションのタイムアウトがあります。
  
次の表に、Office 365 サービスのセッションの有効期間を示します。
  
|**Office 365 サービス**|**セッションのタイムアウト**|
|:-----|:-----|
|Office 365 管理者センター  <br/> |8 時間ごとに管理センターの資格情報を提供するように求められます。  <br/> |
|SharePoint Online  <br/> |5 日間のアクティブでない限り、ユーザーは、**サインインを維持**するかを選択します。ユーザーがアクセスする SharePoint Online 再度前のサインインから 24 以上の時間が経過した後、タイムアウト値は 5 日にリセットされます。<br/> |
|Outlook Web App  <br/> |6 時間です。  <br/> [セット OrganizationConfig](https://go.microsoft.com/fwlink/p/?LinkId=615378)コマンドレットの_ActivityBasedAuthenticationTimeoutInterval_パラメーターを使用して、この値を変更できます。  <br/> |
|Azure Active Directory  <br/> (現代の認証が有効になっているとは、Office 2013 の Windows クライアントで使用)  <br/> | 現代の認証では、アクセス ・ トークンとトークンの更新を使用して、Azure Active Directory を使用して Office 365 リソースへのユーザー アクセスを許可します。アクセス トークンは JSON Web トークン認証に成功した後、有効な 1 時間です。更新トークンの有効期間が長くなりますがも用意されています。アクセス トークンが期限切れに、Office クライアントは新しいアクセス トークンを取得するのには有効な更新トークンを使用します。ユーザーの最初の認証が有効の場合、この交換が成功します。  <br/>  リフレッシュ トークンは 90 日間、有効期間は、継続的な使用は、失効するまで有効なことができます。  <br/>  更新トークンは、次のようにいくつかのイベントによって無効にすることができます。  <br/>  リフレッシュ トークンが発行されてから、ユーザーのパスワードが変更されました。  <br/>  管理者は、ユーザーがアクセスしようとしてリソースへのアクセスを制限する条件付きのアクセス ポリシーを適用できます。  <br/> |
|Android、iOS、および Windows の 10 のモバイル アプリケーションを SharePoint と OneDrive  <br/> |アクセス トークンの既定の有効期間は、1 時間です。更新トークンの既定の最大使用頻度の低い時間は、90 日間です。<br/> [トークンおよびトークンの有効期間を構成する方法の詳細についてください。](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> 更新を取り消すにはトークンがパスワードをリセットするユーザーの Office 365  <br/> |
|Yammer を Office 365 にサインイン  <br/> |ブラウザーの有効期間。ユーザーがブラウザーを閉じるし、Yammer に新しいブラウザーでアクセス、Yammer を再認証に Office 365 にします。ユーザーは、サード ・ パーティ製のブラウザーをキャッシュ cookie を使用している場合、ブラウザーを再度開き、ときに再認証する必要はありません。<br/> > [!NOTE]> これは、Yammer の Office 365 にサインインを使用してネットワークでのみ有効です。           |
   

