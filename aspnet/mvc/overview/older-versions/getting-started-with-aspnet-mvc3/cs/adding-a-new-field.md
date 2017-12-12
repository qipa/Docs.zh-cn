---
uid: mvc/overview/older-versions/getting-started-with-aspnet-mvc3/cs/adding-a-new-field
title: "将新字段添加到的电影模型和表 (C#) |Microsoft 文档"
author: Rick-Anderson
description: "本教程将教您构建使用 Microsoft Visual Web Developer 2010 Express Service Pack 1，这是一个 ASP.NET MVC Web 应用程序的基础知识..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 01/12/2011
ms.topic: article
ms.assetid: b4e76c1a-f66e-43a0-aa72-f39df79c07c1
ms.technology: dotnet-mvc
ms.prod: .net-framework
msc.legacyurl: /mvc/overview/older-versions/getting-started-with-aspnet-mvc3/cs/adding-a-new-field
msc.type: authoredcontent
ms.openlocfilehash: c10f3be30a92a605c34fa1c56fa3691389374beb
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2017
---
<a name="adding-a-new-field-to-the-movie-model-and-table-c"></a><span data-ttu-id="6f291-103">将新字段添加到的电影模型和表 (C#)</span><span class="sxs-lookup"><span data-stu-id="6f291-103">Adding a New Field to the Movie Model and Table (C#)</span></span>
====================
<span data-ttu-id="6f291-104">通过[Rick Anderson](https://github.com/Rick-Anderson)</span><span class="sxs-lookup"><span data-stu-id="6f291-104">by [Rick Anderson](https://github.com/Rick-Anderson)</span></span>

> > [!NOTE]
> > <span data-ttu-id="6f291-105">本教程的更新的版本可[此处](../../../getting-started/introduction/getting-started.md)使用 ASP.NET MVC 5 和 Visual Studio 2013。</span><span class="sxs-lookup"><span data-stu-id="6f291-105">An updated version of this tutorial is available [here](../../../getting-started/introduction/getting-started.md) that uses ASP.NET MVC 5 and Visual Studio 2013.</span></span> <span data-ttu-id="6f291-106">它是更安全，请按照要简单得多，并演示更多的功能。</span><span class="sxs-lookup"><span data-stu-id="6f291-106">It's more secure, much simpler to follow and demonstrates more features.</span></span>
> 
> 
> <span data-ttu-id="6f291-107">本教程将教您构建使用 Microsoft Visual Web Developer 2010 Express Service Pack 1，这是 Microsoft Visual Studio 的免费版本的 ASP.NET MVC Web 应用程序的基础知识。</span><span class="sxs-lookup"><span data-stu-id="6f291-107">This tutorial will teach you the basics of building an ASP.NET MVC Web application using Microsoft Visual Web Developer 2010 Express Service Pack 1, which is a free version of Microsoft Visual Studio.</span></span> <span data-ttu-id="6f291-108">在开始之前，请确保已安装下面列出的先决条件。</span><span class="sxs-lookup"><span data-stu-id="6f291-108">Before you start, make sure you've installed the prerequisites listed below.</span></span> <span data-ttu-id="6f291-109">你可以通过单击以下链接安装所有这些： [Web 平台安装程序](https://www.microsoft.com/web/gallery/install.aspx?appid=VWD2010SP1Pack)。</span><span class="sxs-lookup"><span data-stu-id="6f291-109">You can install all of them by clicking the following link: [Web Platform Installer](https://www.microsoft.com/web/gallery/install.aspx?appid=VWD2010SP1Pack).</span></span> <span data-ttu-id="6f291-110">或者，你可以单独安装系统必备组件，使用以下链接：</span><span class="sxs-lookup"><span data-stu-id="6f291-110">Alternatively, you can individually install the prerequisites using the following links:</span></span>
> 
> - [<span data-ttu-id="6f291-111">Visual Studio Web Developer Express SP1 系统必备</span><span class="sxs-lookup"><span data-stu-id="6f291-111">Visual Studio Web Developer Express SP1 prerequisites</span></span>](https://www.microsoft.com/web/gallery/install.aspx?appid=VWD2010SP1Pack)
> - [<span data-ttu-id="6f291-112">ASP.NET MVC 3 Tools 更新</span><span class="sxs-lookup"><span data-stu-id="6f291-112">ASP.NET MVC 3 Tools Update</span></span>](https://www.microsoft.com/web/gallery/install.aspx?appsxml=&amp;appid=MVC3)
> - <span data-ttu-id="6f291-113">[SQL Server Compact 4.0](https://www.microsoft.com/web/gallery/install.aspx?appid=SQLCE;SQLCEVSTools_4_0)（运行时 + 工具支持）</span><span class="sxs-lookup"><span data-stu-id="6f291-113">[SQL Server Compact 4.0](https://www.microsoft.com/web/gallery/install.aspx?appid=SQLCE;SQLCEVSTools_4_0)(runtime + tools support)</span></span>
> 
> <span data-ttu-id="6f291-114">如果你正在使用 Visual Studio 2010，而不 Visual Web Developer 2010，通过单击以下链接安装必备组件： [Visual Studio 2010 系统必备组件](https://www.microsoft.com/web/gallery/install.aspx?appsxml=&amp;appid=VS2010SP1Pack)。</span><span class="sxs-lookup"><span data-stu-id="6f291-114">If you're using Visual Studio 2010 instead of Visual Web Developer 2010, install the prerequisites by clicking the following link: [Visual Studio 2010 prerequisites](https://www.microsoft.com/web/gallery/install.aspx?appsxml=&amp;appid=VS2010SP1Pack).</span></span>
> 
> <span data-ttu-id="6f291-115">使用 C# 源代码的 Visual Web Developer 项目是可以附带本主题。</span><span class="sxs-lookup"><span data-stu-id="6f291-115">A Visual Web Developer project with C# source code is available to accompany this topic.</span></span> <span data-ttu-id="6f291-116">[下载的 C# 版本](https://code.msdn.microsoft.com/Introduction-to-MVC-3-10d1b098)。</span><span class="sxs-lookup"><span data-stu-id="6f291-116">[Download the C# version](https://code.msdn.microsoft.com/Introduction-to-MVC-3-10d1b098).</span></span> <span data-ttu-id="6f291-117">如果你愿意 Visual Basic，切换到[Visual Basic 版本](../vb/intro-to-aspnet-mvc-3.md)本教程。</span><span class="sxs-lookup"><span data-stu-id="6f291-117">If you prefer Visual Basic, switch to the [Visual Basic version](../vb/intro-to-aspnet-mvc-3.md) of this tutorial.</span></span>


<span data-ttu-id="6f291-118">在本部分将对模型类进行某些更改，并了解如何更新数据库架构以匹配的模型更改。</span><span class="sxs-lookup"><span data-stu-id="6f291-118">In this section you'll make some changes to the model classes and learn how you can update the database schema to match the model changes.</span></span>

## <a name="adding-a-rating-property-to-the-movie-model"></a><span data-ttu-id="6f291-119">向电影模型添加分级属性</span><span class="sxs-lookup"><span data-stu-id="6f291-119">Adding a Rating Property to the Movie Model</span></span>

<span data-ttu-id="6f291-120">添加一个新的启动`Rating`到现有的属性`Movie`类。</span><span class="sxs-lookup"><span data-stu-id="6f291-120">Start by adding a new `Rating` property to the existing `Movie` class.</span></span> <span data-ttu-id="6f291-121">打开*Movie.cs*文件并添加`Rating`属性如下所示：</span><span class="sxs-lookup"><span data-stu-id="6f291-121">Open the *Movie.cs* file and add the `Rating` property like this one:</span></span>

[!code-csharp[Main](adding-a-new-field/samples/sample1.cs)]

<span data-ttu-id="6f291-122">完整`Movie`类现在如下所示的以下代码：</span><span class="sxs-lookup"><span data-stu-id="6f291-122">The complete `Movie` class now looks like the following code:</span></span>

[!code-csharp[Main](adding-a-new-field/samples/sample2.cs)]

<span data-ttu-id="6f291-123">重新编译应用程序使用**调试** &gt;**生成电影**菜单命令。</span><span class="sxs-lookup"><span data-stu-id="6f291-123">Recompile the application using the **Debug** &gt;**Build Movie** menu command.</span></span>

<span data-ttu-id="6f291-124">现在，你已更新`Model`类，你还需要更新*\Views\Movies\Index.cshtml*和*\Views\Movies\Create.cshtml*查看模板以支持新`Rating`属性。</span><span class="sxs-lookup"><span data-stu-id="6f291-124">Now that you've updated the `Model` class, you also need to update the *\Views\Movies\Index.cshtml* and *\Views\Movies\Create.cshtml* view templates in order to support the new `Rating` property.</span></span>

<span data-ttu-id="6f291-125">打开*\Views\Movies\Index.cshtml*文件并添加`<th>Rating</th>`列标题之后**价格**列。</span><span class="sxs-lookup"><span data-stu-id="6f291-125">Open the *\Views\Movies\Index.cshtml* file and add a `<th>Rating</th>` column heading just after the **Price** column.</span></span> <span data-ttu-id="6f291-126">然后添加`<td>`结尾处的模板来呈现的列`@item.Rating`值。</span><span class="sxs-lookup"><span data-stu-id="6f291-126">Then add a `<td>` column near the end of the template to render the `@item.Rating` value.</span></span> <span data-ttu-id="6f291-127">下面是哪些更新*Index.cshtml*视图模板如下所示：</span><span class="sxs-lookup"><span data-stu-id="6f291-127">Below is what the updated *Index.cshtml* view template looks like:</span></span>

[!code-cshtml[Main](adding-a-new-field/samples/sample3.cshtml)]

<span data-ttu-id="6f291-128">接下来，打开*\Views\Movies\Create.cshtml*文件并添加以下标记窗体末尾附近。</span><span class="sxs-lookup"><span data-stu-id="6f291-128">Next, open the *\Views\Movies\Create.cshtml* file and add the following markup near the end of the form.</span></span> <span data-ttu-id="6f291-129">这会呈现一个文本框，以便创建新的影片时，可以指定的分级。</span><span class="sxs-lookup"><span data-stu-id="6f291-129">This renders a text box so that you can specify a rating when a new movie is created.</span></span>

[!code-cshtml[Main](adding-a-new-field/samples/sample4.cshtml)]

## <a name="managing-model-and-database-schema-differences"></a><span data-ttu-id="6f291-130">管理模型和数据库架构差异</span><span class="sxs-lookup"><span data-stu-id="6f291-130">Managing Model and Database Schema Differences</span></span>

<span data-ttu-id="6f291-131">你现在已更新应用程序代码以支持新`Rating`属性。</span><span class="sxs-lookup"><span data-stu-id="6f291-131">You've now updated the application code to support the new `Rating` property.</span></span>

<span data-ttu-id="6f291-132">现在运行应用程序并导航到*/Movies* URL。</span><span class="sxs-lookup"><span data-stu-id="6f291-132">Now run the application and navigate to the */Movies* URL.</span></span> <span data-ttu-id="6f291-133">执行此操作，不过，你将看到以下错误：</span><span class="sxs-lookup"><span data-stu-id="6f291-133">When you do this, though, you'll see the following error:</span></span>

![](adding-a-new-field/_static/image1.png)

<span data-ttu-id="6f291-134">你看到此错误，因为更新`Movie`应用程序中的模型类现在是不同的架构`Movie`现有数据库的表。</span><span class="sxs-lookup"><span data-stu-id="6f291-134">You're seeing this error because the updated `Movie` model class in the application is now different than the schema of the `Movie` table of the existing database.</span></span> <span data-ttu-id="6f291-135">（数据库表中没有 `Rating` 列。）</span><span class="sxs-lookup"><span data-stu-id="6f291-135">(There's no `Rating` column in the database table.)</span></span>

<span data-ttu-id="6f291-136">默认情况下，当你使用 Entity Framework Code First 自动创建的数据库，就像此前在本教程中，Code First 表向数据库添加来帮助跟踪数据库的架构是否与从生成的模型类同步。</span><span class="sxs-lookup"><span data-stu-id="6f291-136">By default, when you use Entity Framework Code First to automatically create a database, as you did earlier in this tutorial, Code First adds a table to the database to help track whether the schema of the database is in sync with the model classes it was generated from.</span></span> <span data-ttu-id="6f291-137">如果它们不同步，实体框架将引发错误。</span><span class="sxs-lookup"><span data-stu-id="6f291-137">If they aren't in sync, the Entity Framework throws an error.</span></span> <span data-ttu-id="6f291-138">这使得更轻松地在开发期间，你可能会否则仅发现 （通过晦涩的错误） 在运行时跟踪问题。</span><span class="sxs-lookup"><span data-stu-id="6f291-138">This makes it easier to track down issues at development time that you might otherwise only find (by obscure errors) at run time.</span></span> <span data-ttu-id="6f291-139">同步检查功能是什么因素会导致要显示错误消息，你刚才看到的。</span><span class="sxs-lookup"><span data-stu-id="6f291-139">The sync-checking feature is what causes the error message to be displayed that you just saw.</span></span>

<span data-ttu-id="6f291-140">有两种方法来解决错误：</span><span class="sxs-lookup"><span data-stu-id="6f291-140">There are two approaches to resolving the error:</span></span>

1. <span data-ttu-id="6f291-141">让 Entity Framework 自动丢弃，并基于新的模型类架构重新创建数据库。</span><span class="sxs-lookup"><span data-stu-id="6f291-141">Have the Entity Framework automatically drop and re-create the database based on the new model class schema.</span></span> <span data-ttu-id="6f291-142">此方法时非常方便进行活动开发上测试数据库，因为它允许你快速发展的模型和数据库架构在一起。</span><span class="sxs-lookup"><span data-stu-id="6f291-142">This approach is very convenient when doing active development on a test database, because it allows you to quickly evolve the model and database schema together.</span></span> <span data-ttu-id="6f291-143">缺点，不过，是，则会失去在数据库中的现有数据，以便你*不*想要在生产数据库上使用此方法 ！</span><span class="sxs-lookup"><span data-stu-id="6f291-143">The downside, though, is that you lose existing data in the database — so you *don't* want to use this approach on a production database!</span></span>
2. <span data-ttu-id="6f291-144">对现有数据库架构进行显式修改，使它与模型类相匹配。</span><span class="sxs-lookup"><span data-stu-id="6f291-144">Explicitly modify the schema of the existing database so that it matches the model classes.</span></span> <span data-ttu-id="6f291-145">此方法的优点是可以保留数据。</span><span class="sxs-lookup"><span data-stu-id="6f291-145">The advantage of this approach is that you keep your data.</span></span> <span data-ttu-id="6f291-146">可以手动或通过创建数据库更改脚本进行此更改。</span><span class="sxs-lookup"><span data-stu-id="6f291-146">You can make this change either manually or by creating a database change script.</span></span>

<span data-ttu-id="6f291-147">对于本教程中，我们将使用第一种方法，你必须 Entity Framework Code First 模型更改的任何时候自动重新创建该数据库。</span><span class="sxs-lookup"><span data-stu-id="6f291-147">For this tutorial, we'll use the first approach — you'll have the Entity Framework Code First automatically re-create the database anytime the model changes.</span></span>

## <a name="automatically-re-creating-the-database-on-model-changes"></a><span data-ttu-id="6f291-148">自动重新创建模型更改上的数据库</span><span class="sxs-lookup"><span data-stu-id="6f291-148">Automatically Re-Creating the Database on Model Changes</span></span>

<span data-ttu-id="6f291-149">因此，Code First 自动将删除并重新创建数据库更改为应用程序模型的任何时候，让我们更新应用程序。</span><span class="sxs-lookup"><span data-stu-id="6f291-149">Let's update the application so that Code First automatically drops and re-creates the database anytime you change the model for the application.</span></span>

> [!NOTE] 
> 
> <span data-ttu-id="6f291-150">**警告**应启用的自动删除并重新创建数据库，仅当你正在使用开发或测试数据库，此方法和*永远不会*对生产数据库包含的真实数据。</span><span class="sxs-lookup"><span data-stu-id="6f291-150">**Warning** You should enable this approach of automatically dropping and re-creating the database only when you're using a development or test database, and *never* on a production database that contains real data.</span></span> <span data-ttu-id="6f291-151">在生产服务器上使用它可能导致数据丢失。</span><span class="sxs-lookup"><span data-stu-id="6f291-151">Using it on a production server can lead to data loss.</span></span>


<span data-ttu-id="6f291-152">在**解决方案资源管理器**，右键单击*模型*文件夹，选择**添加**，然后选择**类**。</span><span class="sxs-lookup"><span data-stu-id="6f291-152">In **Solution Explorer**, right click the *Models* folder, select **Add**, and then select **Class**.</span></span>

![](adding-a-new-field/_static/image2.png)

<span data-ttu-id="6f291-153">将类"MovieInitializer"。</span><span class="sxs-lookup"><span data-stu-id="6f291-153">Name the class "MovieInitializer".</span></span> <span data-ttu-id="6f291-154">更新`MovieInitializer`类包含以下代码：</span><span class="sxs-lookup"><span data-stu-id="6f291-154">Update the `MovieInitializer` class to contain the following code:</span></span>

[!code-csharp[Main](adding-a-new-field/samples/sample5.cs)]

<span data-ttu-id="6f291-155">`MovieInitializer`类指定应删除并自动重新创建的模型类更改使用模型的数据库。</span><span class="sxs-lookup"><span data-stu-id="6f291-155">The `MovieInitializer` class specifies that the database used by the model should be dropped and automatically re-created if the model classes ever change.</span></span> <span data-ttu-id="6f291-156">代码包含`Seed`方法，以便指定一些默认数据自动向数据库添加任何时间已创建 （或重新创建）。</span><span class="sxs-lookup"><span data-stu-id="6f291-156">The code includes a `Seed` method to specify some default data to automatically add to the database any time it's created (or re-created).</span></span> <span data-ttu-id="6f291-157">这提供了有用的方式来使用填充数据库一些示例数据，而无需手动填充它每次进行更改的模型。</span><span class="sxs-lookup"><span data-stu-id="6f291-157">This provides a useful way to populate the database with some sample data, without requiring you to manually populate it each time you make a model change.</span></span>

<span data-ttu-id="6f291-158">既然你已经定义`MovieInitializer`类，你将需要连接它，以便每次应用程序运行时，它会检查是否从数据库中的架构不同的模型类。</span><span class="sxs-lookup"><span data-stu-id="6f291-158">Now that you've defined the `MovieInitializer` class, you'll want to wire it up so that each time the application runs, it checks whether the model classes are different from the schema in the database.</span></span> <span data-ttu-id="6f291-159">如果它们是，你可以运行初始值设定项来重新创建要与模型匹配，然后填充示例数据的数据库的数据库。</span><span class="sxs-lookup"><span data-stu-id="6f291-159">If they are, you can run the initializer to re-create the database to match the model and then populate the database with the sample data.</span></span>

<span data-ttu-id="6f291-160">打开*Global.asax*根目录下的文件`MvcMovies`项目：</span><span class="sxs-lookup"><span data-stu-id="6f291-160">Open the *Global.asax* file that's at the root of the `MvcMovies` project:</span></span>

[![](adding-a-new-field/_static/image4.png)](adding-a-new-field/_static/image3.png)

<span data-ttu-id="6f291-161">*Global.asax*文件包含定义的整个应用程序项目，而包含的类`Application_Start`运行应用程序首次启动时的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="6f291-161">The *Global.asax* file contains the class that defines the entire application for the project, and contains an `Application_Start` event handler that runs when the application first starts.</span></span>

<span data-ttu-id="6f291-162">让我们添加两个使用到文件顶部的语句。</span><span class="sxs-lookup"><span data-stu-id="6f291-162">Let's add two using statements to the top of the file.</span></span> <span data-ttu-id="6f291-163">第一个引用实体框架命名空间，而第二个引用命名空间其中我们`MovieInitializer`类生活：</span><span class="sxs-lookup"><span data-stu-id="6f291-163">The first references the Entity Framework namespace, and the second references the namespace where our `MovieInitializer` class lives:</span></span>

[!code-csharp[Main](adding-a-new-field/samples/sample6.cs)]

<span data-ttu-id="6f291-164">然后找到`Application_Start`方法，并添加到调用`Database.SetInitializer`开头的方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6f291-164">Then find the `Application_Start` method and add a call to `Database.SetInitializer` at the beginning of the method, as shown below:</span></span>

[!code-csharp[Main](adding-a-new-field/samples/sample7.cs)]

<span data-ttu-id="6f291-165">`Database.SetInitializer`刚添加的语句指示该数据库由`MovieDBContext`应自动删除并重新创建如果不匹配的架构和数据库实例。</span><span class="sxs-lookup"><span data-stu-id="6f291-165">The `Database.SetInitializer` statement you just added indicates that the database used by the `MovieDBContext` instance should be automatically deleted and re-created if the schema and the database don't match.</span></span> <span data-ttu-id="6f291-166">如你所看到的它还将使用数据库中指定示例数据填充和`MovieInitializer`类。</span><span class="sxs-lookup"><span data-stu-id="6f291-166">And as you saw, it will also populate the database with the sample data that's specified in the `MovieInitializer` class.</span></span>

<span data-ttu-id="6f291-167">关闭*Global.asax*文件。</span><span class="sxs-lookup"><span data-stu-id="6f291-167">Close the *Global.asax* file.</span></span>

<span data-ttu-id="6f291-168">重新运行该应用程序并导航到*/Movies* URL。</span><span class="sxs-lookup"><span data-stu-id="6f291-168">Re-run the application and navigate to the */Movies* URL.</span></span> <span data-ttu-id="6f291-169">当应用程序启动时，它将检测模型结构不再与数据库架构相匹配。</span><span class="sxs-lookup"><span data-stu-id="6f291-169">When the application starts, it detects that the model structure no longer matches the database schema.</span></span> <span data-ttu-id="6f291-170">自动重新创建数据库，以匹配新的模型结构，并填充示例电影的数据库：</span><span class="sxs-lookup"><span data-stu-id="6f291-170">It automatically re-creates the database to match the new model structure and populates the database with the sample movies:</span></span>

![7_MyMovieList_SM](adding-a-new-field/_static/image5.png)

<span data-ttu-id="6f291-172">单击**新建**链接添加新的影片。</span><span class="sxs-lookup"><span data-stu-id="6f291-172">Click the **Create New** link to add a new movie.</span></span> <span data-ttu-id="6f291-173">请注意，你可以添加一个级别。</span><span class="sxs-lookup"><span data-stu-id="6f291-173">Note that you can add a rating.</span></span>

<span data-ttu-id="6f291-174">[![7_CreateRioII](adding-a-new-field/_static/image7.png)](adding-a-new-field/_static/image6.png)</span><span class="sxs-lookup"><span data-stu-id="6f291-174">[![7_CreateRioII](adding-a-new-field/_static/image7.png)](adding-a-new-field/_static/image6.png)</span></span>

<span data-ttu-id="6f291-175">单击 **“创建”**。</span><span class="sxs-lookup"><span data-stu-id="6f291-175">Click **Create**.</span></span> <span data-ttu-id="6f291-176">新的影片，包括评级，现在显示在电影列出：</span><span class="sxs-lookup"><span data-stu-id="6f291-176">The new movie, including the rating, now shows up in the movies listing:</span></span>

<span data-ttu-id="6f291-177">[![7_ourNewMovie_SM](adding-a-new-field/_static/image9.png)](adding-a-new-field/_static/image8.png)</span><span class="sxs-lookup"><span data-stu-id="6f291-177">[![7_ourNewMovie_SM](adding-a-new-field/_static/image9.png)](adding-a-new-field/_static/image8.png)</span></span>

<span data-ttu-id="6f291-178">在本部分中您将了解如何修改模型对象和保留数据库与更改同步。</span><span class="sxs-lookup"><span data-stu-id="6f291-178">In this section you saw how you can modify model objects and keep the database in sync with the changes.</span></span> <span data-ttu-id="6f291-179">你还了解了一种方法来填充新创建的数据库使用示例数据，因此你还可以尝试方案。</span><span class="sxs-lookup"><span data-stu-id="6f291-179">You also learned a way to populate a newly created database with sample data so you can try out scenarios.</span></span> <span data-ttu-id="6f291-180">接下来，让我们看一下如何将更丰富的验证逻辑添加到模型类和启用一些业务规则，以强制执行。</span><span class="sxs-lookup"><span data-stu-id="6f291-180">Next, let's look at how you can add richer validation logic to the model classes and enable some business rules to be enforced.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="6f291-181">[上一页](examining-the-edit-methods-and-edit-view.md)
[下一页](adding-validation-to-the-model.md)</span><span class="sxs-lookup"><span data-stu-id="6f291-181">[Previous](examining-the-edit-methods-and-edit-view.md)
[Next](adding-validation-to-the-model.md)</span></span>