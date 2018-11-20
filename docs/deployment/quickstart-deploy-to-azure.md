---
title: Publier sur Azure App Service
ms.custom: ''
ms.date: 06/22/2018
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
ms.openlocfilehash: a8de7175b33a91c310da4b3d6d9e4c05c40c3522
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341688"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publier une application web sur Azure App Service avec Visual Studio

Vous pouvez utiliser l’outil **Publier** pour publier des applications ASP.NET, ASP.NET Core, Node.js et .NET Core sur Azure App Service ou Azure App Service Linux (à l’aide de conteneurs). Pour les applications Python, suivez les étapes [Python - Publier sur Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

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

Dans les étapes précédentes, vous avez créé des ressources Azure dans un groupe de ressources. Si vous pensez ne pas avoir besoin de ces ressources à l’avenir, vous pouvez les supprimer en supprimant le groupe de ressources.
Dans le menu de gauche du portail Azure, sélectionnez **Groupes de ressources**, puis sélectionnez **myResourceGroup**.
Dans la page du groupe de ressources, vérifiez que les ressources listées sont celles que vous voulez supprimer.
Sélectionnez **Supprimer**, tapez **myResourceGroup** dans la zone de texte, puis sélectionnez **Supprimer**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez appris à utiliser Visual Studio afin de créer un profil de publication pour le déploiement sur Azure. Vous pouvez aussi configurer un profil de publication en important des paramètres de publication à partir d’Azure App Service.

> [!div class="nextstepaction"]
> [Importer des paramètres de publication et déployer sur Azure](tutorial-import-publish-settings-azure.md)
