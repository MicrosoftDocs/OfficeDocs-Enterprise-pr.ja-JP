---
title: Office 365 のビデオ ネットワークのよく寄せられる質問
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/13/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 2bed67a1-4052-49ff-a4ce-b7e6530eb98e
description: Office 365 のビデオのリポジトリとサービスをストリーミングを使用する保存して、組織内のビデオのストリーミング簡単です。Office 365 ビデオに関する情報が多いネットワークこのよく寄せられる質問は、帯域幅の計画、暗号化、およびサービスがコンテンツ配信ネットワーク (Cdn) を活用する方法を最も一般的な質問に回答するよう設計されています。
ms.openlocfilehash: bea9838277b5752e4c9905162c0e8525e8aded04
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541583"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a><span data-ttu-id="a2d36-104">Office 365 のビデオ ネットワークのよく寄せられる質問</span><span class="sxs-lookup"><span data-stu-id="a2d36-104">Office 365 Video networking Frequently Asked Questions</span></span>

<span data-ttu-id="a2d36-p102">Office 365 のビデオのリポジトリとサービスをストリーミングを使用する保存して、組織内のビデオのストリーミング簡単です。多くの便利な[Office 365 のビデオについての情報](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)です。ネットワークこのよく寄せられる質問は、帯域幅の計画、暗号化、およびサービスが[コンテンツ配信ネットワーク (Cdn)](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)を活用する方法を最も一般的な質問に回答するよう設計されています。</span><span class="sxs-lookup"><span data-stu-id="a2d36-p102">The Office 365 Video repository and streaming services make storing and streaming videos within your organization simple. There's a lot of great [information about Office 365 Video](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50); this networking FAQ is designed to answer the most common questions around bandwidth planning, encryption, and how the service leverages [content delivery networks (CDNs)](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).</span></span>
  
