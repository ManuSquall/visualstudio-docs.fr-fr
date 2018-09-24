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
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341688"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publier une application Web sur Azure App Service à l’aide de Visual Studio

Vous pouvez utiliser la **publier** outil pour publier des applications ASP.NET, ASP.NET Core, Node.js et .NET Core sur Azure App Service ou Azure App Service Linux (à l’aide de conteneurs). Pour les applications Python, suivez les étapes [Python - publier sur Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Publier sur Azure App Service

1. Dans l’Explorateur de solutions, cliquez sur le projet et choisissez **publier** (ou utilisez le **Build** > **publier** élément de menu).

    ![La commande Publier sur le menu contextuel du projet dans l’Explorateur de solutions](../deployment/media/quickstart-publish.png "choisissez Publier")

1. Si vous avez déjà configuré des profils de publication, le **publier** volet s’affiche, dans les cas, sélectionnez **créer nouveau profil**.

1. Dans le **choisir une cible de publication** boîte de dialogue, sélectionnez **App Service**.

    ![Choisissez Azure App Service](../deployment/media/quickstart-publish-azure.png "choisir Azure App Service")

1. Sélectionnez **Publier**. Le **créer App Service** boîte de dialogue s’affiche. Connectez-vous avec votre compte Azure, si nécessaire, puis les paramètres de service d’application par défaut remplissent les champs.

    ![Créer App Service](../deployment/media/quickstart-publish-settings-app-service.png "créer Azure App Service")

1. Sélectionnez **Créer**. Visual Studio déploie l’application sur votre Azure App Service, et l’application web se charge dans votre navigateur. Les propriétés du projet **publier** volet affiche l’URL du site et autres détails.

    ![Publier le volet des propriétés affichant un profil de résumé](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Nettoyer les ressources

Les étapes précédentes, vous avez créé des ressources Azure dans un groupe de ressources. Si vous ne pensez pas avoir besoin de ces ressources à l’avenir, vous pouvez les supprimer en supprimant le groupe de ressources.
Dans le menu de gauche dans le portail Azure, sélectionnez **groupes de ressources** , puis sélectionnez **myResourceGroup**.
Sur la page de groupe de ressources, assurez-vous que les ressources répertoriées sont ceux que vous souhaitez supprimer.
Sélectionnez **supprimer**, type **myResourceGroup** dans la zone de texte, puis sélectionnez **supprimer**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce démarrage rapide, vous avez appris à utiliser Visual Studio pour créer un profil de publication pour le déploiement vers Azure. Vous pouvez également configurer une publication profil en important les paramètres à partir d’Azure App Service de publication.

> [!div class="nextstepaction"]
> [Importer des paramètres de publication et déployer sur Azure](tutorial-import-publish-settings-azure.md)
