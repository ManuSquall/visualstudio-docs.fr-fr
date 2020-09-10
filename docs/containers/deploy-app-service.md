---
title: Déployer un conteneur ASP.NET Core sur Azure App Service
description: Découvrez comment utiliser les outils de conteneur Visual Studio pour déployer une application Web ASP.NET Core dans un conteneur d’ancrage sur Azure App Service
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: e3a0742daa1f5e6e6510f5fa5d7f56d76c1eb4da
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741874"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Déployer un conteneur ASP.NET Core sur Azure App Service à l’aide de Visual Studio

Ce didacticiel vous guide tout au long de l’utilisation de Visual Studio pour publier votre application Web ASP.NET Core en conteneur sur une [Azure App service](/azure/app-service). Azure App Service est un service approprié pour une application Web à conteneur unique hébergée dans Azure.

Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) avant de commencer.

## <a name="prerequisites"></a>Prérequis

Pour suivre ce tutoriel :

::: moniker range="vs-2017"
- Installer la dernière version de [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) avec la charge de travail « Développement web et ASP.NET »
::: moniker-end
::: moniker range=">=vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) avec la charge de travail *Développement ASP.NET et web*.
::: moniker-end
- Installer le Bureau de l' [ancrage](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Créez une application web ASP.NET Core

La procédure suivante vous accompagne dans la création d’une application ASP.NET Core qui sera utilisée dans ce didacticiel.

::: moniker range="vs-2017"
1. Dans le menu Visual Studio, sélectionnez **Fichier > Nouveau > Projet**.
2. Sous la section **Modèles** de la boîte de dialogue **Nouveau projet**, sélectionnez **Visual C# > Web**.
3. Sélectionnez **Application web ASP.NET Core**.
4. Donnez un nom à votre nouvelle application (ou utilisez la valeur par défaut) et sélectionnez **OK**.
5. Sélectionnez **application Web**.
6. Cochez la case **Activer la prise en charge de Docker**.
7. Sélectionnez le type de conteneur **Linux** , puis cliquez sur **OK**. Les conteneurs Windows ne sont pas pris en charge pour le déploiement sur Azure App Service en tant que conteneur.
::: moniker-end
::: moniker range=">= vs-2019"
1. Dans la fenêtre de démarrage Visual Studio, choisissez **Créer un projet**.
1. Choisissez **Application web ASP.NET Core**, puis **Suivant**.
1. Donnez un nom à votre nouvelle application (ou utilisez la valeur par défaut) et choisissez **Créer**.
1. Choisissez **Application web**.
1. Indiquez si vous souhaitez ou non une prise en charge de SSL via la case à cocher **Configurer pour HTTPS**.
1. Cochez la case **Activer la prise en charge de Docker**.
1. Sélectionnez le type de conteneur, puis cliquez sur **créer**.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Déployer le conteneur sur Azure

::: moniker range="vs-2017"

1. Cliquez avec le bouton droit sur votre projet dans l’**Explorateur de solutions** et choisissez **Publier**.
1. Dans la boîte de dialogue cible de publication, choisissez **app service Linux** ou **app service**. Il s’agit du système d’exploitation qui hébergera le serveur Web.
1. Vous pouvez publier uniquement sur App Service, ou vous pouvez publier sur App Service et Azure Container Registry (ACR). Pour publier le conteneur dans une Azure Container Registry (ACR), choisissez **créer un nouveau App service pour conteneurs**, puis cliquez sur **publier**.

   ![Capture d’écran de la boîte de dialogue publier](media/deploy-app-service/publish-app-service-linux.PNG)

   Pour publier uniquement sur un Azure App Service sans utiliser Azure Container Registry, choisissez **créer nouveau**, puis cliquez sur **publier**.

1. Vérifiez que vous êtes connecté avec le compte associé à votre abonnement Azure, puis choisissez un nom unique, un abonnement, un groupe de ressources, un plan d’hébergement et un registre de conteneurs (le cas échéant), ou acceptez les valeurs par défaut.

   ![Capture d’écran des paramètres de publication](media/deploy-app-service/publish-app-service-linux2.png)

1. Choisissez **Créer**. Votre conteneur est déployé sur Azure dans le groupe de ressources et le registre de conteneurs que vous avez sélectionnés. Ce processus prend un peu de temps. Une fois l’opération terminée, l’onglet **publier** affiche des informations sur ce qui a été publié, y compris l’URL du site.

   ![Capture d’écran de l’onglet publier](media/deploy-app-service/publish-succeeded.PNG)

1. Cliquez sur le lien de site pour vérifier que votre application fonctionne comme prévu dans Azure.

   ![Capture d’écran de l’application Web](media/deploy-app-service/web-application-running.png)

1. Le profil de publication est enregistré avec tous les détails que vous avez sélectionnés, tels que le groupe de ressources et le registre de conteneurs.

1. Pour effectuer un nouveau déploiement avec le même profil de publication, utilisez le bouton **publier** , le bouton **publier** dans la fenêtre **activité de publication Web** , ou cliquez avec le bouton droit sur le projet dans **Explorateur de solutions** et choisissez l’élément **publier** dans le menu contextuel.
:::moniker-end
:::moniker range=">=vs-2019"
1. Cliquez avec le bouton droit sur votre projet dans l’**Explorateur de solutions** et choisissez **Publier**.
1. Dans la boîte de dialogue **publier** , choisissez la cible **Azure** .

   ![Capture d’écran de l’Assistant Publication](media/deploy-app-service/publish-choices.png)

