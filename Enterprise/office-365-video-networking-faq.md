---
title: Office 365 のビデオネットワークについてよく寄せられる質問
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/14/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 2bed67a1-4052-49ff-a4ce-b7e6530eb98e
ms.custom:
- Adm_O365
- seo-marvel-apr2020
description: 帯域幅の計画、暗号化、およびサービスがコンテンツ配信ネットワーク (CDNs) をどのように活用するか & に関してよく寄せられる質問の回答を参照してください。
ms.openlocfilehash: 938876075bf849a94f52de9285e83cd442fe2006
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605479"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a><span data-ttu-id="842e8-103">Office 365 のビデオネットワークについてよく寄せられる質問</span><span class="sxs-lookup"><span data-stu-id="842e8-103">Office 365 Video networking Frequently Asked Questions</span></span>

<span data-ttu-id="842e8-104">Office 365 のビデオリポジトリおよびストリーミングサービスを使用すると、組織内のビデオを簡単に保存およびストリーミングすることができます。</span><span class="sxs-lookup"><span data-stu-id="842e8-104">The Office 365 Video repository and streaming services make storing and streaming videos within your organization simple.</span></span> <span data-ttu-id="842e8-105">[Office 365 ビデオについて](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)多くの重要な情報があります。このネットワーク FAQ は、帯域幅の計画、暗号化、およびサービスが[コンテンツ配信ネットワーク](content-delivery-networks.md)(cdns) を活用する方法に関してよく寄せられる質問に回答するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="842e8-105">There's a lot of great [information about Office 365 Video](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50); this networking FAQ is designed to answer the most common questions around bandwidth planning, encryption, and how the service leverages [Content Delivery Networks](content-delivery-networks.md) (CDNs).</span></span>
  
