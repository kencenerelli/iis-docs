---
title: "Classic ASP parent paths are disabled by default | Microsoft Docs"
author: rmcmurray
description: "Classic ASP Parent Paths let developers use relative addresses that contain '..' in the paths to files or folders. For example, the following code excerpt il..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 02/19/2009
ms.topic: article
ms.assetid: 
ms.technology: dotnet-webforms
ms.prod: .net-framework
msc.legacyurl: /learn/application-frameworks/running-classic-asp-applications-on-iis-7-and-iis-8/classic-asp-parent-paths-are-disabled-by-default
msc.type: authoredcontent
---
Classic ASP parent paths are disabled by default
====================
by [Robert McMurray](https://github.com/rmcmurray)

Classic ASP Parent Paths let developers use relative addresses that contain ".." in the paths to files or folders. For example, the following code excerpt illustrates an ASP page that maps a parent path:

[!code-unknown[Main](classic-asp-parent-paths-are-disabled-by-default/samples/sample-127250-1.unknown)]

In addition, the following code except illustrates an ASP page that references an included file in a folder that uses a parent path:

[!code-unknown[Main](classic-asp-parent-paths-are-disabled-by-default/samples/sample-127250-2.unknown)]

In several earlier versions of IIS, parent paths were enabled by default. In IIS 6.0 the default behavior changed to disable parent paths, and this was done for security and design reasons: by preventing the execution of parent paths, you are preventing the inclusion of content across security or application boundaries. By default, class ASP script error messages are not sent to the Web browser, and any attempts to use parent paths will return the following error message to a Web browser:

[!code-unknown[Main](classic-asp-parent-paths-are-disabled-by-default/samples/sample-127250-3.unknown)]

If you enable sending ASP script error messages and your classic ASP scripts attempt to map a path in a parent folder, you receive the following error message in your Web browser:

[!code-unknown[Main](classic-asp-parent-paths-are-disabled-by-default/samples/sample-127250-4.unknown)]

When your classic ASP scripts attempt to include a page that uses parent paths in IIS, you receive the following error message in your Web browser:

[!code-unknown[Main](classic-asp-parent-paths-are-disabled-by-default/samples/sample-127250-5.unknown)]

#### Working with User Access Control

You need to make sure that you follow the steps in this document by using an account that has full administrative permissions. This is best accomplished by using one of two methods:

- Log in to your computer by using the local administrator account.
- If you are logged in using an account that has administrative permissions but that is not the local administrator account, open all applications and all command prompt sessions by using the "Run as Administrator" option.

These above conditions are required because the User Account Control (UAC) security component in Windows Vista and Windows Server 2008 will prevent administrative access to the IIS configuration settings. For more information about UAC, see the following documentation:

- [User Account Control](https://go.microsoft.com/fwlink/?LinkId=113664)

## Resolving Parent Paths Issues

### Using Virtual Paths

As an alternative to using parent paths in your ASP code, you can use virtual paths. Virtual paths require that you enter the full folder path from the URL root of your Web site. For example:

**Mapping paths**:

[!code-unknown[Main](classic-asp-parent-paths-are-disabled-by-default/samples/sample-127250-6.unknown)]

**Including paths**:

[!code-unknown[Main](classic-asp-parent-paths-are-disabled-by-default/samples/sample-127250-7.unknown)]

### Enabling ASP Parent Paths

You can enable or disable parent paths by using IIS Manager. To do so, open IIS Manager and navigate to the site or application where you want to configure parent paths, and then-double click the **ASP** feature.

> [![](classic-asp-parent-paths-are-disabled-by-default/_static/image2.jpg)](classic-asp-parent-paths-are-disabled-by-default/_static/image1.jpg)


In the list of ASP features, configure the **Enable Parent Paths** option.

> [![](classic-asp-parent-paths-are-disabled-by-default/_static/image4.jpg)](classic-asp-parent-paths-are-disabled-by-default/_static/image3.jpg)


You can also configure this setting by using the command-line tool AppCmd.exe with the following syntax:

[!code-console[Main](classic-asp-parent-paths-are-disabled-by-default/samples/sample8.cmd)]

## More Information

For additional information about the options that are available for classic ASP, see the following page in the IIS configuration reference on the Microsoft [IIS.net](https://www.iis.net/) Web site:

> [https://www.iis.net/ConfigReference/system.webServer/asp](../../../configreference/system.webserver/asp.md)


For additional detail on parent paths in IIS, see the following page in the Microsoft Knowledge Base:

> **Enable Parent Paths Is Disabled by Default in IIS 6.0**  
> [https://support.microsoft.com/kb/332117](https://support.microsoft.com/kb/332117)


[Discuss in IIS Forums](https://forums.iis.net/1044.aspx)