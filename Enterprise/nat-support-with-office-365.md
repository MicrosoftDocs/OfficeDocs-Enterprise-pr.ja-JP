---
title: Office 365 の NAT サポート
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: '概要: ネットワーク アドレス変換 (NAT) を使用して、組織内で IP アドレスごとに使用できるクライアントの正しい数を見積もる方法の詳細について説明します。'
ms.openlocfilehash: 04aec45b7d6c68b3e32d4ee384c9927896849bab
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998542"
---
# <a name="nat-support-with-office-365"></a>Office 365 の NAT サポート

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

ガイダンスでは以前、Office 365 に接続するために IP アドレスごとに使用する必要がある Exchange クライアントの最大数は、ネットワーク ポート 1 つあたり約 2,000 と推奨していました。
  
## <a name="why-use-nat"></a>NAT を使用する理由は何ですか。

NAT の使用により、企業ネットワークの何千人ものユーザーが、少数のパブリック ルーティング可能な IP アドレスを「共有」することができます。
  
Most corporate networks use private (RFC1918) IP address space. Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.
  
To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services. These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses. Each outbound connection from an internal device translates to a different source TCP port on the public IP address. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>Office 365 に対して多数の接続を同時に開く必要があるのはなぜですか。

Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.). Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted. Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used. In this scenario, the maximum number of ports could be less than 64,000. Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Office 365 で単一のパブリック IP アドレスにサポートされるデバイスの最大数の計算

To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client. Also, a peak factor should be used for the port usage (minimum 4). 
  
 **IP アドレスごとにサポートされるデバイスの数を計算するには、次の式を使用します。**
  
単一のパブリック IP アドレスにサポートされるデバイスの最大数 = (64,000 - 制限されたポート) / (ピーク ポート消費量 + ピーク係数)
  
 **たとえば、次のような条件だとします。**
  
- **制限されたポート:** オペレーティング システムで 4,000

- **ピーク ポート消費量:** デバイスあたり 6

- **ピーク係数:** 4

このような条件の場合、単一のパブリック IP アドレスにサポートされるデバイスの最大数 = (64,000 - 4,000) / (6 + 4) = 6,000 
  
With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2. You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.
  
単一のパブリック IP アドレスでより多くのデバイスをサポートする場合、サポートできるデバイスの最大数を説明した手順に従って査定します。
  
Monitor network traffic to determine peak port consumption per client. You should collect this data:
  
- 複数の場所から収集する
    
- 複数のデバイスから収集する
    
- 複数回にわたって収集する
    
上記の計算式を使い、クライアントの環境でサポート可能な IP アドレスあたりの最大ユーザー数を計算します。
  
There are various methods for distributing client load across additional public IP addresses. Strategies available depend on the capabilities of the corporate gateway solution. The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway. Another alternative that many gateway devices offer is the ability to use a pool of IP addresses. The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.
  
## <a name="see-also"></a>関連項目

[Office 365 エンドポイントの管理](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 エンドポイントの FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
