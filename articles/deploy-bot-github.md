---
title: Deploy a bot to Azure from GitHub | Microsoft Docs
description: Learn how to deploy a bot to Azure from GitHub and enable continuous deployment.
author: RobStand
ms.author: rstand
manager: rstand
ms.topic: article
ms.prod: bot-framework
ms.date: 08/04/2017
ms.reviewer: 
---

# Deploy a bot to Azure from GitHub

Azure allows continuous deployment of your Git repository to Azure.
With continuous deployment, when you change and build your bot's code, the bot will automatically deploy to Azure.
This tutorial shows you how to deploy a bot to Azure via continuous deployment from GitHub.

> [!NOTE]
> If you created a bot with the Azure Bot Service, your bot deployment was part of the Azure Bot Service bot 
> creation process.

## Prerequisites

You must have a Microsoft Azure subscription before you can deploy a bot to Azure. If you do not already have a subscription, you can register for a <a href="https://azure.microsoft.com/en-us/free/" target="_blank">free trial</a>. Additionally, the process described by this article requires <a href="https://git-scm.com/downloads" target="_blank">Git</a> and a <a href="http://github.com/" target="_blank">GitHub</a> account.

[!include[Pre-deployment considerations](~/includes/snippet-deploy-considerations.md)]

## Step 1: Get a GitHub repository

Start by <a href="https://help.GitHub.com/articles/fork-a-repo/" target="_blank">forking</a> the GitHub repository that contains the code for the bot that you want to deploy. 

> [!NOTE]
> This tutorial uses the <a href="https://GitHub.com/fuselabs/echobot" target="_blank">echobot</a> GitHub repository, which contains the Node.js code for creating a simple bot. Be sure to replace "*echobotsample*" with your bot ID in all settings and URLs that are shown in the examples.

## Step 2: Create an Azure web app

Next, log in to the <a href="http://portal.azure.com/" target="_blank">Azure Portal</a> and create an Azure web app.

![Create an Azure web app](~/media/azure-create-webapp.png)


## Step 3: Set up continuous deployment from your GitHub repository to Azure

Specify GitHub as the **Deployment Option** for your web app.
When you are asked to authorize Azure access to your GitHub repo, choose the branch from which to deploy.

![Set up continuous deployment to Azure from your GitHub repo](~/media/azure-deployment.png)

The deployment process may take a minute or two to complete.
You can verify that the deployment has completed by visiting the web app in a browser.

> [!NOTE]
> The URL of the web app will be `https://appname.azurewebsites.net`, where **appname** is the value that you specified when creating the app.
> In this example, the URL is `https://echobotsample.azurewebsites.net`.

![Hello world web app in browser](~/media/azure-browse.png)

## Step 4: Update Application settings with bot credentials

Update **Application settings** to specify values for `MICROSOFT_APP_ID` and `MICROSOFT_APP_PASSWORD` using the
values that you acquired when you [registered](~/portal-register-bot.md) the bot in the Bot Framework Portal.

> [!NOTE]
> If you have not yet registered the bot in the Bot Framework Portal, you can populate `MICROSOFT_APP_ID` and `MICROSOFT_APP_PASSWORD`
> with temporary (placeholder) values for now.
> After you register your bot, return to the Azure Portal and update these values with the **App ID** and **App Password** values that you acquire during the registration process.

![Enter your Bot Framework App ID and App Secret into Azure settings](~/media/azure-secrets.png)

## Step 5: Test the connection to your bot

[!include[Verify connection to your bot](~/includes/snippet-verify-deployment-using-emulator.md)]

[!include[Post-deployment next steps](~/includes/snippet-deploy-next-steps.md)]