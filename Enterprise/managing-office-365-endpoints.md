---
title: Office 365 エンドポイントの管理
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 7/18/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: ネットワークによっては、Office 365 にアクセスできる、ネットワークとプロキシの管理者は、Fqdn では、Url のリストを管理する必要があります、および IP アドレスなどのネットワーク上のコンピューターは、Office 365 エンドポイントの一覧を構成することを確認するのには、インターネットへのアクセスを制限するように設計されています。これらのネットワーク要求を確認するのにはファイルのプロキシまたはファイアウォールの規則および PAC に追加する必要性は、Office 365 に到達することができます。
ms.openlocfilehash: a1a658ff04bc7306cb953477798d3e32d894d695
ms.sourcegitcommit: 854653f927c9515024a1c9e0a86fd5f2fadb92f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "25359499"
---
# <a name="managing-office-365-endpoints"></a>Office 365 エンドポイントの管理

## <a name="office-365-network-connectivity"></a>Office 365 のネットワーク接続

 Office 365 への接続は、非常に大きく、最適なユーザーに近い低レイテンシの出口を構成するときを実行する信頼されたネットワーク要求で構成されます。いくつかの Office 365 の接続は、接続の最適化を利用できます。 
  
1. ファイアウォールのことを確認 Office 365 エンドポイントへの接続のリストを使用できるようにします。
    
2. ワイルドカードと未公開の宛先へのインターネット接続を許可するのに、プロキシ インフラストラクチャを使用します。
    
3. 最適な境界領域のネットワーク構成を管理します。
    
