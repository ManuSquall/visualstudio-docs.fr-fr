---
title: Publier sur App Service sur Linux
description: En savoir plus sur les méthodes de publication d’ASP.NET Core apps sur Azure App Service Linux à l’aide de conteneurs, y compris des options continues et ponctuelles.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 27002d9360d36330249167b2cc8b75b7cd832135
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815631"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publier une application web ASP.NET Core sur App Service sur Linux à l’aide de Visual Studio

À compter de Visual Studio 2017 version 15.7, vous pouvez publier des applications ASP.NET Core sur Azure App Service Linux (avec des conteneurs) en utilisant une des méthodes suivantes.

* Pour le déploiement continu (ou automatisé) d’applications, utilisez Azure DevOps avec [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true).

* Pour un déploiement ponctuel (ou manuel) d’applications, utilisez l’outil **Publier** de Visual Studio pour publier des applications ASP.NET Core sur App Service pour Linux (avec des conteneurs).

Cet article décrit comment utiliser l’outil **Publier** pour un déploiement ponctuel.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-azure-app-service-on-linux"></a>Publier sur Azure App Service sur Linux

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier** (ou utilisez l’élément de menu **Générer** > **Publier**).

    ![Commande publier dans le menu contextuel du projet dans Explorateur de solutions](../deployment/media/quickstart-publish.png "Choisir Publier")

1. Si vous avez déjà configuré des profils de publication, la fenêtre **publier** s’affiche. Sélectionnez **Nouveau**.

1. Dans la fenêtre **publier** , sélectionnez **Azure**.

    ![Choisir la cible de publication](../deployment/media/quickstart-publish-azure-new.png)

1. Sélectionnez **Azure App service (Linux)** et **suivant**.

    ![Choisir Azure App Service sur Linux](../deployment/media/quickstart-publish-linux-select-azure-service.png)

1. Connectez-vous avec votre compte Azure, si nécessaire. Sélectionnez **créer un nouveau Azure App service...**

    ![Lien pour créer une nouvelle instance de Azure App Service](../deployment/media/quickstart-publish-linux-create-new-link.png)

1. Dans la boîte de dialogue **créer un Azure App service (Linux)** , les champs nom de l' **application**, **groupe de ressources** et App service d’entrée du **plan** sont renseignés. Vous pouvez conserver ces noms ou les changer. Quand vous êtes prêt, sélectionnez **créer**.

    ![Capture d’écran de la boîte de dialogue créer un Azure App Service (Linux) avec les champs nom, abonnement, groupe de ressources et plan d’hébergement rempli.](../deployment/media/quickstart-publish-linux-create-new-dialog.png)

1. Dans la boîte de dialogue **publier** , l’instance nouvellement créée a été automatiquement sélectionnée. Lorsque vous êtes prêt, cliquez sur **Terminer**.

    ![Capture d’écran de la boîte de dialogue publier avec le service MyASpCoreWebAppOnAzure nouvellement créé sélectionné comme App Service pour la publication.](../deployment/media/quickstart-publish-linux-select-instance.png)

1. Sélectionnez **Publier**. Visual Studio déploie l’application sur votre service Azure App Service, et l’application web se charge dans votre navigateur. Le volet **Publier** des propriétés de projet montre l’URL du site et d’autres détails.

    ![Volet de propriétés Publier affichant un récapitulatif du profil](../deployment/media/quickstart-publish-linux-summary-page.png)

## <a name="clean-up-resources"></a>Nettoyer les ressources

Au cours des étapes précédentes, vous avez créé des ressources Azure au sein d’un groupe de ressources. Si vous ne pensez pas avoir besoin de ces ressources à l’avenir, vous pouvez les supprimer en supprimant le groupe de ressources.
Dans le menu de gauche du portail Azure, cliquez sur **Groupes de ressources**, puis sur **myResourceGroup**.
Sur la page du groupe de ressources, assurez-vous que les ressources répertoriées sont bien celles que vous souhaitez supprimer.
Sélectionnez **Supprimer**, tapez **myResourceGroup** dans la zone de texte, puis sélectionnez **Supprimer**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez appris à utiliser Visual Studio afin de créer un profil de publication pour le déploiement sur App Service sur Linux. Consultez d’autres informations sur la publication sur Linux à l’aide d’Azure.

> [!div class="nextstepaction"]
> [App Service Linux](/azure/app-service/containers/app-service-linux-intro)