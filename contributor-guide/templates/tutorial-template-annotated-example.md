---
title:="Deploy an ASP.NET web app to App Service | Microsoft Docs" 
description: "This tutorial shows how to deploy an ASP.NET web application to a web app in Azure App Service by using Visual Studio 2015. "
services: "app-service"
documentationCenter: ""
authors: "CarlRabeler"
manager: "jhubbard"
editor: ""/>

ms.service="app-service"
ms.devlang="NA"
ms.custom: "NA"
ms.topic="article"
ms.tgt_pltfrm="NA"
ms.workload="NA"
ms.date="10/20/2016"
ms.author="carlrab;barbkess"/>

---
<!------------------
This topic is annotated with TEMPLATE guidelines for TUTORIAL TOPICS.


Metadata guidelines

title
	60 characters or less. Tells users clearly what they will do (deploy an ASP.NET web app to App Service). Not the same as H1. It's 60 characters or fewer including all characters between the quotes and the Microsoft Docs site identifier.

description
	115-145 characters. Duplicate of the first sentence in the introduction. This is the abstract of the article that displays under the title when searching in Bing or Google. 

	Example: "This tutorial shows how to deploy an ASP.NET web application to a web app in Azure App Service by using Visual Studio 2015."
------------------>

<!----------------

TEMPLATE GUIDELINES for tutorial topics

The tutorial topic shows users how to solve a problem using a product or service. It includes the prerequisites and steps users need to be successful.  

It is a "solve a problem" topic, not a "learn concepts" topic.

DO include this:
	• What users will do
	• What they will create or accomplish by the end of the tutorial
	• Time estimate
	• Optional but useful: Include a diagram or video. Diagrams help users see the big picture of what they are doing. A video of the steps can be used by customers as an alternative to following the steps in the topic.
	• Prerequisites: Technical expertise and software requirements
	• End-to-end steps. At the end, include next steps to deeper or related tutorials so users can learn more about the service

DON'T include this:
	• Conceptual info about the service. This info is in overview topics that you can link to in the prerequisites section if necessary

------------------->

<!------------------
GUIDELINES for the H1 
	
	The H1 should answer the question "What will I do in this topic?" Write the H1 heading in conversational language and use search keywords as much as possible. Since this is a "solve a problem" topic, make sure the title indicates that. Use a strong, specific verb like "Deploy."  
		
	Heading must use an industry standard term. If your feature is a proprietary name like "Elastic database pools", use a synonym. For example: "Learn about elastic database pools for multi-tenant databases." In this case multi-tenant database is the industry-standard term that will be an anchor for finding the topic.

-------------------->

# Deploy an ASP.NET web app to Azure App Service by using Visual Studio #

<!------------------
	GUIDELINES for introduction
	
	The introduction is 1-2 sentences.  It is optimized for search and sets proper expectations about what to expect in the article. It should contain the top keywords that you are using throughout the article.The introduction should be brief and to the point of what users will do and what they will accomplish. 

	In this example:
	 

Sentence #1 Explains what the user will do. This is also the metadata description. 
	This tutorial shows how to deploy an ASP.NET web application to a web app in Azure App Service by using Visual Studio 2015. 

Sentence #2 Explains what users will learn and the benefit.  
	When you’re finished, you’ll have a simple web application up and running in the cloud.

-------------------->


This tutorial shows how to deploy an ASP.NET web application to a [web app in Azure App Service](app-service-web-overview.md) by using Visual Studio 2015. When you’re finished, you’ll have a simple web application up and running in the cloud.


**Time estimate**: This tutorial will take about 10-15 minutes to complete. Installing the Azure SDK for .NET will take additional time: several minutes to a half hour, depending on how many SDK dependencies you have on your computer.


The diagram illustrates what you do in the tutorial.

![Visual Studio create and deploy diagram](./media/web-sites-dotnet-get-started/Create_App.png)


## Prerequisites

