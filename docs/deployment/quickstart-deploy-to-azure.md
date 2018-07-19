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
ms.openlocfilehash: 7761164182188366425a81518f3d0513361b6f19
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077841"
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

## <a name="next-steps"></a>Étapes suivantes

Dans ce démarrage rapide, vous avez appris à utiliser Visual Studio pour créer un profil de publication pour le déploiement vers Azure. Vous pouvez également configurer une publication profil en important les paramètres à partir d’Azure App Service de publication.

> [!div class="nextstepaction"]
> [Importer des paramètres de publication et déployer sur Azure](tutorial-import-publish-settings-azure.md)