4. [最適な接続を取得していることを確認](https://aka.ms/o365perfprinciples)します。
    
5. 安全に Office 365 のトラフィックを管理し、最高のパフォーマンスを取得するための接続の原理を理解するのには[Office 365 のネットワーク接続性の原則](office-365-network-connectivity-principles.md)を参照してください。 
    
![ファイアウォールやプロキシ経由で Office 365 に接続します。](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)
  
## <a name="update-your-firewalls-outbound-allow-lists"></a>更新プログラム、ファイアウォールの外部リストを許可します。

すべての信頼されたファイアウォールを使用して直接 Office 365 のネットワーク要求を送信する、すべての他のパケット レベルの検査をバイパスする処理では、ネットワークを最適化できます。これは、遅延から低速のパフォーマンスが低下し、境界領域の容量要件を軽減します。ネットワークを信頼するように要求を選択する最も簡単な方法では、当社の[事前構成済みの PAC ファイル](managing-office-365-endpoints.md#pacfiles)を使用します。 
  
ファイアウォールのブロックの送信トラフィックでは、すべての ip アドレスを確認する必要があり、この[XML ファイル](https://go.microsoft.com/fwlink/?LinkId=533185)で**必要な**のと Fqdn が表示されている場合は、許可リストには。いくつかサード パーティのサービスを使用する必要のすべてのサービスを認識します。おしないこれらのサード パーティ サービス プロバイダー、コンテンツ配信ネットワークでは、DNS プロバイダーの証明書などの IP アドレスを提供するとします。すべての Office 365 の機能は、方法に関する情報を多く公開して先に関係なく、Office 365 によって要求されたすべての宛先に到達できる必要があります。 
  
この機能を使用する必要があります解決するにはネットワーク要求の現在の IP アドレスが要求されていると、送信する、多数の宛先が、公開されている IP アドレスがないか、またはない特定の完全修飾ドメイン名を使用して、ワイルドカード ドメインとして登録されている、インターネット経由で要求をネットワークします。
  
自分の代わりに XML ファイルを解析し、サービスまたは機能に基づいて自動的にファイアウォールを使用して直接ルーティングするルールを更新するためのファイアウォールを使用して、プロセスを自動化します。コミュニティによって作成され、する Cisco XE の工順または ACL の一覧の構成、テキスト形式または CSV にエクスポート オプションを使用して XML を解析する[Azure 範囲](https://azurerange.azurewebsites.net/)ツールを使用することもできます。 
  
ネットワーク宛先の長い説明は、[参照サイト](urls-and-ip-address-ranges.md)も、[ベースの RSS の変更ログ](https://go.microsoft.com/fwlink/p/?linkid=236301)から変更を購読することができますので。 
  
<a name="pacfiles"> </a>
## <a name="configure-outbound-paths-with-pac-files"></a>PAC ファイルを使用して送信パスを構成します。

WPAD PAC ファイルを使用すると、Office 365 に関連付けられているが、提供されている IP アドレスがないネットワーク要求を管理できます。プロキシまたは境界デバイス経由で送信される一般的なネットワーク要求には、追加の遅延が発生します。プロキシ認証では、最大の税を支払う、評判の検索などのパケットを検査する試みは、他のサービスが、ユーザー エクスペリエンスの低下します。さらに、これらの境界ネットワーク デバイスには、すべてのネットワーク要求を処理するために十分な容量が必要があります。Office 365 のネットワーク要求を渡すため、プロキシや検査のインフラストラクチャをバイパスすることをお勧めします。
  
出発点としてどのようなネットワーク トラフィックは、プロキシに送信され、ファイアウォールに送信されますを決定するのに、PAC ファイルのいずれかを使用します。新しい PAC ファイルまたは WPAD ファイルに、Office 365 のコンサルタントのいずれかから[PAC ファイルの展開](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/)については、この投稿を読む場合。出発点としてこれらを確認し、お客様の環境に合わせて編集します。 
  
 **PAC ファイルを 7/10/2018 を更新**します。 
  
### <a name="1---pac-file-separates-required-internet-fqdns-from-known-office-365-fqdn"></a>#1 - PAC ファイル: 必要な既知の Office 365 の FQDN から Fqdn をインターネットを分離します。

最初の例では、我々 の推奨されるアプローチのみインターネット上でエンドポイントを管理するためのデモです。Office 365 の宛先 IP アドレスが公開され、残りのネットワーク要求をプロキシに送信のためのプロキシをバイパスします。
  
コード スニペット:

```javascript
// JavaScript source code
//July 2018 - Updates go live 1st August2018
//This PAC file contains all FQDNs needed for all services and splits the traffic between those which Microsoft can provide IPs for (so can be sent through a managed firewall with conditional access if desired) and those which IPs cannot be provided for, so need to go to an unrestricted proxy or egress. 
//Due to the use of wildcards, some extra logic is provided to send traffic to the proxy before a 'direct' wildcard is hit.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    var proxyserver2 = "PROXY 10.10.10.11:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //Catch explicit FQDNs which need the proxy but are covered under wildcarded FQDNs which have IPs. This has to be done first before the wildcard is hit
    if ((shExpMatch(host, "quicktips.skypeforbusiness.com"))    
        || (shExpMatch(host, "*.um.outlook.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r1.res.office365.com")))
    {
        return proxyserver;
    }
        //Send FQDNs which Microsoft provide IPs for direct, so they can be sent via a firewall
    else if ((isPlainHostName(host))
    || (shExpMatch(host, "*.aria.microsoft.com"))    
    || (shExpMatch(host, "*.dc.trouter.io"))
    || (shExpMatch(host, "*.lync.com"))
    || (shExpMatch(host, "*.manage.office.com"))
    || (shExpMatch(host, "*.office365.com"))
    || (shExpMatch(host, "*.onenote.com"))
    || (shExpMatch(host, "*.outlook.com"))
    || (shExpMatch(host, "*.outlook.office.com"))
    || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
    || (shExpMatch(host, "*.protection.office.com"))
    || (shExpMatch(host, "*.sharepoint.com"))
    || (shExpMatch(host, "*.skype.com"))
    || (shExpMatch(host, "*.skypeforbusiness.com"))
    || (shExpMatch(host, "*.svc.ms"))
    || (shExpMatch(host, "*.teams.microsoft.com"))
    || (shExpMatch(host, "*.yammer.com"))
    || (shExpMatch(host, "*.yammerusercontent.com"))    
    || (shExpMatch(host, "*broadcast.officeapps.live.com"))
    || (shExpMatch(host, "*excel.officeapps.live.com"))
    || (shExpMatch(host, "*onenote.officeapps.live.com"))
    || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
    || (shExpMatch(host, "*view.officeapps.live.com"))
    || (shExpMatch(host, "*visio.officeapps.live.com"))
    || (shExpMatch(host, "*word-edit.officeapps.live.com"))
    || (shExpMatch(host, "*word-view.officeapps.live.com"))
    || (shExpMatch(host, "admin.microsoft.com"))    
    || (shExpMatch(host, "account.office.net"))
    || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
    || (shExpMatch(host, "agent.office.net"))
    || (shExpMatch(host, "api.login.microsoftonline.com"))
    || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "apc.delve.office.com"))
    || (shExpMatch(host, "aus.delve.office.com"))
    || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
    || (shExpMatch(host, "becws.microsoftonline.com"))
    || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
    || (shExpMatch(host, "can.delve.office.com"))
    || (shExpMatch(host, "ccs.login.microsoftonline.com"))
    || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
    || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
    || (shExpMatch(host, "clientlog.portal.office.com"))
    || (shExpMatch(host, "companymanager.microsoftonline.com"))
    || (shExpMatch(host, "cus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "delve.office.com"))
    || (shExpMatch(host, "device.login.microsoftonline.com"))    
    || (shExpMatch(host, "ea-000.tasks.osi.office.net"))
    || (shExpMatch(host, "eur.delve.office.com"))
    || (shExpMatch(host, "eus-zzz.tasks.osi.office.net"))
    || (shExpMatch(host, "gbr.delve.office.com"))    
    || (shExpMatch(host, "hip.microsoftonline-p.net"))
    || (shExpMatch(host, "hipservice.microsoftonline.com"))
    || (shExpMatch(host, "home.office.com"))
    || (shExpMatch(host, "ind.delve.office.com"))
    || (shExpMatch(host, "jpn.delve.office.com"))
    || (shExpMatch(host, "kor.delve.office.com"))
    || (shExpMatch(host, "lam.delve.office.com"))
    || (shExpMatch(host, "login.microsoft.com"))
    || (shExpMatch(host, "login.microsoftonline.com"))
    || (shExpMatch(host, "login.microsoftonline-p.com"))
    || (shExpMatch(host, "login.windows.net"))
    || (shExpMatch(host, "logincert.microsoftonline.com"))
    || (shExpMatch(host, "loginex.microsoftonline.com"))
    || (shExpMatch(host, "login-us.microsoftonline.com"))     
    || (shExpMatch(host, "manage.office.com"))
    || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
    || (shExpMatch(host, "nam.delve.office.com"))
    || (shExpMatch(host, "neu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "nexus.microsoftonline-p.com"))
    || (shExpMatch(host, "nexus.officeapps.live.com"))
    || (shExpMatch(host, "nexusrules.officeapps.live.com"))
    || (shExpMatch(host, "office.live.com"))
    || (shExpMatch(host, "officeapps.live.com"))
    || (shExpMatch(host, "passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "portal.microsoftonline.com"))
    || (shExpMatch(host, "portal.office.com"))
    || (shExpMatch(host, "protection.office.com"))
    || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
    || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net"))   
    || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))
    || (shExpMatch(host, "sea-000.tasks.osi.office.net"))    
    || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
    || (shExpMatch(host, "suite.office.net"))    
    || (shExpMatch(host, "tasks.office.com"))
    || (shExpMatch(host, "teams.microsoft.com"))
    || (shExpMatch(host, "testconnectivity.microsoft.com"))
    || (shExpMatch(host, "webshell.suite.office.com"))
    || (shExpMatch(host, "weu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "wus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "www.office.com")))

    {
        return "DIRECT";
    }
    else
        // Send all unknown IP traffic to Proxy for unrestricted access. This section is not necessary if you have a catchall for all other traffic to go to an unfiltered proxy. 
        //However the fqdns required, but for which we dont have IPs for, are listed here incase you need an explicit list.
   if          ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com")) 
        || (shExpMatch(host, "*.adl.windows.com"))   
        || (shExpMatch(host, "*.api.microsoftstream.com"))      
        || (shExpMatch(host, "*.assets-yammer.com"))   
        || (shExpMatch(host, "*.azureedge.net"))            
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))   
        || (shExpMatch(host, "*.helpshift.com"))   
        || (shExpMatch(host, "*.hockeyapp.net"))    
        || (shExpMatch(host, "*.localytics.com"))    
        || (shExpMatch(host, "*.log.optimizely.com"))    
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))      
        || (shExpMatch(host, "*.msocdn.com")) 
        || (shExpMatch(host, "*.mstea.ms"))    
        || (shExpMatch(host, "*.notification.api.microsoftstream.com")) 
        || (shExpMatch(host, "*.o365weve.com"))     
        || (shExpMatch(host, "*.office.com"))   
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.phonefactor.net"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))  
        || (shExpMatch(host, "*.sfbassets.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.teams.microsoft.com"))  
        || (shExpMatch(host, "*.tenor.com"))  
        || (shExpMatch(host, "*.symcd.com"))     
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))  
        || (shExpMatch(host, "apps.identrust.com"))  
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))        
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com")) 
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))
        || (shExpMatch(host, "connect.facebook.net"))        
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))          
        || (shExpMatch(host, "ecn.dev.virtualearth.net "))   
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))             
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))        
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))   
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))   
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))        
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))      
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))       
        || (shExpMatch(host, "ocsp2.globalsign.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))            
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))              
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net")) 
        || (shExpMatch(host, "r1.res.office365.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))         
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))   
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))  
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "sway.com")) 
        || (shExpMatch(host, "teams.microsoft.com"))              
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))         
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))    
        || (shExpMatch(host, "web.microsoftstream.com"))         
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))   
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com"))
        || (shExpMatch(host, "xsi.outlook.com")))

    {
        return proxyserver;
    }
    //Catchall for all other traffic to another proxy 
else return proxyserver;
}

```

### <a name="2---pac-file-connect-to-office-365-over-the-internet-and-expressroute"></a>#2 - PAC ファイル: ExpressRoute、インターネット経由で Office 365 に接続
<a name="bkmk_inet-aer"> </a>

2 番目の例は、ExpressRoute とインターネット回線が利用できる場合は、接続を管理するための当社の推奨される方法のデモンストレーションです。ExpressRoute ExpressRoute 回路の出力先を提供して、インターネット プロキシの出力先を提供のみを送信します。
  
コード スニペット:

```javascript
// JavaScript source code
//July 2018 Update
// Consolidated FQDNs of URLS which are reachable via Microsoft peering over ExpressRoute. All other traffic sent to a proxy in this example. 
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your traffic flow needs and the Office 365 URL &amp; IP page. 
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
//PAC presumes all Office 365 BGP communities/route filters are allowed.
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //SUB-FQDNs of ExpressRoutable wildcards which need to be explicitly sent to the proxy at the top of the PAC because they arent ER routable
    if ((shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "quicktips.skypeforbusiness.com"))
        || (shExpMatch(host, "*.um.outlook.com")))                  
    {
        return proxyserver;
    }
        //EXPRESS ROUTE DIRECT
    else if ((isPlainHostName(host))  
            || (shExpMatch(host, "*.aria.microsoft.com"))             
            || (shExpMatch(host, "*.dc.trouter.io"))
            || (shExpMatch(host, "*.lync.com"))
            || (shExpMatch(host, "*.manage.office.com"))
            || (shExpMatch(host, "*.outlook.com"))
            || (shExpMatch(host, "*.outlook.office.com"))
            || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
            || (shExpMatch(host, "*.protection.office.com"))
            || (shExpMatch(host, "*.protection.outlook.com"))
            || (shExpMatch(host, "*.sharepoint.com")) 
            || (shExpMatch(host, "*.skype.com")) 
            || (shExpMatch(host, "*.skypeforbusiness.com")) 
            || (shExpMatch(host, "*.svc.ms"))   
            || (shExpMatch(host, "*.teams.microsoft.com"))  
            || (shExpMatch(host, "*broadcast.officeapps.live.com"))
            || (shExpMatch(host, "*excel.officeapps.live.com"))
            || (shExpMatch(host, "*onenote.officeapps.live.com"))
            || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
            || (shExpMatch(host, "*view.officeapps.live.com"))                                 
            || (shExpMatch(host, "*visio.officeapps.live.com"))
            || (shExpMatch(host, "*word-edit.officeapps.live.com"))
            || (shExpMatch(host, "*word-view.officeapps.live.com"))
            || (shExpMatch(host, "account.office.net"))
            || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
            || (shExpMatch(host, "agent.office.net"))  
            || (shExpMatch(host, "apc.delve.office.com"))
            || (shExpMatch(host, "api.login.microsoftonline.com"))
            || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "aus.delve.office.com"))
            || (shExpMatch(host, "autologon.microsoftazuread-sso.com")) 
            || (shExpMatch(host, "becws.microsoftonline.com"))
            || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
            || (shExpMatch(host, "can.delve.office.com")) 
            || (shExpMatch(host, "ccs.login.microsoftonline.com"))  
            || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
            || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
            || (shExpMatch(host, "companymanager.microsoftonline.com"))
            || (shExpMatch(host, "delve.office.com"))
            || (shExpMatch(host, "device.login.microsoftonline.com"))
            || (shExpMatch(host, "domains.live.com")) 
            || (shExpMatch(host, "eur.delve.office.com"))
            || (shExpMatch(host, "gbr.delve.office.com"))
            || (shExpMatch(host, "hip.microsoftonline-p.net"))
            || (shExpMatch(host, "hipservice.microsoftonline.com"))
            || (shExpMatch(host, "home.office.com"))
            || (shExpMatch(host, "ind.delve.office.com"))
            || (shExpMatch(host, "jpn.delve.office.com"))
            || (shExpMatch(host, "kor.delve.office.com"))
            || (shExpMatch(host, "lam.delve.office.com"))
            || (shExpMatch(host, "login.microsoft.com"))
            || (shExpMatch(host, "login.microsoftonline.com"))
            || (shExpMatch(host, "login.microsoftonline-p.net"))
            || (shExpMatch(host, "login.windows.net"))
            || (shExpMatch(host, "logincert.microsoftonline.com"))
            || (shExpMatch(host, "loginex.microsoftonline.com"))
            || (shExpMatch(host, "login-us.microsoftonline.com"))
            || (shExpMatch(host, "manage.office.com"))
            || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
            || (shExpMatch(host, "nam.delve.office.com"))
            || (shExpMatch(host, "nexus.microsoftonline-p.net"))
            || (shExpMatch(host, "office.live.com")) 
            || (shExpMatch(host, "officeapps.live.com")) 
            || (shExpMatch(host, "outlook.office365.com")) 
            || (shExpMatch(host, "passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "portal.office.com"))
            || (shExpMatch(host, "protection.office.com"))
            || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
            || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
            || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))  
            || (shExpMatch(host, "signup.microsoft.com"))
            || (shExpMatch(host, "smtp.office365.com"))  
            || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
            || (shExpMatch(host, "suite.office.net")) 
            || (shExpMatch(host, "teams.microsoft.com")) 
            || (shExpMatch(host, "webshell.suite.office.com")) 
            || (shExpMatch(host, "www.office.com")))             
       
    {
        return "DIRECT";
    }
        //Catchall for all other traffic to proxy
    else
    {
        return proxyserver;
    }
}

```

### <a name="3---pac-file-manage-all-office-365-destinations-collectively"></a>#3 - PAC ファイル: Office 365 のすべての宛先を一括管理
<a name="bkmk_inet-direct"> </a>

3 番目の例では、単一の宛先を Office 365 に関連するすべてのネットワーク要求を送信することを示します。これは Office 365 のネットワーク要求のすべての検査をバイパスして、PAC 形式のカスタマイズに使用する] ボックスの一覧では、エンドポイントの公開されているすべての書式が用意されています。
  
コード スニペット:

```javascript
// JavaScript source code
//July 2018 Update new URLS go live 1st August 2018 -
//Consolidated FQDNs required to access Office 365 - All services including optional components covered and elements covered under wildcards removed. 
//Some repeated domains have been consoliodated into unpublished wildcards in order to keep the file as small as possible.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
   if  ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com"))
        || (shExpMatch(host, "*.adl.windows.com"))
        || (shExpMatch(host, "*.api.microsoftstream.com"))  
        || (shExpMatch(host, "*.assets-yammer.com"))
        || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
        || (shExpMatch(host, "*.azureedge.net"))   
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net")) 
        || (shExpMatch(host, "*.dc.trouter.io"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))
        || (shExpMatch(host, "*.helpshift.com"))
        || (shExpMatch(host, "*.hockeyapp.net"))       
        || (shExpMatch(host, "*.localytics.com"))
        || (shExpMatch(host, "*.log.optimizely.com"))     
        || (shExpMatch(host, "*.lync.com"))
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))
        || (shExpMatch(host, "*.msocdn.com"))
        || (shExpMatch(host, "*.mstea.ms"))
        || (shExpMatch(host, "*.o365weve.com"))
        || (shExpMatch(host, "*.office.com"))
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.office365.com"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onenote.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.outlook.com"))
        || (shExpMatch(host, "*.phonefactor.net")) 
        || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))
        || (shExpMatch(host, "*.sfbassets.com"))  
        || (shExpMatch(host, "*.sharepoint.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.skype.com"))
        || (shExpMatch(host, "*.skypeforbusiness.com"))
        || (shExpMatch(host, "*.svc.ms")) 
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.symcd.com"))
        || (shExpMatch(host, "*.tenor.com"))
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*.yammer.com"))
        || (shExpMatch(host, "*.yammerusercontent.com"))         
        || (shExpMatch(host, "*broadcast.officeapps.live.com"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "*excel.officeapps.live.com"))
        || (shExpMatch(host, "*onenote.officeapps.live.com"))
        || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
        || (shExpMatch(host, "*view.officeapps.live.com"))
        || (shExpMatch(host, "*visio.officeapps.live.com"))
        || (shExpMatch(host, "*word-edit.officeapps.live.com"))
        || (shExpMatch(host, "*word-view.officeapps.live.com"))    
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))
        || (shExpMatch(host, "apps.identrust.com")) 
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))    
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com"))
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))     
        || (shExpMatch(host, "connect.facebook.net"))
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))      
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))           
        || (shExpMatch(host, "ecn.dev.virtualearth.net"))
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))               
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))   
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))     
        || (shExpMatch(host, "ocsp2.globalsign.com")) 
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "office.live.com"))
        || (shExpMatch(host, "officeapps.live.com"))
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))              
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "s0.assets-yammer.com"))  
        || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
        || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))              
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))    
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "web.microsoftstream.com"))   
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))  
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))        
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com")))
    {
        return proxyserver;
    }
        //Catchall for all other traffic to another proxy
    else return "PROXY 10.10.10.11:8080";
}

```

### <a name="use-custom-scripts-or-manually-create-your-own-pac-files"></a>カスタム スクリプトを使用するか PAC ファイルを手動で作成します。
<a name="pacfiles_manual"> </a>

構築した休暇を共有するには何かコメントでメモここでは、コミュニティからのいくつかの他のツールです。この資料で参照されているツールが公式にはコミュニティのサポートされているなし、マイクロソフトが管理しているし、利便性のためにここで説明します。
  
- これは、Office 365 コミュニティのメンバーによって作成されたツール、プロセスを管理するための最も古いコミュニティの生成ツールです。ここでは、[ダウンロード](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7)へのリンクです。
    
- エクスポート可能なファイアウォール規則の概念実証:[マイクロソフト クラウド IP API](https://mscloudips.azurewebsites.net/)です。
    
- IT Praktyk: [RSS 変換](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7)を[XML に変換](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896)します。
    
- Peter Abele: から[ダウンロード](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3)してください。
    
- どのネットワークを決定する、ネットワークの分析を要求する使用は、プロキシ インフラストラクチャをバイパスする必要があります。顧客プロキシをバイパスするために使用する最も一般的な Fqdn には、これらのエンドポイントから送信されると、ネットワーク トラフィック量のため、次が含まれています。
    
  ```
  outlook.office365.com
  outlook.office.com
  <tenant-name>.sharepoint.com
  <tenant-name>-my.sharepoint.com
  <tenant-name>-<app>.sharepoint.com
  *.Lync.com
  ```

- 直接ファイアウォールに送信されるすべてのネットワーク要求がファイアウォールを経由する要求を許可する] ボックスの一覧を許可するに対応するエントリを持つようにします。

## <a name="perimeter-network-integration"></a>境界領域ネットワークの統合
<a name="BKMK_Perimeter"> </a>

役に立つ情報マイクロソフトの WAN では、世界最大規模のバックボーンの 1 つですか。
  
この大規模なネットワークは、どの Office 365 とその他のクラウド サービスは世界中の場所に関係なく動作します。高帯域幅、低レイテンシ、フェイル オーバー対応リンクの何千もの民間企業の暗い光ファイバー、およびクラウド サービスを使用して容易にできるようにするのにはすべてのデータ センターとエッジのノード間の接続を複数 Terabit のルートのマイルに当社のネットワークで構成されます。
  
このようなネットワークを使って、できるだけ早く、ネットワークに接続するのには、組織のデバイスをします。2500 以上の ISP のピアリング関係を持つグローバルなプレゼンス、70 ポイントへのネットワークから取得する必要がありますシームレスです。ISP のピアリング関係では、最適です[ここでいくつかの例では](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__)良好ではだめですねピアリングのやり取りに当社のネットワークのことを確認する数分を費やすのも悪くないことはできません。 
  
手動で、または自動的に最適な状態で使用する機器によって、Office 365 アプリケーションのネットワーク要求を処理するために、ネットワーク上のデバイスを構成します。どのような最適な状態で Office 365 のネットワーク トラフィックを処理するために必要な構成の変更は、お客様の環境によって異なります。Office 365 のネットワーク要求には、次のネットワーク構成が挙げられます。
  
- 重要度の低いネットワーク ・ トラフィックの優先順位です。
    
- 低速の WAN 経由で backhauling を避けるためにローカルの出口へのルーティング リンクを活用しながら低レーテンシーの利用可能な Microsoft のネットワークにします。[詳細はここでは、](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/)お客様との契約に基づきます。 
    
- ローカル出口の近くで DNS を使用したネットワーク要求をローカルの出口を離れることを確認は、最も近い Microsoft ピアリングの場所に到着します。
    
- 詳細なパケット検査やその他の負荷の高いネットワーク パケットをスケールで待機時間の要件を満たすための処理から除外します。
    
最新のネットワーク デバイスには、汎用的な信頼されていないインターネット トラフィックとは異なる Office 365 などの信頼されたアプリケーションのネットワーク要求を管理する機能が含まれます。SD WAN ソリューションの新たな展望を持つこのようなトラフィックとパスの選択の差別化要因と実行することも時間の可用性、遅延またはパフォーマンスのさまざまな接続パスのポイントなど、ネットワークの変更の状態の認識でユーザーと、クラウドです。
  
ネットワーク構成の計画に関する追加のガイダンスについては、[ネットワークと Office 365 の移行計画](network-and-migration-planning.md)、[パフォーマンスのトラブルシューティング Office 365 のプラン](performance-troubleshooting-plan.md)、および[Office 365 の展開計画のチェックリスト](deployment-planning-checklist.md)を参照してください。 
  
### <a name="to-implement-this-scenario"></a>このシナリオを実装するには。

ネットワーク ソリューションまたはサービス プロバイダーに確認して Office 365 の URL を使用することができ、IP の定義のローカル (ユーザー)、低オーバーヘッドを容易にするために XML からネットワークのトラフィックを Office 365 の出口、他のアプリケーションに対して優先順位を管理し、調整した場合、Office 365 のネットワークの状態を変更することによって Microsoft のネットワーク接続のネットワーク パスです。一部のソリューションをダウンロードして、スタック内の Office 365 の URL と IP の Xml 定義を自動化します。
  
常に確実に導入済みのソリューションでは、弾力性、適切な地域の Office 365 のトラフィックのネットワーク パスの冗長性のために必要な程度には Office 365 の Url や ip アドレスの変更に対応して発行になります。

## <a name="faq"></a>FAQ

接続に関する管理者のよく寄せられる質問:
  
### <a name="how-do-i-submit-a-question"></a>質問を送信する方法は?

か、記事が役に立ちましたかどうかを示すために下部にあるリンクをクリックし、新たな質問を送信します。私たちは、フィードバックを監視し、最も頻繁に寄せられる質問をここで更新します。
  
### <a name="when-is-the-xml-file-updated"></a>XML ファイルが更新されたとき

新しいエンドポイントを発表しましたが、ときに通常は 30 + 1 日のバッファーが有効なネットワーク要求がそれらに移動を開始する前に。このバッファーは、お客様を確認して、パートナーに自分のシステムを更新する機会があります。FQDN と IP プレフィックスの追加と削除は、すなわち、新しい FQDN は XML ファイルで使用する前に 30 日間、お知らせと同時に XML ファイルで処理されます。停止発表と同時に、XML からエンドポイントを削除する際にそれらの削除を発表する前に削除している私たちのエンドポイントへのネットワーク要求を送信するためには既に使用されません。
  
### <a name="how-can-i-be-notified-of-changes"></a>方法ことができますか変更が通知されるでしょうか。
<a name="bkmk_changes"> </a>

Office 365 エンドポイントは、毎月 30 日間の通知の最後に発行されます。変更が 1 か月に 2 回以上を発生することがありますか、通知期間が短い。エンドポイントを追加する場合の[RSS フィード](https://go.microsoft.com/fwlink/p/?linkid=236301)に記載されている有効日は、エンドポイントに、ネットワーク要求を送信すた後日付です。RSS を新しいなら、ここでは、方法には、 [Outlook で購読](https://go.microsoft.com/fwlink/p/?LinkId=532416)するか、または[RSS フィードのメールでの更新がある](https://go.microsoft.com/fwlink/p/?LinkId=532417)ことができます。
  
### <a name="how-do-i-read-the-rss-change-log"></a>RSS 変更のログを読み取る方法
<a name="bkmk_changes"> </a>

RSS フィードを購読すると後を解析することについては、手動でまたはスクリプトを使用しています。次の表形式の RSS フィード o 容易にできるようにします。
  
|**セクション**|**パート 1**|**パート 2**|**パート 3**|**パート 4**|**第 5 部**|**第 6 部**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|**説明** <br/> |カウント  <br/> |エンドポイントに送信されるネットワーク要求を必要とするその後の日付です。  <br/> |機能またはエンドポイントを必要とするサービスの基本的な説明です。  <br/> |インターネットだけでなく、ExpressRoute 回路では、このエンドポイントに接続することができますか。  <br/> |**[はい]** - インターネットと ExpressRoute の両方では、このエンドポイントに接続することができます。  <br/> **[いいえ**] - インターネット上には、このエンドポイントに接続するだけです。  <br/> |ターゲット FQDN または IP 範囲を追加または削除されています。  <br/> |
|**使用例** <br/> |1/  <br/> |[効果的な xx と xx と xxx。  <br/> |必要な:\<説明\>。  <br/> |ExpressRoute。  <br/> |\<はい/いいえ\>。  <br/> |\<FQDN と IP\>]、  <br/> |

その他の点に注意してください、すべてのエントリには、一般的な一連の区切り記号:
  
- **/** カウントの後
- 数のエントリを示すために **[** -
- **.**-エントリの独立した各セクションの間に使用
- **]、** - 1 つのエントリの終了を示す
- **].**-すべてのエントリの終了を示すために

### <a name="how-do-i-determine-the-location-of-my-tenant"></a>自分のテナントの場所を確認する方法はありますか

 **テナントの場所**は、当社の[データ センターのマップ](https://o365datacentermap.azurewebsites.net/)を使用して最適な決定されます。
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Am にピアリング適切にマイクロソフトのでしょうか。

 **Peering の場所**については、[マイクロソフトとピアリング](https://www.microsoft.com/peering)で詳細に説明します。
  
2500 以上の ISP のピアリング関係を持つグローバルなプレゼンス、70 ポイントへのネットワークから取得する必要がありますシームレスです。ISP のピアリング関係では、最適です[ここでいくつかの例では](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__)良好ではだめですねピアリングのやり取りに当社のネットワークのことを確認する数分を費やすのも悪くないことはできません。 
  
### <a name="how-do-i-determine-which-ip-addresses-to-accept-over-expressroute"></a>判別する方法 ExpressRoute をそのまま使用する IP アドレスですか。

 **ExpressRoute の承認ルート**は、[マイクロソフトの IP の範囲](https://www.microsoft.com/download/details.aspx?id=53602)や特定の Office 365 [BGP コミュニティ](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)によって定義されます。
  
### <a name="how-do-i-determine-which-endpoints-i-need"></a>必要なエンドポイントを判断する方法ですか。

定期的に新しい機能やサービスに追加 Office 365 製品ファミリで、接続性のランドス ケープを展開します。E3、E5 の SKU を購読しているエンドポイントのリストを考慮する簡単な方法がすべてのスイートのすべての機能を取得する必要があります。これらの Sku のいずれかを購読していない場合、違いは、エンドポイントの数は最小限です。
  
[Office 365 のネットワーク接続性の原則](office-365-network-connectivity-principles.md)については、Office 365 エンドポイントのカテゴリを取得して安全に Office 365 のトラフィックを管理し、最高のパフォーマンスを取得するための接続の原理を理解するのにを参照してください。 
  
下の図では、FQDN、Office オンラインのセクションの表の一部の例を表示できます。行は、機能と接続性の違いによって構成されます。最初の 2 行がマークされているエンドポイントでは、Office オンラインを示す Office 365 の認証と Id、およびポータルで必要し、のセクションを共有します。これは、これらの共有サービスに依存している Office 365 のサービスの一般的です。3 番目の行は、クライアント コンピューターに到達できる必要があることを示します\*です。 Office オンラインと 4 番目の行を使用する officeapps.live.com は、コンピューターが到達することも場合がありますことを示します\*です。 Office オンラインを使用する cdn.office.net です。
  
場合でも、3 つの行の両方と、Office オンラインを使用するために必要な 4 は、先が異なることを示すに分割されています。
  
1. \*。 officeapps.live.com は、CDN はありません、この名前空間への要求の意味は、マイクロソフトのデータ センターに直接送られます。
2. \*。 officeapps.live.com は、マイクロソフトの Peering を使用して ExpressRoute の回路上でアクセス可能です。
3. Office オンラインに関連付けられている IP アドレスと\*です。 officeapps.live.com は、このリンクによって確認できます。
4. \*。 cdn.office.net は、Akamai がホストしている CDN を表し、この名前空間への要求の意味は、akamai 社のデータ センターに送られます。
5. \*。 cdn.office.net は ExpressRoute の回路上でアクセス可能ではありません。
6. Office オンラインに関連付けられている IP アドレスと\*です。 cdn.office.net は使用できません。

![エンドポイント] ページの画面キャプチャ](media/42b487f3-24f3-48fe-9885-f97aae3194f3.png)
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>発行済みの一覧にない IP アドレスへのネットワーク要求を表示すると、必要へのアクセスを提供するでしょうか。
<a name="bkmk_MissingIP"> </a>

のみ IP アドレスを提供する Office 365 サーバーをインターネットまたは ExpressRoute の上に直接にルーティングする必要があります。すべての IP アドレスのネットワーク要求が表示されますの包括的なリストではありません。Microsoft およびサード ・ パーティ製の所有している、パブリッシュされていない場合、IP アドレスへのネットワーク要求が表示されます。これらの IP アドレスが動的に生成されるかを変更するときに、タイムリーな通知を防止する方法で管理します。場合は、ファイアウォールでは、これらのネットワーク要求の Fqdn に基づいてアクセスを許可することはできません、要求を管理するために、PAC または WPAD ファイルを使用します。
  
IP は、Office 365 の詳細情報を表示するに関連付けられているを参照してください。
  
1. [CIDR の電卓](http://jodies.de/ipcalc)を使用して大規模な公開されている範囲の IP アドレスが含まれているかどうかを確認してください。
2. パートナーが[whois クエリ](https://dnsquery.org/)を使用して ip アドレスを所有しているかどうかを参照してください。マイクロソフトが所有している場合は、内部の相手がある可能性があります。
3. 証明書をチェックし、IP アドレスへの接続をブラウザーで*HTTPS://\<と\>*、IP アドレスに関連付けられているどのようなドメインを理解する証明書に記載されているドメインを確認します。場合 IP アドレスを所有している Microsoft は、Office 365 の IP アドレスの一覧ではなく可能性があります IP アドレスは、公開されている IP 情報を使用しないで Microsoft ドメインまたは*MSOCDN.NET*などの Microsoft CDN に関連付けられます。証明書のドメインは、いずれかの IP アドレスの一覧を表示する要求は、行う場合は、知らせてください。

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Nsatc.net や akadns.net では、マイクロソフトのドメイン名などの名前を参照してください理由は?
<a name="bkmk_akamai"> </a>

Office 365 とその他の Microsoft サービスは、Office 365 のエクスペリエンスを向上させるために akamai 社、MarkMonitor などのいくつかのサードパーティのサービスを使用します。最高のエクスペリエンスを提供してください、可能な場合があります変更これらのサービス、将来的にします。操作中に、サード パーティのドメインを所有している、レコード、または IP アドレスを指す CNAME レコード多くの場合発行されます。サード パーティのドメインが、CDN などのコンテンツをホストまたは地理的なトラフィック管理サービスなどのサービスをホストすることがあります。これらのサード パーティへの接続が表示されたら、これらはリダイレクトまたは参照は、最初の要求で、クライアントからではないのです。一部のお客様がこのフォームを参照のことを確認する必要があり、潜在的な Fqdn でサード パーティのサービスの長いリストを使用して可能性がありますを明示的に追加せずにリダイレクトを許可します。
  
サービスの一覧は、いつでも変更されることがします。現在使用中のサービスの一部は次のとおりです。
  
含む要求が表示されたら、 [MarkMonitor](https://www.markmonitor.com/)を使用中は*\*です。 nsatc.net* 。このサービスは、ドメイン名の保護、悪意のある行為から保護するための監視を提供します。
  
要求が表示されたら、 [ExactTarget](https://www.marketingcloud.com/)を使用中は*\*です。 exacttarget.com* 。このサービスは、電子メールのリンクの管理し、悪意のある行為に対する監視を提供します。
  
[Akamai 社](https://www.akamai.com/)は、Fqdn を次のいずれかを含む要求が表示された場合、使用中です。このサービスでは、geo DNS、コンテンツ配信ネットワーク サービスを提供します。
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

### <a name="what-are-the-three-types-of-office-365-endpoints"></a>3 種類の Office 365 の端点を挙げてください。
<a name="bkmk_akamai"> </a>

- DNS 参照や CDN コンテンツの検索などの基本的なインターネット サービスを取得するためにサードパーティのサービスに接続します。また、統合、OneNote ノートブック内の YouTube のビデオを組み込むなどのサードパーティ製のサービスに接続します。
- ホストされ、マイクロソフトがお使いのコンピューターに最も近いインターネット上の場所にあるマイクロソフトのグローバル ・ ネットワークを入力するのにはネットワーク要求を有効にするエッジのノードなどを実行、セカンダリ ・ サービスに接続します。地球上の 3 番目に大きなネットワークとしては、接続エクスペリエンスを向上します。また、さまざまな Office 365 サービスで Azure のメディア サービスを使用するなど、Microsoft Azure サービスに接続します。
- オンラインの Exchange メールボックス サーバーなど、Skype ビジネス オンラインのサーバーが、一意で独自のデータが存在するための Office 365 サービスのプライマリに接続します。FQDN または IP アドレス、プライマリの Office 365 サービスに接続し、インターネットまたは ExpressRoute の回路を使用できます。サード ・ パーティと、インターネット回線で、Fqdn を使用して、セカンダリ ・ サービスにのみ接続できます。

次の図は、これらのサービス領域の違いを示しています。この図では、左下にお客様の設置型のネットワークのネットワーク接続を管理するために複数のネットワーク デバイスがあります。次のような構成は、エンタープライズ規模のお客様に共通です。ネットワークにのみ、クライアント コンピューターと同様にサポートされているインターネットの間にファイアウォールがあるし、ファイアウォールの許可リストのルールに Fqdn およびワイルドカードをサポートできることを確認します。
  
[Office 365 のネットワーク接続性の原則](office-365-network-connectivity-principles.md)については、Office 365 エンドポイントのカテゴリを取得して安全に Office 365 のトラフィックを管理し、最高のパフォーマンスを取得するための接続の原理を理解するのにを参照してください。 
  
![Office 365 を使用する場合に、異なる 3 種類のネットワーク エンドポイントを示しています](media/6582bcfa-11ba-4ac2-9b69-14bef0437670.png)
  
### <a name="i-cant-or-dont-want-to-use-any-third-party-service"></a>または任意のサードパーティのサービスを使用したくないできません。
<a name="bkmk_thirdparty"> </a>

Office 365 は、一連のサービスをインターネット経由で機能するように構築、使用可能な多くの標準的なインターネット サービスに基づく信頼性と可用性の約束です。などの DNS、CRL、および Cdn などの標準のインターネット サービスは、最近のほとんどのインターネット サービスを使用して到達できる必要があると同様に、Office 365 を使用するのには到達可能でなければなりません。
  
これらの基本的なインターネット サービスの機能を統合するためにのみ使用されるサードパーティ製のサービスがあります。など、マイクロソフトのチーム内での Giphy.com を使用してにより、シームレスにチーム内での Gif が含まれます。同様に、YouTube、Flickr は、インターネットからの Office クライアントに、ビデオや画像をシームレスに統合するために使用するサードパーティのサービスです。これらが統合に必要なときに、サービスのコア機能は、エンドポイントがアクセス可能でない場合で機能しますが、Office 365 エンドポイントの資料では省略可能としてマークしています。
  
Office 365 を使用しようとするいるし、サードパーティのサービスにアクセスできない検索が[必須であるか、またはこの資料では省略可能にマークされているすべての Fqdn はプロキシとファイアウォールを通過できる](urls-and-ip-address-ranges.md)ことを確認します。
  
### <a name="i-cant-or-dont-want-to-use-any-secondary-services"></a>または、セカンダリ ・ サービスを使用したくないできません。
<a name="bkmk_secondary"> </a>

セカンダリ ・ サービスは、Office 365 の管理には相当しないマイクロソフトのサービスです。これらは、ネットワーク エッジ、Azure メディア サービスでは、Azure コンテンツ配信ネットワークのようなものです。これらは Office 365 を使用するすべての必須であり、到達可能である必要があります。
  
Office 365 を使用しようとするいるし、サードパーティのサービスにアクセスできない検索が[必須であるか、またはこの資料では省略可能にマークされているすべての Fqdn はプロキシとファイアウォールを通過できる](urls-and-ip-address-ranges.md)ことを確認します。
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>マイクロソフトのコンシューマー サービスへのアクセスをブロックする方法は?
<a name="bkmk_consumer"> </a>

自己の責任において、消費者サービスへのアクセス制限を行う必要があります、コンシューマー サービスをブロックする唯一確実な方法は、 *login.live.com* FQDN へのアクセスを制限します。この FQDN は、MSDN、TechNet、およびその他のユーザーなどの非消費者サービスなどのサービスの広範なセットで使用されます。この FQDN へのアクセスを制限するもこれらのサービスに関連付けられているネットワークの要求のルールの例外を含める必要がある可能性があります。
  
Exfiltrate については、Office 365 テナントまたはその他のサービスを使用するネットワーク上の他のユーザーの Microsoft コンシューマー サービスだけにアクセスをブロックしない機能しないように注意してください。
  
## <a name="related-topics"></a>関連項目

[Office 365 IP アドレスと URL の Web サービス ](office-365-ip-web-service.md)

[Microsoft Azure データ センターの IP 範囲](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft パブリック IP スペース](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Microsoft Intune のネットワーク インフラストラクチャの要件](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[電源の BI および ExpressRoute](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Office 365 の URL と IP アドレスの範囲](urls-and-ip-address-ranges.md)
  
[Office 365 向け ExpressRoute の管理](managing-expressroute-for-connectivity.md)
  
[Office 365 ネットワーク接続の原則](office-365-network-connectivity-principles.md)