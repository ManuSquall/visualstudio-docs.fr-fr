---
title: Publier sur Azure App Service - Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 11/22/2017
ms.technology:
- vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: d6de76a3f3bd781ec8cd798eef87cce7acd01e69
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="publish-an-aspnet-or-aspnet-core-app-to-azure-app-service-using-visual-studio"></a>Publier une application ASP.NET ou ASP.NET Core pour le Service d’applications Azure à l’aide de Visual Studio

Vous pouvez utiliser la **publier** outil pour publier des applications ASP.NET, ASP.NET Core, Python, Node.js et .NET Core pour le Service d’applications Azure.

Si vous n’avez pas déjà un compte Azure, vous pouvez [Inscrivez-vous ici](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="create-a-new-project"></a>Créer un nouveau projet 

1. Dans Visual Studio, sélectionnez **Fichier > Nouveau projet**.

1. Sous **Visual C#** ou **Visual Basic**, choisissez **Web**, puis dans le volet central, choisissez soit **ASP.NET Web Applications (.NET Framework)**ou (c# uniquement) **Application ASP.NET Core Web**, puis cliquez sur **OK**.

1. Choisissez **MVC**, assurez-vous que **aucune authentification** est sélectionné, puis cliquez sur **OK**.

1. Tapez un nom tel que **MyWebApp** et cliquez sur **OK**.

    Visual Studio crée le projet.

1. Choisissez **Générer > Générer la Solution** pour générer le projet.

## <a name="publish-to-azure-app-service"></a>Publier sur Azure App Service

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier**.

    ![Choisissez publier](../deployment/media/quickstart-publish-aspnet.png "choisissez Publier")

1. Dans le **publier** volet, choisissez **Microsoft Azure App Service**.

    ![Choisissez le Service d’applications Azure](../deployment/media/quickstart-publish-azure.png "choisissez Azure App Service")

1. Cliquez sur **Publier**.

    Le **créer un Service application** boîte de dialogue s’affiche.

    ![Créer le Service d’applications](../deployment/media/quickstart-publish-settings-app-service.png "créer Azure App Service")
    
1. Si vous n’êtes pas connecté à Visual Studio, connectez-vous, puis les paramètres de service d’application par défaut pour remplir les champs.

    Le profil de paramètres ouvre la boîte de dialogue de publication.

    ![Choisissez le dossier](../deployment/media/quickstart-publish-settings-web.png "dossier")

    Dans cette boîte de dialogue, vous pouvez sélectionner l’abonnement que vous utilisez, sélectionnez ou créez un groupe de ressources Azure, un etc.

1. Cliquez sur **Créer**.

    Visual Studio déploie l’application sur votre Service d’applications Azure, et l’application web est chargé dans votre navigateur.

    Dans le résumé de la **publier** volet, vous voyez l’URL du Site pour le nouveau Service d’application Azure.

## <a name="next-steps"></a>Étapes suivantes

- [Déployer une application ASP.NET Core dans Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- [Déploiement continu d’ASP.NET Core sur Azure avec Git](/aspnet/core/publishing/azure-continuous-deployment)
