---
uid: web-pages/overview/security/using-a-catpcha-to-prevent-automated-programs-bots-from-using-your-aspnet-web-site
title: "使用验证码以使用 ASP.NET Web Razor 防止机器人） 的站点 |Microsoft 文档"
author: microsoft
description: "此文章介绍了如何使用 ReCaptcha （一种安全措施） 来防止自动的程序 （机器人） 执行任务中的 ASP.NET Web Pages (Razor) 我们..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 05/21/2012
ms.topic: article
ms.assetid: 2b381a41-2cb3-40c0-8545-1d393e22877f
ms.technology: dotnet-webpages
ms.prod: .net-framework
msc.legacyurl: /web-pages/overview/security/using-a-catpcha-to-prevent-automated-programs-bots-from-using-your-aspnet-web-site
msc.type: authoredcontent
ms.openlocfilehash: 75e80a3e7ebe787852152404bf2e0bf88a1a6a56
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2017
---
<a name="using-a-captcha-to-prevent-bots-from-using-your-aspnet-web-razor-site"></a><span data-ttu-id="7ca11-103">使用验证码以使用 ASP.NET Web Razor 防止机器人） 站点</span><span class="sxs-lookup"><span data-stu-id="7ca11-103">Using a CAPTCHA to Prevent Bots from Using Your ASP.NET Web Razor) Site</span></span>
====================
<span data-ttu-id="7ca11-104">通过[Microsoft](https://github.com/microsoft)</span><span class="sxs-lookup"><span data-stu-id="7ca11-104">by [Microsoft](https://github.com/microsoft)</span></span>

> <span data-ttu-id="7ca11-105">此文章介绍了如何使用 ReCaptcha （一种安全措施） 来防止自动的程序 （机器人） 在 ASP.NET Web 页 (Razor) 网站中执行任务。</span><span class="sxs-lookup"><span data-stu-id="7ca11-105">This article explains how to use ReCaptcha (a security measure) to prevent automated programs (bots) from performing tasks in an ASP.NET Web Pages (Razor) website.</span></span>
> 
> <span data-ttu-id="7ca11-106">**你将学习：**</span><span class="sxs-lookup"><span data-stu-id="7ca11-106">**What you'll learn:**</span></span> 
> 
> - <span data-ttu-id="7ca11-107">如何将 CAPTCHA 测试添加到你的站点。</span><span class="sxs-lookup"><span data-stu-id="7ca11-107">How to add a CAPTCHA test to your site.</span></span>
> 
> <span data-ttu-id="7ca11-108">这些是文章中引入的 ASP.NET 功能：</span><span class="sxs-lookup"><span data-stu-id="7ca11-108">These are the ASP.NET features introduced in the article:</span></span>
> 
> - <span data-ttu-id="7ca11-109">`ReCaptcha`帮助器。</span><span class="sxs-lookup"><span data-stu-id="7ca11-109">The `ReCaptcha` helper.</span></span>
> 
> > [!NOTE]
> > <span data-ttu-id="7ca11-110">这篇文章中的信息适用于 ASP.NET Web Pages 1.0 和 Web Pages 2。</span><span class="sxs-lookup"><span data-stu-id="7ca11-110">The information in this article applies to ASP.NET Web Pages 1.0 and Web Pages 2.</span></span>


## <a name="about-captchas"></a><span data-ttu-id="7ca11-111">有关 CAPTCHAs</span><span class="sxs-lookup"><span data-stu-id="7ca11-111">About CAPTCHAs</span></span>

<span data-ttu-id="7ca11-112">在你的站点，或即使只是使用户可以注册任何时间输入名称和 URL （如博客注释时），你可能会出现大量的假名称。</span><span class="sxs-lookup"><span data-stu-id="7ca11-112">Any time you let people register in your site, or even just enter a name and URL (like for a blog comment), you might get a flood of fake names.</span></span> <span data-ttu-id="7ca11-113">这些通常会尝试将 Url 保留在用户可在找到每个网站的自动程序 （机器人） 保留。</span><span class="sxs-lookup"><span data-stu-id="7ca11-113">These are often left by automated programs (bots) that try to leave URLs in every website they can find.</span></span> <span data-ttu-id="7ca11-114">（常见动机是 post 的产品销售的 Url。）</span><span class="sxs-lookup"><span data-stu-id="7ca11-114">(A common motivation is to post the URLs of products for sale.)</span></span>

<span data-ttu-id="7ca11-115">你可以帮助确保用户是真正的用户而不是计算机程序，通过使用*CAPTCHA*来验证用户在注册或否则输入其名称和站点时。</span><span class="sxs-lookup"><span data-stu-id="7ca11-115">You can help make sure that a user is real person and not a computer program by using a *CAPTCHA* to validate users when they register or otherwise enter their name and site.</span></span> <span data-ttu-id="7ca11-116">CAPTCHA 代表完全自动公共执行测试来告诉计算机和理解分离。</span><span class="sxs-lookup"><span data-stu-id="7ca11-116">CAPTCHA stands for Completely Automated Public Turing test to tell Computers and Humans Apart.</span></span> <span data-ttu-id="7ca11-117">验证码是*质询-响应*便于人员完成但硬的自动程序执行的测试要求用户执行某些操作。</span><span class="sxs-lookup"><span data-stu-id="7ca11-117">A CAPTCHA is a *challenge-response* test in which the user is asked to do something that is easy for a person to do but hard for an automated program to do.</span></span> <span data-ttu-id="7ca11-118">最常用的 CAPTCHA 类型是一个位置，你可以看到一些失真的号和需要键入它们。</span><span class="sxs-lookup"><span data-stu-id="7ca11-118">The most common type of CAPTCHA is one where you see some distorted letters and are asked to type them.</span></span> <span data-ttu-id="7ca11-119">（扭曲应该以使其难以机器人才能破译字母。）</span><span class="sxs-lookup"><span data-stu-id="7ca11-119">(The distortion is supposed to make it hard for bots to decipher the letters.)</span></span>

## <a name="adding-a-recaptcha-test"></a><span data-ttu-id="7ca11-120">添加 ReCaptcha 测试</span><span class="sxs-lookup"><span data-stu-id="7ca11-120">Adding a ReCaptcha Test</span></span>

<span data-ttu-id="7ca11-121">在 ASP.NET 页中，你可以使用`ReCaptcha`用于呈现基于 ReCaptcha 服务的 CAPTCHA 测试帮助 ([http://recaptcha.net](http://recaptcha.net))。</span><span class="sxs-lookup"><span data-stu-id="7ca11-121">In ASP.NET pages, you can use the `ReCaptcha` helper to render a CAPTCHA test that is based on the ReCaptcha service ([http://recaptcha.net](http://recaptcha.net)).</span></span> <span data-ttu-id="7ca11-122">`ReCaptcha`帮助程序显示用户必须之前验证页，请输入正确的两个失真单词的图像。</span><span class="sxs-lookup"><span data-stu-id="7ca11-122">The `ReCaptcha` helper displays an image of two distorted words that users have to enter correctly before the page is validated.</span></span> <span data-ttu-id="7ca11-123">用户响应 ReCaptcha.Net 服务通过验证。</span><span class="sxs-lookup"><span data-stu-id="7ca11-123">The user response is validated by the ReCaptcha.Net service.</span></span>

![](using-a-catpcha-to-prevent-automated-programs-bots-from-using-your-aspnet-web-site/_static/image1.jpg)

1. <span data-ttu-id="7ca11-124">注册你的网站在 ReCaptcha.Net ([http://recaptcha.net](http://recaptcha.net))。</span><span class="sxs-lookup"><span data-stu-id="7ca11-124">Register your website at ReCaptcha.Net ([http://recaptcha.net](http://recaptcha.net)).</span></span> <span data-ttu-id="7ca11-125">你已完成注册，你会获得一个公钥和私钥。</span><span class="sxs-lookup"><span data-stu-id="7ca11-125">When you've completed registration, you'll get a public key and a private key.</span></span>
2. <span data-ttu-id="7ca11-126">将 ASP.NET Web 帮助程序库添加到你的网站中所述[安装 ASP.NET 网页站点中的帮助器](https://go.microsoft.com/fwlink/?LinkId=252372)，如果你尚未。</span><span class="sxs-lookup"><span data-stu-id="7ca11-126">Add the ASP.NET Web Helpers Library to your website as described in [Installing Helpers in an ASP.NET Web Pages Site](https://go.microsoft.com/fwlink/?LinkId=252372), if you haven't already.</span></span>
3. <span data-ttu-id="7ca11-127">如果你还没有 *\_AppStart.cshtml*文件，在网站的根文件夹中创建名为的文件 *\_AppStart.cshtml*。</span><span class="sxs-lookup"><span data-stu-id="7ca11-127">If you don't already have a *\_AppStart.cshtml* file, in the root folder of a website create a file named *\_AppStart.cshtml*.</span></span>
4. <span data-ttu-id="7ca11-128">添加以下`Recaptcha`中的帮助器设置 *\_AppStart.cshtml*文件：</span><span class="sxs-lookup"><span data-stu-id="7ca11-128">Add the following `Recaptcha` helper settings in the *\_AppStart.cshtml* file:</span></span> 

    [!code-cshtml[Main](using-a-catpcha-to-prevent-automated-programs-bots-from-using-your-aspnet-web-site/samples/sample1.cshtml?highlight=6-7)]
5. <span data-ttu-id="7ca11-129">设置`PublicKey`和`PrivateKey`属性使用你自己的公共和私有密钥。</span><span class="sxs-lookup"><span data-stu-id="7ca11-129">Set the `PublicKey` and `PrivateKey` properties using your own public and private keys.</span></span>
6. <span data-ttu-id="7ca11-130">保存 *\_AppStart.cshtml*文件并将其关闭。</span><span class="sxs-lookup"><span data-stu-id="7ca11-130">Save the *\_AppStart.cshtml* file and close it.</span></span>
7. <span data-ttu-id="7ca11-131">在网站的根文件夹中，创建名为的新页*Recaptcha.cshtml*。</span><span class="sxs-lookup"><span data-stu-id="7ca11-131">In the root folder of a website, create new page named *Recaptcha.cshtml*.</span></span>
8. <span data-ttu-id="7ca11-132">将现有内容替换为以下：</span><span class="sxs-lookup"><span data-stu-id="7ca11-132">Replace the existing content with the following:</span></span> 

    [!code-cshtml[Main](using-a-catpcha-to-prevent-automated-programs-bots-from-using-your-aspnet-web-site/samples/sample2.cshtml)]
9. <span data-ttu-id="7ca11-133">运行*Recaptcha.cshtml*在浏览器中的页。</span><span class="sxs-lookup"><span data-stu-id="7ca11-133">Run the *Recaptcha.cshtml* page in a browser.</span></span> <span data-ttu-id="7ca11-134">如果`PrivateKey`值是否有效，该页显示 ReCaptcha 控件和一个按钮。</span><span class="sxs-lookup"><span data-stu-id="7ca11-134">If the `PrivateKey` value is valid, the page displays the ReCaptcha control and a button.</span></span> <span data-ttu-id="7ca11-135">如果全局在尚未设置密钥 *\_AppStart.html*，页面将显示错误。</span><span class="sxs-lookup"><span data-stu-id="7ca11-135">If you had not set the keys globally in *\_AppStart.html*, the page would display an error.</span></span> 

    ![](using-a-catpcha-to-prevent-automated-programs-bots-from-using-your-aspnet-web-site/_static/image1.png)
10. <span data-ttu-id="7ca11-136">测试输入的单词。</span><span class="sxs-lookup"><span data-stu-id="7ca11-136">Enter the words for the test.</span></span> <span data-ttu-id="7ca11-137">如果您传入 ReCaptcha 测试，你将看到一条消息针对此效果。</span><span class="sxs-lookup"><span data-stu-id="7ca11-137">If you pass the ReCaptcha test, you see a message to that effect.</span></span> <span data-ttu-id="7ca11-138">否则，你看到一条错误消息和 ReCaptcha 控件重新显示。</span><span class="sxs-lookup"><span data-stu-id="7ca11-138">Otherwise you see an error message and the ReCaptcha control is redisplayed.</span></span>

> [!NOTE]
> <span data-ttu-id="7ca11-139">如果你的计算机处于使用代理服务器的域，你可能需要配置`defaultproxy`元素*Web.config*文件。</span><span class="sxs-lookup"><span data-stu-id="7ca11-139">If your computer is on a domain that uses proxy server, you might need to configure the `defaultproxy` element of the *Web.config* file.</span></span> <span data-ttu-id="7ca11-140">下面的示例演示*Web.config*文件`defaultproxy`元素配置为启用 ReCaptcha 服务正常工作。</span><span class="sxs-lookup"><span data-stu-id="7ca11-140">The following example shows a *Web.config* file with the `defaultproxy` element configured to enable the ReCaptcha service to work.</span></span>
> 
> [!code-xml[Main](using-a-catpcha-to-prevent-automated-programs-bots-from-using-your-aspnet-web-site/samples/sample3.xml)]


<a id="Additional_Resources"></a>
## <a name="additional-resources"></a><span data-ttu-id="7ca11-141">其他资源</span><span class="sxs-lookup"><span data-stu-id="7ca11-141">Additional Resources</span></span>


- [<span data-ttu-id="7ca11-142">中的 ASP.NET Web 页网站的自定义站点范围行为</span><span class="sxs-lookup"><span data-stu-id="7ca11-142">Customizing Site-Wide Behavior for ASP.NET Web Pages Sites</span></span>](https://go.microsoft.com/fwlink/?LinkId=202906)
- [<span data-ttu-id="7ca11-143">ReCaptcha 站点</span><span class="sxs-lookup"><span data-stu-id="7ca11-143">ReCaptcha site</span></span>](https://www.google.com/recaptcha)