1. Sous l’onglet **cible spécifique** , choisissez la cible de déploiement appropriée, par exemple **app service (Windows)** ou **app service (Linux)**, en fonction de votre type de conteneur.

   ![Capture d’écran de l’onglet cible spécifique de l’Assistant Publication](media/deploy-app-service/publish-app-service-windows.png)

1. Si vous n’êtes pas connecté au compte Azure approprié avec l’abonnement que vous souhaitez utiliser, connectez-vous à l’aide du bouton en haut à gauche de la fenêtre **publier** .

1. Vous pouvez utiliser un app service existant ou en créer un nouveau en cliquant sur le lien **créer un Azure App service** . Recherchez votre App service existant dans l’arborescence en développant son groupe de ressources ou modifiez le paramètre d' **affichage** en **type de ressource** pour trier par type.

   ![Capture d’écran montrant le choix d’une App Service](media/deploy-app-service/publish-app-service-windows2.png)

1. Si vous en créez un nouveau, un groupe de ressources et un service d’application seront générés dans Azure. Vous pouvez modifier les noms si vous le souhaitez, à condition qu’ils soient uniques.

   ![Capture d’écran montrant la création d’un App Service](media/deploy-app-service/publish-app-service-windows3.png)

1. Vous pouvez accepter le plan d’hébergement par défaut ou modifier le plan d’hébergement maintenant ou ultérieurement dans le Portail Azure. La valeur par défaut est `S1` (petite) dans l’une des régions prises en charge. Pour créer un plan d’hébergement, choisissez **nouveau** en regard de la liste déroulante **plan d’hébergement** . La fenêtre **plan d’hébergement** s’affiche.

   ![Capture d’écran montrant les options du plan d’hébergement](media/deploy-app-service/hosting-plan.png)

   Vous pouvez afficher les détails relatifs à ces options dans [Azure App service vue d’ensemble du plan](/azure/app-service/overview-hosting-plans).

1. Une fois que vous avez fini de sélectionner ou de créer ces ressources, choisissez **Terminer**. Votre conteneur est déployé sur Azure dans le groupe de ressources et le service d’application que vous avez sélectionnés. Ce processus prend un peu de temps. Une fois l’opération terminée, l’onglet **publier** affiche des informations sur ce qui a été publié, y compris l’URL du site.

   ![Capture d’écran de l’onglet publier](media/deploy-app-service/publish-succeeded-windows.png)

1. Cliquez sur le lien de site pour vérifier que votre application fonctionne comme prévu dans Azure.

   ![Capture d’écran de l’application Web](media/deploy-app-service/web-application-running2.png)

1. Le profil de publication est enregistré avec tous les détails que vous avez sélectionnés, tels que le groupe de ressources et App service.

1. Pour effectuer un nouveau déploiement avec le même profil de publication, utilisez le bouton **publier** , le bouton **publier** dans la fenêtre **activité de publication Web** , ou cliquez avec le bouton droit sur le projet dans **Explorateur de solutions** et choisissez l’élément **publier** dans le menu contextuel.
:::moniker-end

## <a name="view-container-settings"></a>Afficher les paramètres du conteneur

Dans le [portail Azure](https://portal.azure.com), vous pouvez ouvrir votre App service déployée.

Vous pouvez afficher les paramètres de votre App Service déployée en ouvrant le menu des **paramètres de conteneur** (lorsque vous utilisez Visual Studio 2019 version 16,4 ou ultérieure).

![Capture d’écran du menu des paramètres de conteneur dans le Portail Azure](media/deploy-app-service/container-settings-menu.png)

À partir de là, vous pouvez afficher les informations du conteneur, afficher ou télécharger des journaux ou configurer un déploiement continu. Consultez [Azure App service ci/CD de déploiement continu](/azure/app-service/containers/app-service-linux-ci-cd).

## <a name="clean-up-resources"></a>Nettoyer les ressources

Pour supprimer toutes les ressources Azure associées à ce didacticiel, supprimez le groupe de ressources à l’aide de l' [portail Azure](https://portal.azure.com). Pour rechercher le groupe de ressources associé à une application Web publiée, choisissez **Afficher**  >  **autres**  >  **activités de publication Web**Windows, puis cliquez sur l’icône d’engrenage. L’onglet **publier** s’ouvre, qui contient le groupe de ressources.

Dans la Portail Azure, choisissez **groupes de ressources**, sélectionnez le groupe de ressources pour ouvrir la page de détails correspondante. Vérifiez qu’il s’agit du groupe de ressources approprié, puis choisissez **supprimer le groupe de ressources**, tapez le nom et choisissez **supprimer**.

## <a name="next-steps"></a>Étapes suivantes

En savoir plus sur les [Azure App service](/azure/app-service/overview).

## <a name="see-also"></a>Voir aussi

[Déployer sur Azure Container Registry](hosting-web-apps-in-docker.md)