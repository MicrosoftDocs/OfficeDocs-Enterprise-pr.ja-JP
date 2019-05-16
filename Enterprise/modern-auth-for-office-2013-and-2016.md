---
title: Office 2013 クライアント アプリと Office 2016 クライアント アプリでの先進認証のしくみ
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/1/2017
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- GMA150
- GPA150
- GEA150
- BCS160
ms.assetid: e4c45989-4b1a-462e-a81b-2a13191cf517
ms.collection:
- M365-security-compliance
description: Office 365 モダン認証の動作が Office 2013 および2016クライアントアプリによって異なる方法について説明します。
ms.openlocfilehash: 80a5f557fc1f3d189e8852ac3039521cfc31fb2c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070063"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>Office 2013 クライアント アプリと Office 2016 クライアント アプリでの先進認証のしくみ

この記事では、office 2013 および Office 2016 クライアントアプリが、Exchange Online、SharePoint Online、Skype for Business Online の Office 365 テナントの認証構成に基づいて先進認証機能を使用する方法について説明します。

> [!NOTE]
> Office 2010 や Office for Mac 2011 などのレガシクライアントアプリは先進認証をサポートしておらず、基本認証でのみ使用できます。

## <a name="availability-of-modern-authentication-for-office-365-services"></a>Office 365 サービスの先進認証の利用可能性

Office 365 サービスの場合、モダン認証の既定の状態は次のとおりです。
  
- 既定では、Exchange Online に対してオン**に**なっています。 オフまたはオンにするには、「 [Exchange Online で先進認証を有効または無効](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662)にする」を参照してください。 
    
- 既定では、SharePoint Online に対してオン**に**なっています。 
    
- 既定では、Skype for Business Online に対してオン**に**なっています。 この機能をオフまたはオンにするには、「[モダン認証のために Skype For Business Online を有効](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)にする」を参照してください。
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Office クライアントアプリのサインイン動作

Office 2013 クライアントアプリは、既定で従来の認証をサポートしています。 従来の場合は、Microsoft Online サインインアシスタントまたは基本認証のいずれかをサポートしています。 これらのクライアントが先進認証機能を使用するためには、Windows クライアントにレジストリキーが設定されています。 手順については、「 [Windows デバイスで Office 2013 の先進認証を有効にする](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910)」を参照してください。
  