<span data-ttu-id="a2d36-107">既にビデオがアップロードされたときの動作の理解や再生、このビデオを見てについてまとめてみました、[ビデオ ファイルを Office 365 のビデオをアップロードするときに動作](https://www.youtube.com/watch?v=HXSZ0jYBKlM)します。</span><span class="sxs-lookup"><span data-stu-id="a2d36-107">If you don't already have a thorough understanding of what happens when a video is uploaded or played back, have a look at this video we put together, [What happens to a video file when uploaded to Office 365 Video](https://www.youtube.com/watch?v=HXSZ0jYBKlM).</span></span>
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a><span data-ttu-id="a2d36-108">Office 365 のビデオ帯域幅の要件は?</span><span class="sxs-lookup"><span data-stu-id="a2d36-108">What are the Office 365 Video bandwidth requirements?</span></span>

<span data-ttu-id="a2d36-p103">さまざまな[ビデオ形式がサポートされている](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817)Office 365 にアップロードできます。各ビデオ ファイルは、再生するためのいくつかのさまざまなビデオ品質の標準の形式にエンコードされます。Office 365 のビデオでは、アダプティブ ・ ビットレートが利用可能なネットワーク帯域幅とビデオ プレーヤーのサイズに基づいて、高品質なビデオ再生を選択するのにはストリーミングを使用します。これを行うには、プレーヤーは最初に最下位の再生品質を要求します。サービスは、ビデオ プレーヤーに 2 秒のビデオのセグメントの送信を開始します。プレイヤーは、各セグメントの配信速度に基づいて上位または下位の再生品質を要求します。</span><span class="sxs-lookup"><span data-stu-id="a2d36-p103">There are a numerous [supported video formats](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817) that can be uploaded to Office 365. Each video file is then encoded to a standard format with several different video qualities for playback. Office 365 Video uses adaptive bitrate streaming to select the best video playback quality based on the available network bandwidth and size of the video player. To do this, the player initially requests the lowest playback quality. The service then begins sending 2-second video segments to the video player. The player can then request higher or lower playback quality based on how quickly each segment is delivered.</span></span>
  
<span data-ttu-id="a2d36-p104">アダプティブ ・ ビットレートのストリームはすべてバック グラウンドでビデオが最小限の中断またはバッファーの再生中にします。ビデオの再生中は、ビデオ プレーヤーは、特定のビデオの再生品質を選択するのには、自動再生の品質を手動でオーバーライドするビューアーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a2d36-p104">The adaptive bitrate streaming does all this in the background while the video plays with the least amount of disruption or buffering. During video playback, the video player allows the viewer to manually override the automatic playback quality, to select a specific video playback quality.</span></span>
  
<span data-ttu-id="a2d36-p105">ここでは、各ビデオの再生品質のネットワーク要件をまとめたクイック テーブルです。1 人のビデオを再生するために必要な最小の帯域幅は、802 Kbps です。</span><span class="sxs-lookup"><span data-stu-id="a2d36-p105">Here's a quick table that outlines the network requirements for each of the video playback qualities. The minimum bandwidth per person needed to play a video is 802Kbps.</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="a2d36-119">**再生品質**</span><span class="sxs-lookup"><span data-stu-id="a2d36-119">**Playback Quality**</span></span> <br/> |<span data-ttu-id="a2d36-120">**ネットワーク速度**</span><span class="sxs-lookup"><span data-stu-id="a2d36-120">**Network Speed**</span></span> <br/> |
|<span data-ttu-id="a2d36-121">288 p</span><span class="sxs-lookup"><span data-stu-id="a2d36-121">288p</span></span>  <br/> |<span data-ttu-id="a2d36-122">802 kbps</span><span class="sxs-lookup"><span data-stu-id="a2d36-122">802Kbps</span></span>  <br/> |
|<span data-ttu-id="a2d36-123">360 p</span><span class="sxs-lookup"><span data-stu-id="a2d36-123">360p</span></span>  <br/> |<span data-ttu-id="a2d36-124">1.2 Mbps</span><span class="sxs-lookup"><span data-stu-id="a2d36-124">1.2 Mbps</span></span>  <br/> |
|<span data-ttu-id="a2d36-125">576 p</span><span class="sxs-lookup"><span data-stu-id="a2d36-125">576p</span></span>  <br/> |<span data-ttu-id="a2d36-126">2.5 Mbps</span><span class="sxs-lookup"><span data-stu-id="a2d36-126">2.5 Mbps</span></span>  <br/> |
|<span data-ttu-id="a2d36-127">720 p</span><span class="sxs-lookup"><span data-stu-id="a2d36-127">720p</span></span>  <br/> |<span data-ttu-id="a2d36-128">3.8 Mbps</span><span class="sxs-lookup"><span data-stu-id="a2d36-128">3.8 Mbps</span></span>  <br/> |

<span data-ttu-id="a2d36-129">([先頭に戻る](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="a2d36-129">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="how-do-cdns-help-video-playback"></a><span data-ttu-id="a2d36-130">Cdn がビデオの再生に役立つでしょうか。</span><span class="sxs-lookup"><span data-stu-id="a2d36-130">How do CDNs help video playback?</span></span>

<span data-ttu-id="a2d36-p106">同じ地理的な場所にある同じ組織で複数の人には、同じビデオをストリーミングは、Cdn は、その地域に近い場所にこれらのビデオのコピーが格納されます。ビデオと格納されている、または最も近い場所にあるキャッシュされた各ユーザー、離れた場所をさらにではなくそれらに最も近い場所からのビデオにストリームします。Office 365 のビデオは、どのようなキャッシュで Azure Cdn、および時間を管理するために、Azure のメディア サービスを使用します。Azure のメディア サービスは、ビデオの断片と、数日の目録をキャッシュするのには、 [Azure CDN の場所](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/)のいずれかを使用できます。組織内のユーザーがキャッシュされているビデオを見ながら引き続きキャッシュのままになります。数日、ビデオのビデオが最終的にはない 1 つのアクセスの場合は、ドロップがキャッシュから削除されます。次回のビデオを見るときにもう一度キャッシュに最も近い CDN の場所です。</span><span class="sxs-lookup"><span data-stu-id="a2d36-p106">If several people from the same organization within the same geographic location are streaming the same video(s), CDNs will store a copy of these videos in a location closer to that geographic region. With the video stored, or cached at the closest location, each person streams the video from the location closest to them instead of a location further away. Office 365 Video uses Azure Media Services to manage what is cached in the Azure CDNs, and for how long. Azure Media Services can use any of the [Azure CDN locations](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/) to cache video fragments and manifests for a few days. If people in your organization continue to watch the cached videos they'll stay in the cache. If no one accesses the video for several days, the video will eventually drop be dropped from the cache. The next time someone attempts to watch the video it's once again cached at the nearest CDN location.</span></span>
  
<span data-ttu-id="a2d36-p107">すべてのコンテンツの中にビデオを視聴しようとする人が、近くにある CDN のメリットが近づき、ビデオからホップ離れたところ、以下のほとんどの場合にキャッシュされます。これがビデオの再生速度を向上します。ただし、ビデオを再生するネットワークの要件は変更されません。</span><span class="sxs-lookup"><span data-stu-id="a2d36-p107">Everyone who attempts to watch the video while the content is cached at a nearby CDN benefits from the video being closer, and in most cases less hops, away. This improves video playback speed; however, it doesn't change the network requirement to play the video.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a2d36-140">容量制限に達したことを 3 日に達した前にビデオを削除することがありますなど、いくつかの状況があります。</span><span class="sxs-lookup"><span data-stu-id="a2d36-140">There are some circumstances, such as our capacity limit being reached, where the video may be removed before the three days has been reached.</span></span>
  
<span data-ttu-id="a2d36-141">([先頭に戻る](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="a2d36-141">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a><span data-ttu-id="a2d36-142">ローカル再生が高速にビデオをキャッシュできますか。</span><span class="sxs-lookup"><span data-stu-id="a2d36-142">Can I cache the videos locally for faster playback?</span></span>

<span data-ttu-id="a2d36-p108">うん。Office 365 もできないローカルの CDN やキャッシュ プロキシを使用して高速アクセスのためのローカル ネットワーク内にビデオ、またはその他の Office 365 のコンテンツを表示します。ネットワーク上のローカル ・ キャッシュ ・ ソリューションを実装するためにいくつかの方法がある、最も一般的な方法は、コンテンツをローカルにキャッシュするプロキシ ソリューションを使用します。プロキシまたはプライベートの CDN は、ビデオの断片とマニフェストをキャッシュは、1 回プロキシまたはプライベートの CDN を経由してルーティングするこれらのファイルの将来の要求がローカル キャッシュから取得し、インターネット上の場所からプルしていません。このようなソリューションの計画時に、ネットワーク帯域幅、容量、およびビデオの再生の同時実行を検討してください。</span><span class="sxs-lookup"><span data-stu-id="a2d36-p108">Yes. Office 365 won't prevent you from using a local CDN or a caching proxy to bring video or other Office 365 content into your local network for faster access. There are several ways to implement a local caching solution on your network, the most common method is to use a proxy solution that caches content locally. Once a proxy or private CDN has cached the video fragments and manifests, future requests for those files that route through the proxy or private CDN are pulled from the local cache and not pulled from an internet location. Consider network bandwidth, capacity, and video playback concurrency during the planning of a solution like this.</span></span>
  
<span data-ttu-id="a2d36-148">([先頭に戻る](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="a2d36-148">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="how-videos-are-encrypted-and-secured"></a><span data-ttu-id="a2d36-149">どのビデオが暗号化され、セキュリティで保護しますか。</span><span class="sxs-lookup"><span data-stu-id="a2d36-149">How videos are encrypted and secured?</span></span>

<span data-ttu-id="a2d36-p109">Office 365 のビデオでは、データの安全性とプライバシーを維持することがいかに重要である認識しています。[[Office 365 の信頼センター](https://products.office.com/business/office-365-trust-center-cloud-computing-security)では、コンテンツのセキュリティとプライバシーへの取り組みについて説明します。ビデオの再生速度は、環境は良好ですただし、速度と引き換えにプライバシー、セキュリティを侵害しません。速度、セキュリティ、プライバシー対応する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a2d36-p109">Office 365 Video knows how important it is to keep your data secure and private. [The Office 365 Trust Center](https://products.office.com/business/office-365-trust-center-cloud-computing-security) describes our commitment to the privacy and security of your content. With video playback, speed is important for a good experience; however, we don't compromise your security or privacy in exchange for speed. Here's how we accommodate speed, security and privacy.</span></span>
  
<span data-ttu-id="a2d36-p110">または他の組織では、新しいビデオをアップロード、そのビデオは、トランス コード、aes-128 暗号化で暗号化され、Azure のメディア サービスに格納されているです。これは、ビデオは両方で転送中に暗号化を意味します。</span><span class="sxs-lookup"><span data-stu-id="a2d36-p110">When you or someone in your organization uploads a new video, that video is transcoded, encrypted with AES-128 encryption, and stored in Azure Media Services. This means the videos are encrypted both in transit and at rest.</span></span>
  
<span data-ttu-id="a2d36-156">組織のだれかが新しいビデオを見るしようとすると、これらの手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a2d36-156">When someone in your organization attempts to watch a new video, they follow these steps:</span></span>
  
1. <span data-ttu-id="a2d36-157">SharePoint のオンライン ビデオを表示するアクセス許可があるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="a2d36-157">Ask SharePoint Online if they have permission to view the video.</span></span>

2. <span data-ttu-id="a2d36-158">SharePoint Online は、ユーザーがビデオを見ることができるかどうかを決定するのにファイルのアクセス許可を使用します。</span><span class="sxs-lookup"><span data-stu-id="a2d36-158">SharePoint Online uses the file permissions to determine if the person can watch the video.</span></span>

3. <span data-ttu-id="a2d36-159">許可されている場合は、SharePoint Online トークンを取得、ビデオ プレーヤーにするための Azure からです。</span><span class="sxs-lookup"><span data-stu-id="a2d36-159">If they're allowed, SharePoint Online retrieves a token from Azure to give to the video player.</span></span>

4. <span data-ttu-id="a2d36-160">ビデオ プレーヤーは、トークンを使用して、Azure から復号化キーを要求します。</span><span class="sxs-lookup"><span data-stu-id="a2d36-160">The video player then uses the token to request the decryption key from Azure.</span></span>

5. <span data-ttu-id="a2d36-161">手で復号化キー、ビデオ プレーヤーは、ビデオをストリーム配信することです。</span><span class="sxs-lookup"><span data-stu-id="a2d36-161">With the decryption key in hand, the video player is able to stream the video.</span></span>

![O365 ビデオの再生](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
<span data-ttu-id="a2d36-163">([先頭に戻る](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="a2d36-163">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a><span data-ttu-id="a2d36-164">Office 365 のビデオを再生するための要件を挙げてください。</span><span class="sxs-lookup"><span data-stu-id="a2d36-164">What are the requirements to playback Office 365 Video?</span></span>

<span data-ttu-id="a2d36-p111">Office 365 のビデオには、オペレーティング システムがサポートされているし、web ブラウザーでは、SharePoint Online の要件では、 [Office 365 のシステム要件](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45)と同じです。によって、どのオペレーティング システムと web ブラウザーの設定がある場合は、ビデオ プレーヤーの特定のニーズを決定します。[ビデオ再生の要件](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)の詳細については、ここで。</span><span class="sxs-lookup"><span data-stu-id="a2d36-p111">Office 365 Video supported operating systems and web browsers are the same as the SharePoint Online requirements in [Office 365 system requirements](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45). Depending on which operating system and web browser configuration you have will determine the specific needs of the video player. Here's more information on [video playback requirements](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6).</span></span>
  
<span data-ttu-id="a2d36-168">([先頭に戻る](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="a2d36-168">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a><span data-ttu-id="a2d36-169">Office 365 ビデオには、開始する必要があります場所が表示されることはできませんか。</span><span class="sxs-lookup"><span data-stu-id="a2d36-169">I can't get Office 365 video to work, where should I start?</span></span>

<span data-ttu-id="a2d36-p112">Office 365 のビデオへの接続のトラブルシューティングには、ネットワーク、ISP(s)、および Office 365 の構成をトラブルシューティングする必要があります。開始する最初の場所は、サービス正常性ダッシュ ボードです。これは、により、Office 365 のビデオの問題が発生してかが示されます。すべてすばらしいが、いくつかに役立つその他のリソースです。</span><span class="sxs-lookup"><span data-stu-id="a2d36-p112">Troubleshooting connectivity to Office 365 Video involves troubleshooting your network, your ISP(s), and your configuration of Office 365. The first place to start is the service health dashboard. This will tell you of Office 365 Video is having a problem or not. If everything looks great there, here's some additional resources to help you.</span></span>
  
- <span data-ttu-id="a2d36-174">[Office 365 のビデオに必要なネットワークのエンドポイント](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)に接続できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a2d36-174">Make sure you can connect to the [network endpoints required for Office 365 Video](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).</span></span>

- <span data-ttu-id="a2d36-175">マイクロソフトの[Office 365 のネットワーク トラブルシューティング ガイド](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)を使用して、ネットワーク接続を確認してください。</span><span class="sxs-lookup"><span data-stu-id="a2d36-175">Check your network connectivity using our [Office 365 network troubleshooting guide](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).</span></span>

- <span data-ttu-id="a2d36-176">[低速のネットワーク上の Office 365 を使用するためのベスト プラクティス](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2d36-176">See our [best practices for using Office 365 on a slow network](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166).</span></span>

- <span data-ttu-id="a2d36-177">[Office 365 のビデオの構成についてのヘルプ](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)を検索します。</span><span class="sxs-lookup"><span data-stu-id="a2d36-177">Find [help about Office 365 Video configuration](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).</span></span>

<span data-ttu-id="a2d36-178">([先頭に戻る](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="a2d36-178">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="office-365-video-resources"></a><span data-ttu-id="a2d36-179">Office 365 のビデオ リソース</span><span class="sxs-lookup"><span data-stu-id="a2d36-179">Office 365 Video resources</span></span>

<span data-ttu-id="a2d36-p113">トピックを評価し、ご連絡ください、質問の答えは場合、または回答が探している場合にコメントを記入します。正常に展開し、Office 365 のビデオを使用するため、他のリソースのいくつかを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="a2d36-p113">Rate the topic and leave a comment to let us know if we answered your questions or if you're still looking for answers. Here's a few of our other resources to help you successfully deploy and use Office 365 Video:</span></span>
  
<span data-ttu-id="a2d36-182">[Office 365 のビデオの構成に関するヘルプを検索](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)します。</span><span class="sxs-lookup"><span data-stu-id="a2d36-182">[Find help about Office 365 Video configuration](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).</span></span>
  
[<span data-ttu-id="a2d36-183">Office 365 のビデオに対応します。</span><span class="sxs-lookup"><span data-stu-id="a2d36-183">Meet Office 365 Video</span></span>](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)
  
[<span data-ttu-id="a2d36-184">作成し、Office 365 のビデオでは、チャンネルの管理</span><span class="sxs-lookup"><span data-stu-id="a2d36-184">Create and manage a channel in Office 365 Video</span></span>](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  
[<span data-ttu-id="a2d36-185">Office 365 のビデオのポータルを管理します。</span><span class="sxs-lookup"><span data-stu-id="a2d36-185">Manage your Office 365 Video portal</span></span>](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da)
  
[<span data-ttu-id="a2d36-186">Office 365 のビデオで動作しているビデオの形式</span><span class="sxs-lookup"><span data-stu-id="a2d36-186">Video formats that work in Office 365 Video</span></span>](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
<span data-ttu-id="a2d36-187">([先頭に戻る](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="a2d36-187">([Back to top](office-365-video-networking-faq.md))</span></span>
  
<span data-ttu-id="a2d36-188">戻るを使用することができます短いリンクを以下に示します。[https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)</span><span class="sxs-lookup"><span data-stu-id="a2d36-188">Here's a short link you can use to come back: [https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)</span></span>
