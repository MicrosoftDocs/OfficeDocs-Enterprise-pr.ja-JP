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
f1.keywords:
- CSH
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
description: Office 2013 と2016クライアントアプリで Microsoft 365 モダン認証が異なるしくみについて説明します。
ms.openlocfilehash: 22f9bf521fc5da367cb8f8d6f02a004baf42a866
ms.sourcegitcommit: d8ca7017b25d5ddc2771e662e02b62ff2058383b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2020
ms.locfileid: "45102605"
---
# <a name="how-modern-authentication-works-for-office-2013-office-2016-and-office-2019-client-apps"></a>Office 2013、Office 2016、および Office 2019 クライアントアプリでの先進認証のしくみ

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

この記事では、Office 2013 および Office 2016 クライアントアプリが、Exchange Online、SharePoint Online、Skype for Business Online の Microsoft 365 テナントの認証構成に基づいて先進認証機能を使用する方法について説明します。

> [!NOTE]
> Office 2010 や Office for Mac 2011 などのレガシクライアントアプリは先進認証をサポートしておらず、基本認証でのみ使用できます。

## <a name="availability-of-modern-authentication-for-microsoft-365-services"></a>Microsoft 365 サービスの先進認証の利用可能性

Microsoft 365 サービスの場合、モダン認証の既定の状態は次のとおりです。
  
- 既定では、Exchange Online に対してオン**に**なっています。 オフまたはオンにするには、「 [Exchange Online で先進認証を有効または無効](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662)にする」を参照してください。 
    
- 既定では、SharePoint Online に対してオン**に**なっています。 
    
- 既定では、Skype for Business Online に対してオン**に**なっています。 この機能をオフまたはオンにするには、「[モダン認証のために Skype For Business Online を有効](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)にする」を参照してください。

> [!NOTE]
> 2017 年 8 月 1 日より**前**に作成されたテナントでは、Exchange Online と Skype for Business Online は既定で**オフ**になっています。
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Office クライアントアプリのサインイン動作

Office 2013 クライアントアプリは、既定で従来の認証をサポートしています。 従来の場合は、Microsoft Online サインインアシスタントまたは基本認証のいずれかをサポートしています。 これらのクライアントが先進認証機能を使用するためには、Windows クライアントにレジストリキーが設定されている必要があります。 手順については、「 [Windows デバイスで Office 2013 の先進認証を有効にする](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910)」を参照してください。

Microsoft Office 2013 がインストールされている Windows を実行しているデバイス (たとえばノート PC やタブレット) で先進認証を有効にするには、次のレジストリ キーを設定する必要があります。先進認証を有効にするデバイスごとに、次のキーを設定する必要があります。
  
|**レジストリ キー**|**型**|**値** |
|:-------|:------:|--------:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL  |REG_DWORD  |1   |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |1  |
  