<span data-ttu-id="842e8-106">ビデオをアップロードまたは再生したときに何が起こるかを十分に理解していない場合は、このビデオをまとめたものとして、 [Office 365 のビデオにアップロードしたときにビデオファイル](https://www.youtube.com/watch?v=HXSZ0jYBKlM)がどうなるかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="842e8-106">If you don't already have a thorough understanding of what happens when a video is uploaded or played back, have a look at this video we put together, [What happens to a video file when uploaded to Office 365 Video](https://www.youtube.com/watch?v=HXSZ0jYBKlM).</span></span>
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a><span data-ttu-id="842e8-107">Office 365 のビデオ帯域幅の要件を教えてください。</span><span class="sxs-lookup"><span data-stu-id="842e8-107">What are the Office 365 Video bandwidth requirements?</span></span>

<span data-ttu-id="842e8-108">Office 365 にアップロードできる[サポートされているビデオ形式](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817)は多数あります。</span><span class="sxs-lookup"><span data-stu-id="842e8-108">There are a numerous [supported video formats](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817) that can be uploaded to Office 365.</span></span> <span data-ttu-id="842e8-109">各ビデオファイルは、再生にさまざまなビデオ品質を持つ標準形式にエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="842e8-109">Each video file is then encoded to a standard format with several different video qualities for playback.</span></span> <span data-ttu-id="842e8-110">Office 365 Video は、アダプティブビットレートのストリーミングを使用して、使用可能なネットワーク帯域幅とビデオプレーヤーのサイズに基づいて、最適なビデオ再生品質を選択します。</span><span class="sxs-lookup"><span data-stu-id="842e8-110">Office 365 Video uses adaptive bitrate streaming to select the best video playback quality based on the available network bandwidth and size of the video player.</span></span> <span data-ttu-id="842e8-111">これを行うために、player は最初に最小の再生品質を要求します。</span><span class="sxs-lookup"><span data-stu-id="842e8-111">To do this, the player initially requests the lowest playback quality.</span></span> <span data-ttu-id="842e8-112">その後、サービスは、2秒間のビデオセグメントをビデオプレーヤーに送信します。</span><span class="sxs-lookup"><span data-stu-id="842e8-112">The service then begins sending 2-second video segments to the video player.</span></span> <span data-ttu-id="842e8-113">プレーヤーは、各セグメントが配信される速度に基づいて、より高いまたは低い再生品質を要求できます。</span><span class="sxs-lookup"><span data-stu-id="842e8-113">The player can then request higher or lower playback quality based on how quickly each segment is delivered.</span></span>
  
<span data-ttu-id="842e8-114">アダプティブビットレートストリーミングでは、ビデオの再生が最小限に抑えられている間、バックグラウンドでこれらすべてが実行されます。</span><span class="sxs-lookup"><span data-stu-id="842e8-114">The adaptive bitrate streaming does all this in the background while the video plays with the least amount of disruption or buffering.</span></span> <span data-ttu-id="842e8-115">ビデオの再生中に、ビデオプレーヤーでは、視聴者が自動再生の品質を手動で上書きして、特定のビデオ再生品質を選択することができます。</span><span class="sxs-lookup"><span data-stu-id="842e8-115">During video playback, the video player allows the viewer to manually override the automatic playback quality, to select a specific video playback quality.</span></span>
  
<span data-ttu-id="842e8-116">ビデオ再生の各品質のネットワーク要件の概要を示すクイックテーブルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="842e8-116">Here's a quick table that outlines the network requirements for each of the video playback qualities.</span></span> <span data-ttu-id="842e8-117">ビデオの再生に必要なユーザーあたりの最小帯域幅は802Kbps です。</span><span class="sxs-lookup"><span data-stu-id="842e8-117">The minimum bandwidth per person needed to play a video is 802Kbps.</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="842e8-118">**再生品質**</span><span class="sxs-lookup"><span data-stu-id="842e8-118">**Playback Quality**</span></span> <br/> |<span data-ttu-id="842e8-119">**ネットワークの速度**</span><span class="sxs-lookup"><span data-stu-id="842e8-119">**Network Speed**</span></span> <br/> |
|<span data-ttu-id="842e8-120">288 p</span><span class="sxs-lookup"><span data-stu-id="842e8-120">288p</span></span>  <br/> |<span data-ttu-id="842e8-121">802Kbps</span><span class="sxs-lookup"><span data-stu-id="842e8-121">802Kbps</span></span>  <br/> |
|<span data-ttu-id="842e8-122">360p</span><span class="sxs-lookup"><span data-stu-id="842e8-122">360p</span></span>  <br/> |<span data-ttu-id="842e8-123">1.2 Mbps</span><span class="sxs-lookup"><span data-stu-id="842e8-123">1.2 Mbps</span></span>  <br/> |
|<span data-ttu-id="842e8-124">576p</span><span class="sxs-lookup"><span data-stu-id="842e8-124">576p</span></span>  <br/> |<span data-ttu-id="842e8-125">2.5 Mbps</span><span class="sxs-lookup"><span data-stu-id="842e8-125">2.5 Mbps</span></span>  <br/> |
|<span data-ttu-id="842e8-126">プログレッシブ</span><span class="sxs-lookup"><span data-stu-id="842e8-126">720p</span></span>  <br/> |<span data-ttu-id="842e8-127">3.8 Mbps</span><span class="sxs-lookup"><span data-stu-id="842e8-127">3.8 Mbps</span></span>  <br/> |

<span data-ttu-id="842e8-128">([トップに戻る](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="842e8-128">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="how-do-content-delivery-networks-cdns-help-video-playback"></a><span data-ttu-id="842e8-129">コンテンツ配信ネットワーク (CDNs) はどのようにビデオの再生をサポートしますか?</span><span class="sxs-lookup"><span data-stu-id="842e8-129">How do Content Delivery Networks (CDNs) help video playback?</span></span>

<span data-ttu-id="842e8-130">同じ地理的位置にある同じ組織の複数のユーザーが同じビデオをストリーミングしている場合、CDNs はその地域に近い場所にこれらのビデオのコピーを保存します。</span><span class="sxs-lookup"><span data-stu-id="842e8-130">If several people from the same organization within the same geographic location are streaming the same video(s), CDNs will store a copy of these videos in a location closer to that geographic region.</span></span> <span data-ttu-id="842e8-131">ビデオが保存されているか、最も近い場所にキャッシュされていると、各ユーザーは、その場所から離れた場所ではなく、最も近い場所からビデオをストリームします。</span><span class="sxs-lookup"><span data-stu-id="842e8-131">With the video stored, or cached at the closest location, each person streams the video from the location closest to them instead of a location further away.</span></span> <span data-ttu-id="842e8-132">Office 365 Video は、azure メディアサービスを使用して Azure CDNs にキャッシュされているものと、期間を管理します。</span><span class="sxs-lookup"><span data-stu-id="842e8-132">Office 365 Video uses Azure Media Services to manage what is cached in the Azure CDNs, and for how long.</span></span> <span data-ttu-id="842e8-133">Azure Media Services では、任意の[AZURE CDN の場所](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/)を使用して、ビデオフラグメントとマニフェストを数日間キャッシュできます。</span><span class="sxs-lookup"><span data-stu-id="842e8-133">Azure Media Services can use any of the [Azure CDN locations](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/) to cache video fragments and manifests for a few days.</span></span> <span data-ttu-id="842e8-134">組織内のユーザーがキャッシュされたビデオを引き続き視聴する場合は、キャッシュに残ります。</span><span class="sxs-lookup"><span data-stu-id="842e8-134">If people in your organization continue to watch the cached videos they'll stay in the cache.</span></span> <span data-ttu-id="842e8-135">何度もビデオにアクセスできない場合、ビデオは最終的にキャッシュから削除されます。</span><span class="sxs-lookup"><span data-stu-id="842e8-135">If no one accesses the video for several days, the video will eventually drop be dropped from the cache.</span></span> <span data-ttu-id="842e8-136">次回、ユーザーがビデオを視聴しようとしたときに、それが最も近い CDN の場所で再びキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="842e8-136">The next time someone attempts to watch the video it's once again cached at the nearest CDN location.</span></span>
  
<span data-ttu-id="842e8-137">ビデオを視聴しようとしているすべてのユーザーは、ビデオの近くにある CDN の利点で、ビデオが近い場所にあることを示しています。</span><span class="sxs-lookup"><span data-stu-id="842e8-137">Everyone who attempts to watch the video while the content is cached at a nearby CDN benefits from the video being closer, and in most cases less hops, away.</span></span> <span data-ttu-id="842e8-138">これにより、ビデオの再生速度が向上します。ただし、ビデオを再生するためにネットワーク要件が変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="842e8-138">This improves video playback speed; however, it doesn't change the network requirement to play the video.</span></span>
  
> [!NOTE]
> <span data-ttu-id="842e8-139">容量の制限に達しているなど、状況によっては、3日が経過する前にビデオが削除されることがあります。</span><span class="sxs-lookup"><span data-stu-id="842e8-139">There are some circumstances, such as our capacity limit being reached, where the video may be removed before the three days has been reached.</span></span>
  
<span data-ttu-id="842e8-140">([トップに戻る](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="842e8-140">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a><span data-ttu-id="842e8-141">再生を高速化するためにビデオをローカルにキャッシュすることはできますか?</span><span class="sxs-lookup"><span data-stu-id="842e8-141">Can I cache the videos locally for faster playback?</span></span>

<span data-ttu-id="842e8-142">はい。</span><span class="sxs-lookup"><span data-stu-id="842e8-142">Yes.</span></span> <span data-ttu-id="842e8-143">Office 365 では、ローカル CDN またはキャッシュプロキシを使用して、アクセスを高速化するためにビデオやその他の Office 365 コンテンツをローカルネットワークに格納することはできません。</span><span class="sxs-lookup"><span data-stu-id="842e8-143">Office 365 won't prevent you from using a local CDN or a caching proxy to bring video or other Office 365 content into your local network for faster access.</span></span> <span data-ttu-id="842e8-144">ネットワークにローカルキャッシュソリューションを実装する方法はいくつかありますが、最も一般的な方法は、コンテンツをローカルにキャッシュするプロキシソリューションを使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="842e8-144">There are several ways to implement a local caching solution on your network, the most common method is to use a proxy solution that caches content locally.</span></span> <span data-ttu-id="842e8-145">プロキシまたはプライベート CDN によってビデオフラグメントとマニフェストがキャッシュされた後、プロキシまたはプライベート CDN を経由してルーティングされるこれらのファイルへの要求は、インターネット上の場所から引き出されずにローカルキャッシュから取得されます。</span><span class="sxs-lookup"><span data-stu-id="842e8-145">Once a proxy or private CDN has cached the video fragments and manifests, future requests for those files that route through the proxy or private CDN are pulled from the local cache and not pulled from an internet location.</span></span> <span data-ttu-id="842e8-146">このようなソリューションを計画する際には、ネットワーク帯域幅、容量、ビデオ再生の同時実行を考慮します。</span><span class="sxs-lookup"><span data-stu-id="842e8-146">Consider network bandwidth, capacity, and video playback concurrency during the planning of a solution like this.</span></span>
  
<span data-ttu-id="842e8-147">([トップに戻る](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="842e8-147">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="how-videos-are-encrypted-and-secured"></a><span data-ttu-id="842e8-148">ビデオを暗号化してセキュリティで保護する方法</span><span class="sxs-lookup"><span data-stu-id="842e8-148">How videos are encrypted and secured?</span></span>

<span data-ttu-id="842e8-149">Office 365 Video は、データのセキュリティを確保し、プライベートにすることが重要であることを認識しています。</span><span class="sxs-lookup"><span data-stu-id="842e8-149">Office 365 Video knows how important it is to keep your data secure and private.</span></span> <span data-ttu-id="842e8-150">[Microsoft Trust Center](https://products.office.com/business/office-365-trust-center-welcome)は、コンテンツのプライバシーとセキュリティに対するコミットメントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="842e8-150">[Microsoft Trust Center](https://products.office.com/business/office-365-trust-center-welcome) describes our commitment to the privacy and security of your content.</span></span> <span data-ttu-id="842e8-151">ビデオの再生では、パフォーマンスを向上させるには速度が重要です。しかし、exchange のセキュリティやプライバシーをスピードアップすることはありません。</span><span class="sxs-lookup"><span data-stu-id="842e8-151">With video playback, speed is important for a good experience; however, we don't compromise your security or privacy in exchange for speed.</span></span> <span data-ttu-id="842e8-152">スピード、セキュリティ、プライバシーに対応する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="842e8-152">Here's how we accommodate speed, security and privacy.</span></span>
  
<span data-ttu-id="842e8-153">組織内のユーザーが新しいビデオをアップロードすると、そのビデオはトランスコードされ、AES-128 暗号化によって暗号化され、Azure Media Services に格納されます。</span><span class="sxs-lookup"><span data-stu-id="842e8-153">When you or someone in your organization uploads a new video, that video is transcoded, encrypted with AES-128 encryption, and stored in Azure Media Services.</span></span> <span data-ttu-id="842e8-154">これは、送信中と保存中の両方のビデオが暗号化されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="842e8-154">This means the videos are encrypted both in transit and at rest.</span></span>
  
<span data-ttu-id="842e8-155">組織内の誰かが新しいビデオを視聴しようとすると、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="842e8-155">When someone in your organization attempts to watch a new video, they follow these steps:</span></span>
  
1. <span data-ttu-id="842e8-156">ビデオを表示する権限がある場合は、SharePoint Online にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="842e8-156">Ask SharePoint Online if they have permission to view the video.</span></span>

2. <span data-ttu-id="842e8-157">SharePoint Online は、ファイルのアクセス許可を使用して、ユーザーがビデオを視聴できるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="842e8-157">SharePoint Online uses the file permissions to determine if the person can watch the video.</span></span>

3. <span data-ttu-id="842e8-158">許可されている場合、SharePoint Online は、ビデオプレーヤーに提供するために Azure からトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="842e8-158">If they're allowed, SharePoint Online retrieves a token from Azure to give to the video player.</span></span>

4. <span data-ttu-id="842e8-159">その後、ビデオプレーヤーは、トークンを使用して Azure の復号化キーを要求します。</span><span class="sxs-lookup"><span data-stu-id="842e8-159">The video player then uses the token to request the decryption key from Azure.</span></span>

5. <span data-ttu-id="842e8-160">復号キーが手元にある場合、ビデオプレーヤーはビデオをストリームできます。</span><span class="sxs-lookup"><span data-stu-id="842e8-160">With the decryption key in hand, the video player is able to stream the video.</span></span>

![O365 ビデオの再生](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
<span data-ttu-id="842e8-162">([トップに戻る](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="842e8-162">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a><span data-ttu-id="842e8-163">Office 365 ビデオを再生するための要件</span><span class="sxs-lookup"><span data-stu-id="842e8-163">What are the requirements to playback Office 365 Video?</span></span>

<span data-ttu-id="842e8-164">Office 365 のビデオサポートされているオペレーティングシステムと web ブラウザーは、 [office 365 のシステム要件](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45)である SharePoint Online の要件と同じです。</span><span class="sxs-lookup"><span data-stu-id="842e8-164">Office 365 Video supported operating systems and web browsers are the same as the SharePoint Online requirements in [Office 365 system requirements](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45).</span></span> <span data-ttu-id="842e8-165">使用しているオペレーティングシステムと web ブラウザーの構成に応じて、ビデオプレーヤーの特定のニーズが決まります。</span><span class="sxs-lookup"><span data-stu-id="842e8-165">Depending on which operating system and web browser configuration you have will determine the specific needs of the video player.</span></span> <span data-ttu-id="842e8-166">[ビデオ再生の要件](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)の詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="842e8-166">Here's more information on [video playback requirements](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6).</span></span>
  
<span data-ttu-id="842e8-167">([トップに戻る](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="842e8-167">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a><span data-ttu-id="842e8-168">Office 365 ビデオをご利用いただけません。どこから始めるべきですか?</span><span class="sxs-lookup"><span data-stu-id="842e8-168">I can't get Office 365 video to work, where should I start?</span></span>

<span data-ttu-id="842e8-169">Office 365 ビデオへの接続のトラブルシューティングでは、ネットワーク、ISP、および Office 365 の構成に関するトラブルシューティングを行います。</span><span class="sxs-lookup"><span data-stu-id="842e8-169">Troubleshooting connectivity to Office 365 Video involves troubleshooting your network, your ISP(s), and your configuration of Office 365.</span></span> <span data-ttu-id="842e8-170">最初に開始する場所は、サービス正常性ダッシュボードです。</span><span class="sxs-lookup"><span data-stu-id="842e8-170">The first place to start is the service health dashboard.</span></span> <span data-ttu-id="842e8-171">これにより、Office 365 のビデオで問題が発生しているかどうかがわかります。</span><span class="sxs-lookup"><span data-stu-id="842e8-171">This will tell you of Office 365 Video is having a problem or not.</span></span> <span data-ttu-id="842e8-172">すべてがすばらしいのであれば、次のような追加のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="842e8-172">If everything looks great there, here's some additional resources to help you.</span></span>
  
- <span data-ttu-id="842e8-173">[Office 365 のビデオに必要なネットワークエンドポイント](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)に接続できることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="842e8-173">Make sure you can connect to the [network endpoints required for Office 365 Video](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).</span></span>

- <span data-ttu-id="842e8-174">[Office 365 ネットワークトラブルシューティングガイド](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)を使用して、ネットワーク接続を確認します。</span><span class="sxs-lookup"><span data-stu-id="842e8-174">Check your network connectivity using our [Office 365 network troubleshooting guide](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).</span></span>

- <span data-ttu-id="842e8-175">[低速のネットワークで Office 365 を使用するためのベストプラクティス](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="842e8-175">See our [best practices for using Office 365 on a slow network](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166).</span></span>

- <span data-ttu-id="842e8-176">[Office 365 のビデオ構成に関するヘルプを参照して](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)ください。</span><span class="sxs-lookup"><span data-stu-id="842e8-176">[Find help about Office 365 Video configuration](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).</span></span>

<span data-ttu-id="842e8-177">([トップに戻る](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="842e8-177">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="office-365-video-resources"></a><span data-ttu-id="842e8-178">Office 365 のビデオリソース</span><span class="sxs-lookup"><span data-stu-id="842e8-178">Office 365 Video resources</span></span>

<span data-ttu-id="842e8-179">Office 365 ビデオを正常に展開して使用するために役立つその他のリソースを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="842e8-179">Here's a few other resources to help you successfully deploy and use Office 365 Video:</span></span>
  
[<span data-ttu-id="842e8-180">Office 365 のビデオ構成に関するヘルプを参照する</span><span class="sxs-lookup"><span data-stu-id="842e8-180">Find help about Office 365 Video configuration</span></span>](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)
  
[<span data-ttu-id="842e8-181">Office 365 ビデオを利用する</span><span class="sxs-lookup"><span data-stu-id="842e8-181">Meet Office 365 Video</span></span>](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)
  
[<span data-ttu-id="842e8-182">Office 365 でチャネルを作成および管理するビデオ</span><span class="sxs-lookup"><span data-stu-id="842e8-182">Create and manage a channel in Office 365 Video</span></span>](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  
[<span data-ttu-id="842e8-183">Office 365 ビデオ ポータルを管理する</span><span class="sxs-lookup"><span data-stu-id="842e8-183">Manage your Office 365 Video portal</span></span>](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da)
  
[<span data-ttu-id="842e8-184">Office 365 のビデオで使用できるビデオ形式</span><span class="sxs-lookup"><span data-stu-id="842e8-184">Video formats that work in Office 365 Video</span></span>](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
<span data-ttu-id="842e8-185">([トップに戻る](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="842e8-185">([Back to top](office-365-video-networking-faq.md))</span></span>
  
<span data-ttu-id="842e8-186">ここに戻る場合は、次の短いリンクをご利用ください: [https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)</span><span class="sxs-lookup"><span data-stu-id="842e8-186">Here's a short link you can use to come back: [https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)</span></span>
