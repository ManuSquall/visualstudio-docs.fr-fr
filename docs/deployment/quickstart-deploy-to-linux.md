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
ms.openlocfilehash: 9f79cef595b3a58426b596fc1019c59b801a02d5
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252360"
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

## <a name="next-steps"></a>Étapes suivantes

Dans ce démarrage rapide, vous avez appris à utiliser Visual Studio pour créer un profil de publication pour le déploiement sur App Service sur Linux. Vous souhaiterez peut-être plus d’informations sur la publication sur Linux à l’aide d’Azure.

> [!div class="nextstepaction"]
> [App Service Linux](/azure/app-service/containers/app-service-linux-intro)
