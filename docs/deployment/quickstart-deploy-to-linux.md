---
title: Publier sur App Service sur Linux
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 1e05862aa57c24bfa8f17d551762054278dd6e52
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806875"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publier une application web ASP.NET Core sur App Service sur Linux à l’aide de Visual Studio

À compter de Visual Studio 2017 version 15.7, vous pouvez publier des applications ASP.NET Core sur Azure App Service Linux (avec des conteneurs) en utilisant une des méthodes suivantes.

* Pour le déploiement continu (ou automatisé) d’applications, utilisez Azure DevOps avec [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops).

* Pour un déploiement ponctuel (ou manuel) d’applications, utilisez l’outil **Publier** de Visual Studio pour publier des applications ASP.NET Core sur App Service pour Linux (avec des conteneurs).

Cet article décrit comment utiliser l’outil **Publier** pour un déploiement ponctuel.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Publier sur App Service sur Linux

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier** (ou utilisez l’élément de menu **Générer** > **Publier**).

    ![Commande publier dans le menu contextuel du projet dans Explorateur de solutions](../deployment/media/quickstart-publish.png "Choisir Publier")

1. Si vous avez déjà configuré des profils de publication, le volet **Publier** s’affiche, dans lequel vous sélectionnez **Créer un profil**.

1. Dans la boîte de dialogue **Choisir une cible de publication**, choisissez **App Service Linux**.

    ![Choisir Azure App Service](../deployment/media/quickstart-publish-linux.png "Choisir Azure App Service")

1. Sélectionnez **Publier**. La boîte de dialogue **Créer App Service** s’affiche. Connectez-vous avec votre compte Azure, si nécessaire, et laissez les paramètres App Service par défaut remplir les champs.

    ![Créer App Service](../deployment/media/quickstart-publish-settings-app-service-linux.png "Créer Azure App Service")

1. Sélectionnez **Créer**. Visual Studio déploie l’application sur votre service Azure App Service, et l’application web se charge dans votre navigateur. Le volet **Publier** des propriétés de projet montre l’URL du site et d’autres détails.

    ![Volet de propriétés Publier affichant un récapitulatif du profil](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Nettoyer les ressources

Dans les étapes précédentes, vous avez créé des ressources Azure dans un groupe de ressources. Si vous pensez ne plus avoir besoin de ces ressources, vous pouvez les supprimer en supprimant le groupe de ressources.
Dans le menu de gauche du portail Azure, sélectionnez **Groupes de ressources**, puis sélectionnez **myResourceGroup**.
Dans la page du groupe de ressources, vérifiez que les ressources listées sont celles que vous voulez supprimer.
Sélectionnez **Supprimer**, tapez **myResourceGroup** dans la zone de texte, puis sélectionnez **Supprimer**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez appris à utiliser Visual Studio afin de créer un profil de publication pour le déploiement sur App Service sur Linux. Consultez d’autres informations sur la publication sur Linux à l’aide d’Azure.

> [!div class="nextstepaction"]
> [App Service Linux](/azure/app-service/containers/app-service-linux-intro)
