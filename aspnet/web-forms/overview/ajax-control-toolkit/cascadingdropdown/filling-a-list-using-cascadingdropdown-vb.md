---
uid: web-forms/overview/ajax-control-toolkit/cascadingdropdown/filling-a-list-using-cascadingdropdown-vb
title: 填充使用 CascadingDropDown (VB) 的列表 |Microsoft 文档
author: wenz
description: AJAX 控件工具包中的 CascadingDropDown 控件扩展的 DropDownList 控件，使得一个 DropDownList 负载中的更改关联中 anoth 值...
ms.author: aspnetcontent
manager: wpickett
ms.date: 06/02/2008
ms.topic: article
ms.assetid: 5236695e-5c70-4887-baee-0bfb0afb3448
ms.technology: dotnet-webforms
ms.prod: .net-framework
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/cascadingdropdown/filling-a-list-using-cascadingdropdown-vb
msc.type: authoredcontent
ms.openlocfilehash: e488a30443970d5e2ce825abd96d8e4a027585d1
ms.sourcegitcommit: f8852267f463b62d7f975e56bea9aa3f68fbbdeb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/06/2018
---
<a name="filling-a-list-using-cascadingdropdown-vb"></a>填充使用 CascadingDropDown (VB) 的列表
====================
通过[Christian Wenz](https://github.com/wenz)

[下载代码](http://download.microsoft.com/download/9/0/7/907760b1-2c60-4f81-aeb6-ca416a573b0d/cascadingdropdown0.vb.zip)或[下载 PDF](http://download.microsoft.com/download/2/d/c/2dc10e34-6983-41d4-9c08-f78f5387d32b/cascadingdropdown0VB.pdf)

> AJAX 控件工具包中的 CascadingDropDown 控件扩展的 DropDownList 控件，使得一个 DropDownList 负载中的更改关联中另一个 DropDownList 值。 （例如，一个列表提供了一份我们状态，并且用处于该状态的主要城市然后填充下一个列表。）若要解决第一次质询是实际填充使用此控件的下拉列表。


## <a name="overview"></a>概述

AJAX 控件工具包中的 CascadingDropDown 控件扩展的 DropDownList 控件，使得一个 DropDownList 负载中的更改关联中另一个 DropDownList 值。 （例如，一个列表提供了一份我们状态，并且用处于该状态的主要城市然后填充下一个列表。）若要解决第一次质询是实际填充使用此控件的下拉列表。

## <a name="steps"></a>步骤

为了激活 ASP.NET AJAX 和控件工具包中的功能`ScriptManager`必须在页面上任意位置放置控件 (但内`<form>`元素):

[!code-aspx[Main](filling-a-list-using-cascadingdropdown-vb/samples/sample1.aspx)]

然后，需要进行的 DropDownList 控制：

[!code-aspx[Main](filling-a-list-using-cascadingdropdown-vb/samples/sample2.aspx)]

对于此列表中，添加 CascadingDropDown 扩展程序。 它将发送的异步请求到 web 服务，然后将返回要在列表中显示的项的列表。 为此，需要设置以下 CascadingDropDown 属性：

- `ServicePath`: 提供的列表项 web 服务的 URL
- `ServiceMethod`: Web 方法提供的列表项
- `TargetControlID`: ID 的下拉列表
- `Category`： 提交给 web 方法调用时的类别信息
- `PromptText`： 当以异步方式从服务器加载列表数据时显示的文本

下面是有关标记`CascadingDropDown`元素。 C# 和 VB 的唯一区别是关联的 web 服务的名称：

[!code-aspx[Main](filling-a-list-using-cascadingdropdown-vb/samples/sample3.aspx)]

JavaScript 代码来自`CascadingDropDown`扩展程序调用 web 服务方法具有以下签名：

[!code-vb[Main](filling-a-list-using-cascadingdropdown-vb/samples/sample4.vb)]

因此重要方面是该方法需要返回类型的数组`CascadingDropDownNameValue`（由 ASP.NET AJAX 控件工具包定义）。 在`CascadingDropDownNameValue`构造函数，第一个列表项的文本，然后其值都必须提供，就像`<option value="VALUE">NAME</option>`像在 HTML 中。 下面是一些示例数据：

[!code-aspx[Main](filling-a-list-using-cascadingdropdown-vb/samples/sample5.aspx)]

加载浏览器中将触发三个供应商要填充的列表。


[![列表已自动填充](filling-a-list-using-cascadingdropdown-vb/_static/image2.png)](filling-a-list-using-cascadingdropdown-vb/_static/image1.png)

列表已自动填充 ([单击以查看实际尺寸的图像](filling-a-list-using-cascadingdropdown-vb/_static/image3.png))

> [!div class="step-by-step"]
> [上一页](using-auto-postback-with-cascadingdropdown-cs.md)
> [下一页](using-cascadingdropdown-with-a-database-vb.md)
