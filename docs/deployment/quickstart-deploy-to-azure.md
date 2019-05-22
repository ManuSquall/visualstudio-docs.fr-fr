---
title: Publier sur Azure App Service
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: d1703fb5386c7b29446b621d2e83f9486e93dd3d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65679261"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publier une application web sur Azure App Service avec Visual Studio

Pour les applications ASP.NET, ASP.NET Core, Node.js et .NET Core, publiez sur Azure App Service ou Azure App Service Linux (avec des conteneurs) en utilisant une des méthodes suivantes.

* Pour le déploiement continu (ou automatisé) d’applications, utilisez Azure DevOps avec [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started-yaml?view=azdevops).

* Pour un déploiement ponctuel (ou manuel) d’applications, utilisez l’outil **Publier** de Visual Studio pour publier des applications ASP.NET, ASP.NET Core, Node.js et .NET Core sur Azure App Service pour Linux (avec des conteneurs). Pour les applications Python, suivez les étapes [Python - Publier sur Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

Cet article décrit comment utiliser l’outil **Publier** pour un déploiement ponctuel.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Publier sur Azure App Service

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier** (ou utilisez l’élément de menu **Générer** > **Publier**).

    ![Commande Publier du menu contextuel du projet dans l’Explorateur de solutions](../deployment/media/quickstart-publish.png "Choisissez Publier")

1. Si vous avez déjà configuré des profils de publication, le volet **Publier** s’affiche, dans lequel vous sélectionnez **Créer un profil**.

1. Dans la boîte de dialogue **Choisir une cible de publication**, choisissez **App Service**.

    ![Choisir Azure App Service](../deployment/media/quickstart-publish-azure.png "Choisir Azure App Service")

1. Sélectionnez **Publier**. La boîte de dialogue **Créer App Service** s’affiche. Connectez-vous avec votre compte Azure, si nécessaire, et laissez les paramètres App Service par défaut remplir les champs.

    ![Créer App Service](../deployment/media/quickstart-publish-settings-app-service.png "Créer Azure App Service")

1. Sélectionnez **Créer**. Visual Studio déploie l’application sur votre service Azure App Service, et l’application web se charge dans votre navigateur. Le volet **Publier** des propriétés de projet montre l’URL du site et d’autres détails.

    ![Volet de propriétés Publier affichant un récapitulatif du profil](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Nettoyer les ressources

Dans les étapes précédentes, vous avez créé des ressources Azure dans un groupe de ressources. Si vous pensez ne plus avoir besoin de ces ressources, vous pouvez les supprimer en supprimant le groupe de ressources.
Dans le menu de gauche du portail Azure, sélectionnez **Groupes de ressources**, puis sélectionnez **myResourceGroup**.
Dans la page du groupe de ressources, vérifiez que les ressources listées sont celles que vous voulez supprimer.
Sélectionnez **Supprimer**, tapez **myResourceGroup** dans la zone de texte, puis sélectionnez **Supprimer**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez appris à utiliser Visual Studio afin de créer un profil de publication pour le déploiement sur Azure. Vous pouvez aussi configurer un profil de publication en important des paramètres de publication à partir d’Azure App Service.

> [!div class="nextstepaction"]
> [Importer des paramètres de publication et déployer sur Azure](tutorial-import-publish-settings-azure.md)
