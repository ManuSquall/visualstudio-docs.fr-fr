---
title: Déployer un conteneur ASP.NET Core Docker au service d’applications Azure (fr) Microsoft Docs
description: Découvrez comment utiliser Visual Studio Container Tools pour déployer une application web ASP.NET Core sur Azure App Service
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 6c1d56f788294826853ad441313597255308bb39
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027291"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Déployer un conteneur ASP.NET Core au service d’applications Azure à l’aide de Visual Studio

Ce tutoriel vous guide à travers l’utilisation de Visual Studio pour publier votre application web ASP.NET Core conteneurisée à un [service d’application Azure](/azure/app-service). Azure App Service est un service approprié pour une application web à conteneur unique hébergée à Azure.

Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) avant de commencer.

## <a name="prerequisites"></a>Conditions préalables requises

Pour suivre ce tutoriel :

::: moniker range="vs-2017"
- Installer la dernière version de [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) avec la charge de travail « Développement web et ASP.NET »
::: moniker-end
::: moniker range=">=vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) avec la charge de travail *Développement ASP.NET et web*.
::: moniker-end
- Installer [Docker Desktop](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Créez une application web ASP.NET Core

La procédure suivante vous accompagne dans la création d’une application ASP.NET Core qui sera utilisée dans ce didacticiel.

::: moniker range="vs-2017"
1. Dans le menu Visual Studio, sélectionnez **Fichier > Nouveau > Projet**.
2. Sous la section **Modèles** de la boîte de dialogue **Nouveau projet**, sélectionnez **Visual C# > Web**.
3. Sélectionnez **Application web ASP.NET Core**.
4. Donnez un nom à votre nouvelle application (ou utilisez la valeur par défaut) et sélectionnez **OK**.
5. Sélectionnez **application Web**.
6. Cochez la case **Activer la prise en charge de Docker**.
7. Sélectionnez le type de conteneur **Linux** et cliquez **sur OK**. Les conteneurs Windows ne sont pas pris en charge pour être déployés dans le service d’applications Azure en tant que conteneur.
::: moniker-end
::: moniker range=">= vs-2019"
1. Dans la fenêtre de démarrage Visual Studio, choisissez **Créer un projet**.
1. Choisissez **Application web ASP.NET Core**, puis **Suivant**.
1. Donnez un nom à votre nouvelle application (ou utilisez la valeur par défaut) et choisissez **Créer**.
1. Choisissez **Application web**.
1. Indiquez si vous souhaitez ou non une prise en charge de SSL via la case à cocher **Configurer pour HTTPS**.
1. Cochez la case **Activer la prise en charge de Docker**.
1. Sélectionnez le type de conteneur et cliquez sur **Créer**. Les conteneurs Windows ne sont pas pris en charge pour être déployés dans le service d’applications Azure en tant que conteneur.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Déployez le conteneur à Azure

1. Cliquez avec le bouton droit sur votre projet dans l’**Explorateur de solutions** et choisissez **Publier**.
1. Sur le dialogue cible de publication, choisissez **App Service Linux** ou App **Service**. C’est le système d’exploitation qui hébergera le serveur web.
1. Vous ne pouvez publier que sur App Service, ou vous pouvez les publier à la fois sur App Service et Azure Container Registry (ACR). Pour publier le conteneur dans un registre des conteneurs Azure (ACR), choisissez **créer un nouveau service d’application pour les conteneurs**et cliquez sur **Publier**.

   ![Capture d’écran du dialogue publié](media/deploy-app-service/publish-app-service-linux.PNG)

   Pour ne publier que sur un service d’application Azure sans utiliser le registre des conteneurs Azure, choisissez **Créer de nouveaux**, et cliquez sur **Publier**.

1. Vérifiez que vous êtes connecté au compte associé à votre abonnement Azure, et choisissez un nom unique, un abonnement, un groupe de ressources, un plan d’hébergement et un registre des conteneurs (le cas échéant), ou acceptez les défauts.

   ![Capture d’écran des paramètres de publication](media/deploy-app-service/publish-app-service-linux2.png)

1. Choisissez **Créer**. Votre conteneur est déployé à Azure dans le groupe de ressources et le registre des conteneurs que vous avez sélectionnés. Ce processus prend un peu de temps. Une fois terminé, l’onglet **Publier** affiche des informations sur ce qui a été publié, y compris l’URL du site.

   ![Capture d’écran de l’onglet publier](media/deploy-app-service/publish-succeeded.PNG)

1. Cliquez sur le lien du site pour vérifier que votre application fonctionne comme prévu dans Azure.

   ![Capture d’écran de l’application web](media/deploy-app-service/web-application-running.png)

1. Le profil de publication est enregistré avec tous les détails que vous avez sélectionnés, tels que le groupe de ressources et le registre des conteneurs.

1. Pour vous déployer à nouveau avec le même profil de publication, utilisez le bouton **Publier,** le bouton **Publier** sur la fenêtre **d’activité Web Publish** ou cliquer à droite sur le projet dans Solution **Explorer** et choisissez **l’élément Publier** sur le menu contextuelle.

## <a name="view-container-settings"></a>Afficher les paramètres des conteneurs

Dans le [portail Azure,](https://portal.azure.com)vous pouvez ouvrir votre service App déployé.

Vous pouvez afficher les paramètres de votre service d’application déployé en ouvrant le menu*des paramètres de conteneurs* (lorsque vous utilisez visual Studio 2019 version 16.4 ou plus tard).

![Capture d’écran du menu Paramètres de conteneurs dans le portail Azure](media/deploy-app-service/container-settings-menu.png)

De là, vous pouvez afficher les informations du conteneur, afficher ou télécharger des journaux, ou configurer un déploiement continu. Voir [Azure App Service Continuous Deployment CI/CD](/azure/app-service/containers/app-service-linux-ci-cd).

## <a name="clean-up-resources"></a>Nettoyer les ressources

Pour supprimer toutes les ressources Azure associées à ce tutoriel, supprimez le groupe de ressources à l’aide du [portail Azure](https://portal.azure.com). Pour trouver le groupe de ressources associé à une application Web publiée, choisissez **View** > **Other Windows** > **Web Publish Activity,** puis choisissez l’icône de l’engrenage. **L’onglet Publier** s’ouvre, qui contient le groupe de ressources.

Dans le portail Azure, choisissez **les groupes de ressources,** sélectionnez le groupe de ressources pour ouvrir sa page de détails. Vérifiez qu’il s’agit du bon groupe de ressources, puis choisissez Supprimer le **groupe de ressources**, tapez le nom, et choisissez **Supprimer**.

## <a name="next-steps"></a>Étapes suivantes

En savoir plus sur [Azure App Service Linux](/azure/app-service/containers/app-service-linux-intro).

## <a name="see-also"></a>Voir aussi

[Déployer sur Azure Container Registry](hosting-web-apps-in-docker.md)