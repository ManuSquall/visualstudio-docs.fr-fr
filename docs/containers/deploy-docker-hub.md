---
title: Déployer un conteneur ASP.NET Core Docker à Docker Hub (fr) Microsoft Docs
description: Découvrez comment utiliser Visual Studio Container Tools pour déployer une application web ASP.NET Core sur Docker Hub
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 07/23/2019
ms.author: ghogen
ms.openlocfilehash: b033825bbe8facbeae3dcdee6a5b563461921522
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "73188748"
---
# <a name="deploy-to-docker-hub"></a>Déployer sur Docker Hub

Docker Hub fournit un service d’hébergement pratique pour vos dépôts d’images. Vous pouvez facilement vous déployer manuellement sur Docker Hub à partir de Visual Studio.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Créez un compte Docker et un référentiel Docker Hub

[Inscrivez-vous à](https://hub.docker.com/signup) un compte Docker, si vous n’en avez pas déjà.

Si vous n’avez pas de référentiel Docker Hub, créez-en un chez [Docker Hub](https://hub.docker.com/).

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Publier l’image d’un seul projet à Docker Hub

1. Cliquez à droite sur le nœud du projet et choisissez **Publish...**. Un écran affichant les options de déploiement apparaît.

   ![](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. Sous **Choisir une cible de publication**, choisissez Container **Registry**, puis choisissez Docker **Hub**. THe **Docker Hub** dialogue apparaît.

   ![](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Si vous vous connectez à votre propre référentiel (qui ne fait pas partie d’une organisation), laissez la case à cocher pour **publier un référentiel personnel** vérifié. Si le référentiel appartient à une organisation, effacez la case à cocher et saisissez le nom de l’organisation. Entrez votre nom d’utilisateur Docker et mot de passe pour votre compte Docker qui a les autorisations d’accéder au référentiel à laquelle vous vous connectez, puis sélectionnez **Enregistrer**.  

   Visual Studio tente de déployer votre image sur le Docker Hub.  En cas de succès, **l’écran Publier** apparaît avec l’URL de l’image du référentiel, de l’étiquette d’image, du référentiel et de la configuration de construction (par exemple, **Release**).

   ![](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. Vous pouvez mettre à jour l’image à tout moment en cliquant sur le bouton **Publier** sur cette page.  Ou, vous pouvez modifier ou supprimer le profil, en utilisant les liens sous l’URL.

## <a name="next-steps"></a>Étapes suivantes

Publier au [Registre des conteneurs Azure](/azure/container-registry/) en suivant les étapes du [Registre des conteneurs De Deploy to Azure](hosting-web-apps-in-docker.md).

Configurez l’intégration et la livraison continues (CI/CD) avec [Azure Pipelines](/azure/devops/pipelines/?view=azure-devops).

## <a name="see-also"></a>Voir aussi

[Déployer à Azure App Service](deploy-app-service.md)
[Visual Studio Container Tools](/visualstudio/containers/).