Skype for business での[先進認証 (ADAL) の使用](https://go.microsoft.com/fwlink/p/?LinkId=785431)方法については、「方法」を参照してください。 
  
Office 2016 および Office 2019 クライアントは、既定で先進認証をサポートしており、クライアントがこれらの新しいフローを使用するために必要な操作はありません。 ただし、従来の認証を使用するには、明示的なアクションが必要です。
  
次のリンクをクリックすると、モダン認証が有効になっているかどうかに応じて、Office 2013 と Office 2016 クライアント認証が Microsoft 365 サービスでどのように機能するかを確認できます。
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [Skype for Business Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

次の表は、モダン認証を使用して、または使用しない状態で Exchange Online に接続した場合の Office 2013 または Office 2016 クライアントアプリの認証動作を示しています。
  
|Office クライアントアプリのバージョン * * * *|レジストリキーが存在するかどうか * * * *|モダン認証は? * * * *|テナントで先進認証がオンになっている認証動作 (既定) * * * *|テナントの先進認証がオフになっている認証動作 * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |違います <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |はい  <br/> |Outlook 2010、2013、または2019で先進認証を強制する <br/> [詳細情報](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Outlook クライアント内で先進認証を強制的に実行します。<br/> |
|Office 2019  <br/> |No、または EnableADAL = 1  <br/> |はい  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、基本認証が使用されます。 テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、基本認証が使用されます。 テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |
|Office 2019  <br/> |はい、EnableADAL = 1  <br/> |はい  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、基本認証が使用されます。 テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、基本認証が使用されます。 テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |
|Office 2019  <br/> |はい、EnableADAL = 0  <br/> |いいえ  <br/> |基本認証  <br/> |基本認証  <br/> |
|Office 2016  <br/> |違います <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |はい  <br/> |Outlook 2010、2013、または2016で先進認証を強制する <br/> [詳細情報](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Outlook クライアント内で先進認証を強制的に実行します。<br/> |
|Office 2016  <br/> |No、または EnableADAL = 1  <br/> |はい  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、基本認証が使用されます。 テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、基本認証が使用されます。 テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |
|Office 2016  <br/> |はい、EnableADAL = 1  <br/> |はい  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、基本認証が使用されます。 テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、基本認証が使用されます。 テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |
|Office 2016  <br/> |はい、EnableADAL = 0  <br/> |いいえ  <br/> |基本認証  <br/> |基本認証  <br/> |
|Office 2013  <br/> |いいえ  <br/> |いいえ  <br/> |基本認証  <br/> |基本認証  <br/> |
|Office 2013  <br/> |はい、EnableADAL = 1  <br/> |はい  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、基本認証が使用されます。 テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、基本認証が使用されます。 テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |
   
<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

次の表に、モダン認証を使用して、または使用しない状態で SharePoint Online に接続した場合の Office 2013 または Office 2016 クライアントアプリの認証動作を示します。
  
|Office クライアントアプリのバージョン * * * *|レジストリキーが存在するかどうか * * * *|モダン認証は? * * * *|テナントで先進認証がオンになっている認証動作 (既定) * * * *|テナントの先進認証がオフになっている認証動作 * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |No、または EnableADAL = 1  <br/> |はい  <br/> |モダン認証のみ。  <br/> |接続の失敗。  <br/> |
|Office 2019  <br/> |はい、EnableADAL = 1  <br/> |はい  <br/> |モダン認証のみ。  <br/> |接続の失敗。  <br/> |
|Office 2019  <br/> |はい、EnableADAL = 0  <br/> |いいえ  <br/> |Microsoft Online サインインアシスタントのみ。  <br/> |Microsoft Online サインインアシスタントのみ。  <br/> |
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
|Office 2019  <br/> |No、または EnableADAL = 1  <br/> |はい  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、Microsoft Online サインインアシスタントが使用されます。 Skype for Business Online テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、Microsoft Online サインインアシスタントが使用されます。 Skype for Business Online テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |
|Office 2019  <br/> |はい、EnableADAL = 1  <br/> |はい  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、Microsoft Online サインインアシスタントが使用されます。 Skype for Business Online テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、Microsoft Online サインインアシスタントが使用されます。 Skype for Business Online テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |
|Office 2019  <br/> |はい、EnableADAL = 0  <br/> |いいえ  <br/> |Microsoft Online サインインアシスタントのみ。  <br/> |Microsoft Online サインインアシスタントのみ。  <br/> |
|Office 2016  <br/> |No、または EnableADAL = 1  <br/> |はい  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、Microsoft Online サインインアシスタントが使用されます。 Skype for Business Online テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、Microsoft Online サインインアシスタントが使用されます。 Skype for Business Online テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |
|Office 2016  <br/> |はい、EnableADAL = 1  <br/> |はい  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、Microsoft Online サインインアシスタントが使用されます。 Skype for Business Online テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、Microsoft Online サインインアシスタントが使用されます。 Skype for Business Online テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |
|Office 2016  <br/> |はい、EnableADAL = 0  <br/> |いいえ  <br/> |Microsoft Online サインインアシスタントのみ。  <br/> |Microsoft Online サインインアシスタントのみ。  <br/> |
|Office 2013  <br/> |いいえ  <br/> |いいえ  <br/> |Microsoft Online サインインアシスタントのみ。  <br/> |Microsoft Online サインインアシスタントのみ。  <br/> |
|Office 2013  <br/> |はい、EnableADAL = 1  <br/> |はい  <br/> |最初にモダン認証が試行されます。 サーバーが最新の認証接続を拒否した場合は、Microsoft Online サインインアシスタントが使用されます。 Skype for Business Online テナントが有効になっていない場合、サーバーはモダン認証を拒否します。  <br/> |Microsoft Online サインインアシスタントのみ。  <br/> |
   
## <a name="see-also"></a>関連項目

[Windows デバイスの Office 2013 の先進認証を有効にする](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/enable-modern-authentication)

[Microsoft 365 の多要素認証](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/multi-factor-authentication-microsoft-365)

[多要素認証を使用した Microsoft 365 へのサインイン](https://support.microsoft.com/office/sign-in-to-microsoft-365-with-multi-factor-authentication-2b856342-170a-438e-9a4f-3c092394d3cb)

[Microsoft 365 Enterprise の概要](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
