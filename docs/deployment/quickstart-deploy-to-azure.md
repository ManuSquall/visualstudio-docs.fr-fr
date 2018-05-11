---
title: Publier sur Azure App Service - Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 11/22/2017
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: c5c172ff3ec3033b50815efdb0b4ee293853ab1e
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="publish-an-aspnet-or-aspnet-core-app-to-azure-app-service-using-visual-studio"></a>Publier une application ASP.NET ou ASP.NET Core pour le Service d’applications Azure à l’aide de Visual Studio

Vous pouvez utiliser la **publier** outil pour publier des applications ASP.NET, ASP.NET Core, Python, Node.js et .NET Core pour le Service d’applications Azure.

Si vous n’avez pas déjà un compte Azure, vous pouvez [Inscrivez-vous ici](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="prerequisites"></a>Prérequis

* Vous devez disposer de Visual Studio 2017 installé et le **ASP.NET** et **.NET Framework** charge de travail de développement. Pour une application .NET Core, vous devez également le **.NET Core** la charge de travail.

    Si vous n’avez pas encore installé Visual Studio, installez-le gratuitement [ici](http://www.visualstudio.com).

## <a name="create-a-new-project"></a>Créer un nouveau projet 

1. Dans Visual Studio, sélectionnez **Fichier > Nouveau projet**.

1. Sous **Visual C#** ou **Visual Basic**, choisissez **Web**, puis dans le volet central, choisissez soit **ASP.NET Web Applications (.NET Framework)** ou (c# uniquement) **Application ASP.NET Core Web**, puis cliquez sur **OK**.

1. Choisissez **MVC** (ou choisissez **l’Application Web (Model-View-Controller)** pour .NET Core), assurez-vous que **aucune authentification** est sélectionné, puis cliquez sur **OK** .

1. Tapez un nom tel que **MyWebApp** et cliquez sur **OK**.

    Visual Studio crée le projet.

1. Choisissez **Générer > Générer la Solution** pour générer le projet.

## <a name="publish-to-azure-app-service"></a>Publier sur Azure App Service

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier**.

    ![Choisissez publier](../deployment/media/quickstart-publish-aspnet.png "choisissez Publier")

1. Si vous avez déjà configuré des profils de publication, le **publier** volet s’affiche. Cliquez sur **créer nouveau profil**.

1. Dans le **choisir une cible de publication** boîte de dialogue, choisissez **du Service d’applications**.

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

Dans ce démarrage rapide, vous avez appris à utiliser Visual Studio pour créer un profil de publication pour un déploiement vers Azure. Vous pouvez également configurer une publication de profil en important les paramètres à partir d’Azure App Service de publication.

> [!div class="nextstepaction"]
> [Importation des paramètres de publication et le déployer vers Azure](tutorial-import-publish-settings-azure.md)
