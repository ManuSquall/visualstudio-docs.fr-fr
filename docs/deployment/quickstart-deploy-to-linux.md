---
title: Publier sur App Service sur Linux
ms.custom: ''
ms.date: 07/23/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: aa4afce6ef50284f1f966054e805b55c86f4daaf
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341746"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publier une application ASP.NET Core sur App Service sur Linux à l’aide de Visual Studio

Vous pouvez utiliser la **publier** outil pour publier des applications ASP.NET Core sur Azure App Service sur Linux.

Déploiement sur App Service sur Linux à l’aide du **publier** outil nécessite Visual Studio 2017 version 15.7.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Publier sur App Service sur Linux

1. Dans l’Explorateur de solutions, cliquez sur le projet et choisissez **publier** (ou utilisez le **Build** > **publier** élément de menu).

    ![La commande Publier sur le menu contextuel du projet dans l’Explorateur de solutions](../deployment/media/quickstart-publish.png "choisissez Publier")

1. Si vous avez déjà configuré des profils de publication, le **publier** volet s’affiche, dans les cas, sélectionnez **créer nouveau profil**.

1. Dans le **choisir une cible de publication** boîte de dialogue, sélectionnez **App Service Linux**.

    ![Choisissez Azure App Service](../deployment/media/quickstart-publish-linux.png "choisir Azure App Service")

1. Sélectionnez **Publier**. Le **créer App Service** boîte de dialogue s’affiche. Connectez-vous avec votre compte Azure, si nécessaire, puis les paramètres de service d’application par défaut remplissent les champs.

    ![Créer App Service](../deployment/media/quickstart-publish-settings-app-service-linux.png "créer Azure App Service")

1. Sélectionnez **Créer**. Visual Studio déploie l’application sur votre Azure App Service, et l’application web se charge dans votre navigateur. Les propriétés du projet **publier** volet affiche l’URL du site et autres détails.

    ![Publier le volet des propriétés affichant un profil de résumé](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Nettoyer les ressources

Les étapes précédentes, vous avez créé des ressources Azure dans un groupe de ressources. Si vous ne pensez pas avoir besoin de ces ressources à l’avenir, vous pouvez les supprimer en supprimant le groupe de ressources.
Dans le menu de gauche dans le portail Azure, sélectionnez **groupes de ressources** , puis sélectionnez **myResourceGroup**.
Sur la page de groupe de ressources, assurez-vous que les ressources répertoriées sont ceux que vous souhaitez supprimer.
Sélectionnez **supprimer**, type **myResourceGroup** dans la zone de texte, puis sélectionnez **supprimer**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce démarrage rapide, vous avez appris à utiliser Visual Studio pour créer un profil de publication pour le déploiement sur App Service sur Linux. Vous souhaiterez peut-être plus d’informations sur la publication sur Linux à l’aide d’Azure.

> [!div class="nextstepaction"]
> [App Service Linux](/azure/app-service/containers/app-service-linux-intro)