Skype for business での[先進認証 (ADAL) の使用](https://go.microsoft.com/fwlink/p/?LinkId=785431)方法については、「方法」を参照してください。 
  
Office 2016 クライアントは既定で先進認証をサポートしており、クライアントがこれらの新しいフローを使用するために必要な操作はありません。 ただし、従来の認証を使用するには、明示的なアクションが必要です。
  
次のリンクをクリックすると、モダン認証が有効になっているかどうかに応じて、office 2013 と office 2016 クライアント認証が Office 365 サービスでどのように動作するかを確認できます。
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [Skype for Business Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
### <a name="exchange-online"></a>Exchange Online

次の表は、モダン認証を使用して、または使用しない状態で Exchange Online に接続した場合の Office 2013 または Office 2016 クライアントアプリの認証動作を示しています。
  
|Office クライアントアプリのバージョン * * * *|レジストリキーが存在するかどうか * * * *|モダン認証は? * * * *|テナントで先進認証がオンになっている認証動作 (既定) * * * *|テナントの先進認証がオフになっている認証動作 * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |No、または EnableADAL = 1  <br/> |はい  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、基本認証が使用されます。 テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、基本認証が使用されます。 テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |
|Office 2016  <br/> |はい、EnableADAL = 1  <br/> |はい  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、基本認証が使用されます。 テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、基本認証が使用されます。 テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |
|Office 2016  <br/> |はい、EnableADAL = 0  <br/> |いいえ  <br/> |基本認証  <br/> |基本認証  <br/> |
|Office 2013  <br/> |いいえ  <br/> |いいえ  <br/> |基本認証  <br/> |基本認証  <br/> |
|Office 2013  <br/> |はい、EnableADAL = 1  <br/> |はい  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、基本認証が使用されます。 テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、基本認証が使用されます。 テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |
   
### <a name="sharepoint-online"></a>SharePoint Online
<a name="BK_SharePointOnline"> </a>

次の表に、モダン認証を使用して、または使用しない状態で SharePoint Online に接続した場合の Office 2013 または Office 2016 クライアントアプリの認証動作を示します。
  
|Office クライアントアプリのバージョン * * * *|レジストリキーが存在するかどうか * * * *|モダン認証は? * * * *|テナントで先進認証がオンになっている認証動作 (既定) * * * *|テナントの先進認証がオフになっている認証動作 * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |No、または EnableADAL = 1  <br/> |はい  <br/> |モダン認証のみ。  <br/> |接続の失敗。  <br/> |
|Office 2016  <br/> |はい、EnableADAL = 1  <br/> |はい  <br/> |モダン認証のみ。  <br/> |接続の失敗。  <br/> |
|Office 2016  <br/> |はい、EnableADAL = 0  <br/> |いいえ  <br/> |Microsoft Online サインインアシスタントのみ。  <br/> |Microsoft Online サインインアシスタントのみ。  <br/> |
|Office 2013  <br/> |いいえ  <br/> |いいえ  <br/> |Microsoft Online サインインアシスタントのみ。  <br/> |Microsoft Online サインインアシスタントのみ。  <br/> |
|Office 2013  <br/> |はい、EnableADAL = 1  <br/> |はい  <br/> |モダン認証のみ。  <br/> |接続の失敗。  <br/> |
   
### <a name="skype-for-business-online"></a>Skype for Business Online
<a name="BK_SFBO"> </a>

次の表に、Office 2013 または Office 2016 クライアントアプリが先進認証を使用して、または使用していない Skype for Business Online に接続する場合の認証動作を示します。
  
|Office クライアントアプリのバージョン * * * *|レジストリキーが存在するかどうか * * * *|モダン認証は? * * * *|テナントで先進認証がオンになっている認証動作 * * * *|テナントの先進認証がオフになっている認証動作 (既定) * * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |No、または EnableADAL = 1  <br/> |はい  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、Microsoft Online サインインアシスタントが使用されます。 Skype for Business Online テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、Microsoft Online サインインアシスタントが使用されます。 Skype for Business Online テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |
|Office 2016  <br/> |はい、EnableADAL = 1  <br/> |はい  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、Microsoft Online サインインアシスタントが使用されます。 Skype for Business Online テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、Microsoft Online サインインアシスタントが使用されます。 Skype for Business Online テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |
|Office 2016  <br/> |はい、EnableADAL = 0  <br/> |いいえ  <br/> |Microsoft Online サインインアシスタントのみ。  <br/> |Microsoft Online サインインアシスタントのみ。  <br/> |
|Office 2013  <br/> |いいえ  <br/> |いいえ  <br/> |Microsoft Online サインインアシスタントのみ。  <br/> |Microsoft Online サインインアシスタントのみ。  <br/> |
|Office 2013  <br/> |はい、EnableADAL = 1  <br/> |はい  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、Microsoft Online サインインアシスタントが使用されます。 Skype for Business Online テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |Microsoft Online サインインアシスタントのみ。  <br/> |
   
## <a name="see-also"></a>関連項目

[Windows デバイスで Office 2013 の先進認証を有効にする](https://support.office.com/article/enable-modern-authentication-for-office-2013-on-windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910)

[Office 365 の展開で多要素認証を計画する (Office 365 管理者向け)](https://support.office.com/article/plan-for-multi-factor-authentication-for-office-365-deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

[2段階認証を使用して Office 365 にサインインします (エンドユーザー向け)](https://support.office.com/article/sign-in-to-office-365-with-2-step-verification-2b856342-170a-438e-9a4f-3c092394d3cb)
