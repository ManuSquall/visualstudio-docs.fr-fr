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
ms.openlocfilehash: 842f7912d88031d720f438800ef6b54133ce05c9
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184494"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publier une application web sur Azure App Service avec Visual Studio

Pour les applications ASP.NET, ASP.NET Core, Node.js et .NET Core, publiez sur Azure App Service ou Azure App Service Linux (avec des conteneurs) en utilisant une des méthodes suivantes.

* Pour le déploiement continu (ou automatisé) d’applications, utilisez Azure DevOps avec [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops).

* Pour un déploiement ponctuel (ou manuel) d’applications, utilisez l’outil **Publier** de Visual Studio pour publier des applications ASP.NET, ASP.NET Core, Node.js et .NET Core sur Azure App Service pour Linux (avec des conteneurs). Pour les applications Python, suivez les étapes [Python - Publier sur Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

Cet article décrit comment utiliser l’outil **Publier** pour un déploiement ponctuel.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service-on-windows"></a>Publier sur Azure App Service sur Windows

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier** (ou utilisez l’élément de menu **Générer** > **Publier**).

    ![Commande publier dans le menu contextuel du projet dans Explorateur de solutions](../deployment/media/quickstart-publish.png "Choisir Publier")

1. Dans la boîte de dialogue **publier** , sélectionnez **Azure**.

    ![Choisir la cible de publication](../deployment/media/quickstart-publish-azure.png)

1. Sélectionnez * * Azure App Service (Windows) * * et **suivant**.

    ![Choisir Azure App Service sur Linux](../deployment/media/quickstart-publish-windows-select-azure-service.png)

1. Connectez-vous avec votre compte Azure, si nécessaire. Sélectionnez **créer un nouveau Azure App service...**

    ![Lien pour créer une nouvelle instance de Azure App Service](../deployment/media/quickstart-publish-windows-create-new-link.png)

1. Dans la boîte de dialogue **créer un Azure App service (Windows)** , le nom de l' **application**, le **groupe de ressources**et les champs d’entrée du plan de **app service** sont remplis. Vous pouvez conserver ces noms ou les changer. Quand vous êtes prêt, sélectionnez **créer**.

    ![Choisir Azure App Service](../deployment/media/quickstart-publish-windows-create-new-dialog.png)

1. Dans la boîte de dialogue **publier** , l’instance nouvellement créée a été automatiquement sélectionnée. Lorsque vous êtes prêt, cliquez sur **Terminer**.

    ![Choisir Azure App Service](../deployment/media/quickstart-publish-windows-select-instance.png)

1. Sélectionnez **Publier**. Visual Studio déploie l’application sur votre service Azure App Service, et l’application web se charge dans votre navigateur. Le volet **Publier** des propriétés de projet montre l’URL du site et d’autres détails.

    ![Volet de propriétés Publier affichant un récapitulatif du profil](../deployment/media/quickstart-publish-windows-summary-page.png)

## <a name="clean-up-resources"></a>Nettoyer les ressources

Au cours des étapes précédentes, vous avez créé des ressources Azure au sein d’un groupe de ressources. Si vous ne pensez pas avoir besoin de ces ressources à l’avenir, vous pouvez les supprimer en supprimant le groupe de ressources.
Dans le menu de gauche du portail Azure, cliquez sur **Groupes de ressources**, puis sur **myResourceGroup**.
Sur la page du groupe de ressources, assurez-vous que les ressources répertoriées sont bien celles que vous souhaitez supprimer.
Sélectionnez **Supprimer**, tapez **myResourceGroup** dans la zone de texte, puis sélectionnez **Supprimer**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez appris à utiliser Visual Studio afin de créer un profil de publication pour le déploiement sur Azure. Vous pouvez aussi configurer un profil de publication en important des paramètres de publication à partir d’Azure App Service.

> [!div class="nextstepaction"]
> [Importer des paramètres de publication et déployer sur Azure](tutorial-import-publish-settings-azure.md)