* The tutorial assumes you have worked with ASP.NET MVC and Visual Studio. If you need an introduction, see [Getting Started with ASP.NET MVC 5](http://www.asp.net/mvc/overview/getting-started/introduction/getting-started).

* You need an Azure account. You can [open a free Azure account](/pricing/free-trial/?WT.mc_id=A261C142F) or [Activate Visual Studio subscriber benefits](/pricing/member-offers/msdn-benefits-details/?WT.mc_id=A261C142F). 

	If you want to get started with Azure App Service before you sign up for an Azure account, go to [Try App Service](http://go.microsoft.com/fwlink/?LinkId=523751). There you can create a short-lived starter app in App Service — no credit card required, and no commitments.


<!--**Procedure**: *This is the first “step”. Make titles H2’s and short and clear – H2’s appear in the right pane on the web page and are important for navigation.*-->

## <a name="setupdevenv"></a>Set up the development environment

The tutorial is written for Visual Studio 2015 with the [Azure SDK for .NET](../dotnet-sdk.md) 2.9 or later. 

* [Download the latest Azure SDK for Visual Studio 2015](http://go.microsoft.com/fwlink/?linkid=518003). The SDK installs Visual Studio 2015 if you don't already have it.


<!--**Notes**: *Notes provide just-in-time info: A Note is “by the way” info, an Important is info users need to complete a task, Tip is for shortcuts. Don’t overdo*.-->

	>[AZURE.NOTE] Depending on how many of the SDK dependencies you already have on your machine, installing the SDK could take a long time, from several minutes to a half hour or more.

If you have Visual Studio 2013 and prefer to use that, you can [download the latest Azure SDK for Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=324322). Some screens may look different from the illustrations.


<!--**Procedures**: *This is the second “step." They often include substeps. Again, use a short title that tells users what they’ll do*. *("Configure a new web project.")*-->

<!--**UI**: *Note the format for documenting the UI: bold for UI elements and arrow keys for sequence. (Ex. Click **File > New > Project**.)*-->

<!--**Screenshot**: *Screenshots really help users. But don’t include too many since they’re difficult to maintain. Highlight areas you are referring to in red.*-->

<!--**No. of steps**: *Make sure the number of steps within a procedure is 10 or fewer. Seven steps is ideal. Break up long procedure logically.*-->

## Configure a new web project

Your next step is to create a web project in Visual Studio and a web app in Azure App Service. In this section of the tutorial you configure the new web project. 

1. Open Visual Studio 2015.

2. Click **File > New > Project**.

3. In the **New Project** dialog box, click **Visual C# > Web > ASP.NET Web Application**.

4. Make sure that **.NET Framework 4.5.2** is selected as the target framework.

5.  [Azure Application Insights](../application-insights/app-insights-overview.md) monitors your web app for availability, performance, and usage. The **Add Application Insights to Project** check box is selected by default the first time you create a web project after installing Visual Studio. Clear the check box if it's selected but you don't want to try Application Insights.

6. Name the application **MyExample**, and then click **OK**.

	![New Project dialog box](./media/web-sites-dotnet-get-started/GS13newprojdb.png)

7. In the **New ASP.NET Project** dialog box, select the **MVC** template, and then click **Change Authentication**.

	For this tutorial, you deploy an ASP.NET MVC web project. If you want to learn how to deploy an ASP.NET Web API project, see the [Next steps](#next-steps) section. 

	![New ASP.NET Project dialog box](./media/web-sites-dotnet-get-started/GS13changeauth.png)

8. In the **Change Authentication** dialog box, click **No Authentication**, and then click **OK**.

	![No Authentication](./media/web-sites-dotnet-get-started/GS13noauth.png)

	For this getting-started tutorial you're deploying a simple app that doesn't do user log-in.

9. In the **Microsoft Azure** section of the **New ASP.NET Project** dialog box, make sure that **Host in the cloud** is selected and that **App Service** is selected in the drop-down list, and then click **OK**.

	![New ASP.NET Project dialog box](./media/web-sites-dotnet-get-started/GS13newaspnetprojdb.png)

	These settings direct Visual Studio to create an Azure web app for your web project.

## Configure Azure resources for a new web app

Now you tell Visual Studio about the Azure resources that you want it to create.

5. In the **Create App Service** dialog, click **Add an account**, and then sign in to Azure with the ID and password of the account that you use to manage your Azure subscription.

	![Sign in to Azure](./media/web-sites-dotnet-get-started/configuresitesettings.png)

	If you already signed in earlier on the same computer, you might not see the **Add an account** button. In that case, you can skip this step or you might need to reenter your credentials.
 
3. Enter a **Web App Name** that is unique in the *azurewebsites.net* domain. For example, you can name it MyExample with numbers to the right to make it unique, such as MyExample810. If a default web name is created for you, it will be unique and you can use that.

	If someone else has already used the name that you enter, you see a red exclamation mark to the right instead of a green check mark, and you have to enter a different name.

	The URL for your application is this name plus *.azurewebsites.net*. For example, if the name is `MyExample810`, the URL is `myexample810.azurewebsites.net`.

	You can also use a custom domain with an Azure web app. For more information, see [Configure a custom domain name in Azure App Service](web-sites-custom-domain-name.md).

6. Click the **New** button next to the **Resource Group** box, and then enter "MyExample" or another name if you prefer. 

	![Create App Service dialog](./media/web-sites-dotnet-get-started/rgcreate.png)

	A resource group is a collection of Azure resources such as web apps, databases, and VMs. For a tutorial, it's generally best to create a new resource group because that makes it easy to delete in one step any Azure resources that you create for the tutorial. For more information, see [Azure Resource Manager overview](../resource-group-overview.md).

4. Click the **New** button next to the **App Service Plan** drop-down.

	![Create App Service dialog](./media/web-sites-dotnet-get-started/createasplan.png)

	The **Configure App Service Plan** dialog appears.

	![Configure App Service dialog](./media/web-sites-dotnet-get-started/configasp.png)

	In the following steps, you configure an App Service plan for the new resource group. An App Service plan specifies the compute resources that your web app runs on. For example, if you choose the free tier, your API app runs on shared VMs, while for some paid tiers it runs on dedicated VMs. For more information, see [App Service plans overview](../app-service/azure-web-sites-web-hosting-plans-in-depth-overview.md).

5. In the **Configure App Service Plan** dialog, enter "MyExamplePlan" or another name if you prefer.

5. In the **Location** drop-down list, choose the location that is closest to you.

	This setting specifies which Azure datacenter your app will run in. For this tutorial, you can select any region and it won't make a noticeable difference. But for a production app, you want your server to be as close as possible to the clients that are accessing it, to minimize [latency](http://www.bing.com/search?q=web%20latency%20introduction&qs=n&form=QBRE&pq=web%20latency%20introduction&sc=1-24&sp=-1&sk=&cvid=eefff99dfc864d25a75a83740f1e0090).

5. In the **Size** drop-down, click **Free**.

	For this tutorial, The free pricing tier will provide good enough performance.

6. In the **Configure App Service Plan** dialog, click **OK**.

7. In the **Create App Service** dialog box, click **Create**.

## Visual Studio creates the project and web app

In a short time, usually less than a minute, Visual Studio creates the web project and the web app.  

The **Solution Explorer** window shows the files and folders in the new project.

![Solution Explorer](./media/web-sites-dotnet-get-started/solutionexplorer.png)

The **Azure App Service Activity** window shows that the web app has been created.

![Web app created in Azure App Service Activity window](./media/web-sites-dotnet-get-started/GS13sitecreated1.png)

The **Cloud Explorer** window lets you view and manage Azure resources, including the new web app that you just created.

![Web app created in Cloud Explorer](./media/web-sites-dotnet-get-started/siteinse.png)
	
## Deploy the web project to the Azure web app

In this section, you deploy the web project to the web app.

1. In **Solution Explorer**, right-click the project, and choose **Publish**.

	![Choose Publish in Visual Studio menu](./media/web-sites-dotnet-get-started/choosepublish.png)

	In a few seconds, the **Publish Web** wizard appears. The wizard opens to a *publish profile* that has settings for deploying the web project to the new web app.

	The publish profile includes a user name and password for deployment.  These credentials have been generated for you, and you don't have to enter them. The password is encrypted in a hidden user-specific file in the `Properties\PublishProfiles` folder.
 
8. On the **Connection** tab of the **Publish Web** wizard, click **Next**.

	![Click Next on Connection tab of Publish Web wizard](./media/web-sites-dotnet-get-started/GS13ValidateConnection.png)

	Next is the **Settings** tab. Here you can change the build configuration to deploy a debug build for [remote debugging](../app-service-web/web-sites-dotnet-troubleshoot-visual-studio.md#remotedebug). The tab also offers several [File Publish Options](https://msdn.microsoft.com/library/dd465337.aspx#Anchor_2).

10. On the **Settings** tab, click **Next**.

	![Settings tab of Publish Web wizard](./media/web-sites-dotnet-get-started/GS13SettingsTab.png)

	The **Preview** tab is next. Here you have an opportunity to see what files are going to be copied from your project to the API app. When you're deploying a project to an API app that you already deployed to earlier, only changed files are copied. If you want to see a list of what will be copied, you can click the **Start Preview** button.

11. On the **Preview** tab, click **Publish**.

	![Preview tab of Publish Web wizard](./media/web-sites-dotnet-get-started/GS13previewoutput.png)

	When you click **Publish**, Visual Studio begins the process of copying the files to the Azure server. This may take a minute or two.

	The **Output** and **Azure App Service Activity** windows show what deployment actions were taken and report successful completion of the deployment.

	![Visual Studio Output window reporting successful deployment](./media/web-sites-dotnet-get-started/PublishOutput.png)

	Upon successful deployment, the default browser automatically opens to the URL of the deployed web app, and the application that you created is now running in the cloud. The URL in the browser address bar shows that the web app is loaded from the Internet.

	![Web app running in Azure](./media/web-sites-dotnet-get-started/GS13deployedsite.png)

	> [AZURE.TIP] You can enable the **Web One Click Publish** toolbar for quick deployment. Click **View > Toolbars**, and then select **Web One Click Publish**. You can use the toolbar to select a profile, click a button to publish, or click a button to open the **Publish Web** wizard.
	> ![Web One Click Publish Toolbar](./media/web-sites-dotnet-get-started/weboneclickpublish.png)

<!--**Next steps**: *Reiterate what users have done, and give them interesting and useful next steps so they want to go on.*-->

## Next steps

In this tutorial, you've seen how to create a simple web application and deploy it to an Azure web app. Here are some related topics and resources for learning more about Azure App Service:

* Monitor and manage your web app in the [Azure portal](https://portal.azure.com/). 

	For more information, see [an overview of the Azure portal](/services/management-portal/) and [Configure web apps in Azure App Service](web-sites-configure.md).

* Deploy an existing web project to a new web app, using Visual Studio

	Right-click the project in **Solution Explorer**, and then click **Publish**. Choose **Microsoft Azure App Service** as the publish target, and then click **New**. The dialogs are then the same as what you've seen in this tutorial.

* Deploy a web project from source control

	For information about [automating deployment](http://www.asp.net/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/continuous-integration-and-continuous-delivery) from a [source control system](http://www.asp.net/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control), see [Get started with web apps in Azure App Service](app-service-web-get-started.md) and [How to deploy an Azure web app](web-sites-deploy.md).

* Deploy an ASP.NET Web API to an API app in Azure App Service

	You've seen how to create an instance of Azure App Service that is mainly intended to host a website. App Service also offers features for hosting Web APIs, such as CORS support and API metadata support for client code generation. You can use API features in a web app, but if you mainly want to host an API in an instance of App Service, an **API app** would be a better choice. For more information, see [Get started with API Apps and ASP.NET in Azure App Service](../app-service-api/app-service-api-dotnet-get-started.md). 

* Add a custom domain name and SSL

	For information about how to use SSL and your own domain (for example, www.contoso.com instead of contoso.azurewebsites.net), see the following resources:

	* [Configure a custom domain name in Azure App Service](web-sites-custom-domain-name.md)
	* [Enable HTTPS for an Azure website](web-sites-configure-ssl-certificate.md)

* Delete the resource group that contains your web app and any related Azure resources when you're done with them.

	For information about how to work with resource groups in the Azure portal, see [Deploy resources with Resource Manager templates and Azure portal](../resource-group-template-deploy-portal.md).   

*	For more examples of creating an ASP.NET Web App in App Service, see [Create and deploy an ASP.NET web app in Azure App Service](https://github.com/Microsoft/HealthClinic.biz/wiki/Create-and-deploy-an-ASP.NET-web-app-in-Azure-App-Service) from the [HealthClinic.biz](https://github.com/Microsoft/HealthClinic.biz) 2015 Connect [demo](https://blogs.msdn.microsoft.com/visualstudio/2015/12/08/connectdemos-2015-healthclinic-biz/). For more quickstarts from the HealthClinic.biz demo, see [Azure Developer Tools Quickstarts](https://github.com/Microsoft/HealthClinic.biz/wiki/Azure-Developer-Tools-Quickstarts).