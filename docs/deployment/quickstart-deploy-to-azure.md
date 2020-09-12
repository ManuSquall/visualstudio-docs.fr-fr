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
ms.openlocfilehash: 60b3d471191f58a5eb612d9942b72c9d5e90e8af
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036416"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publier une application web sur Azure App Service avec Visual Studio

Pour les applications ASP.NET, ASP.NET Core, Node.js et .NET Core, publiez sur Azure App Service ou Azure App Service Linux (avec des conteneurs) en utilisant une des méthodes suivantes.

* Pour le déploiement continu (ou automatisé) d’applications, utilisez Azure DevOps avec [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops).

* Pour le déploiement d’applications à usage unique (ou manuel), utilisez l’outil de **publication** de Visual Studio pour déployer des applications ASP.NET, ASP.NET Core, Node.js et .net Core sur Azure App Service ou [app service pour Linux](../deployment/quickstart-deploy-to-linux.md) (à l’aide de conteneurs). Pour les applications Python, suivez les étapes [Python - Publier sur Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

Cet article décrit comment utiliser l’outil **Publier** pour un déploiement ponctuel.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service-on-windows"></a>Publier sur Azure App Service sur Windows

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le nœud du projet et choisissez **publier** (ou utilisez l’élément de menu **générer**  >  **publier** ).

    ![Commande publier dans le menu contextuel du projet dans Explorateur de solutions](../deployment/media/quickstart-publish.png "Choisir Publier")

1. Si vous avez déjà configuré des profils de publication, la fenêtre **publier** s’affiche. Sélectionnez **Nouveau**.

1. Dans la fenêtre **publier** , sélectionnez **Azure**.

    ![Choisir la cible de publication](../deployment/media/quickstart-publish-azure-new.png)

1. Sélectionnez **Azure App service (Windows)** et **suivant**.

    ![Choisir Azure App Service sur Linux](../deployment/media/quickstart-publish-windows-select-azure-service.png)

1. Connectez-vous avec votre compte Azure, si nécessaire. Sélectionnez **créer un nouveau Azure App service...**

    ![Lien pour créer une nouvelle instance de Azure App Service](../deployment/media/quickstart-publish-windows-create-new-link.png)

1. Dans la boîte de dialogue **créer un Azure App service (Windows)** , le nom de l' **application**, le **groupe de ressources**et les champs d’entrée du plan de **app service** sont remplis. Vous pouvez conserver ces noms ou les changer. Quand vous êtes prêt, sélectionnez **créer**.

    ![Choisir Azure App Service](../deployment/media/quickstart-publish-windows-create-new-dialog.png)

1. Dans la boîte de dialogue **publier** , l’instance nouvellement créée a été automatiquement sélectionnée. Quand vous êtes prêt, sélectionnez **Terminer**.

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
