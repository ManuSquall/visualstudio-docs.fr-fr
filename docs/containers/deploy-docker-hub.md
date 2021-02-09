---
title: Déployer un conteneur d’ancrage ASP.NET Core sur le hub d’ancrage | Microsoft Docs
description: Découvrez comment utiliser les outils de conteneur Visual Studio pour déployer une application Web ASP.NET Core sur le hub d’ancrage
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 07/23/2019
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: e51088d135d0d2cdcc5d1bcca71f72fed8b73fd2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867657"
---
# <a name="deploy-to-docker-hub"></a>Déployer sur Docker Hub

Le hub d’ancrage fournit un service d’hébergement pratique pour vos référentiels d’images. Vous pouvez facilement effectuer un déploiement sur le hub d’ancrage manuellement à partir de Visual Studio.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Créer un compte d’ancrage et un référentiel de hub d’ancrage

[Inscrivez](https://hub.docker.com/signup) -vous pour obtenir un compte d’ancrage, si vous n’en avez pas déjà un.

Si vous n’avez pas de référentiel du hub d’ancrage, créez-en un dans le hub de l' [ancrage](https://hub.docker.com/).

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Publier l’image d’un seul projet vers le hub d’ancrage

1. Cliquez avec le bouton droit sur le nœud du projet et choisissez **publier...**. Un écran affichant les options de déploiement s’affiche.

   ![Capture d’écran des options de déploiement](media/container-tools/vs-2019/docker-container-registry.png)

1. Sélectionnez l’Container Registry de l' **ancreur**, puis choisissez **hub d’ancrage**.

   ![Capture d’écran de la boîte de dialogue publier-choisir un hub d’ancrage](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. Entrez les informations d’identification de votre ancrage.

   ![Capture d’écran de la boîte de dialogue Hub Dockr](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Si vous vous connectez à votre propre référentiel (ne faisant pas partie d’une organisation), laissez la case à cocher **publier sur un dépôt personnel** cochée. Si le référentiel est détenu par une organisation, désactivez la case à cocher, puis entrez le nom de l’organisation. Entrez votre nom d’utilisateur et votre mot de passe pour votre compte d’ancrage qui dispose des autorisations d’accès au référentiel auquel vous vous connectez, puis sélectionnez **Enregistrer**.

   Visual Studio tente de déployer votre image sur le hub d’ancrage.  En cas de réussite, l’écran de **publication** s’affiche avec l’URL de l’image du référentiel, la balise d’image, le référentiel et la configuration de build (par exemple, **Release**).

   ![Capture d’écran de l’écran de publication](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. Vous pouvez mettre à jour l’image à tout moment en cliquant sur le bouton **publier** dans cette page.  Vous pouvez modifier ou supprimer le profil en utilisant les liens sous l’URL.

## <a name="next-steps"></a>Étapes suivantes

Publiez sur [Azure Container Registry](/azure/container-registry/) en suivant les étapes décrites dans [déployer sur Azure Container Registry](hosting-web-apps-in-docker.md).

Configurez l’intégration et la livraison continues (CI/CD) avec [Azure pipelines](/azure/devops/pipelines/?view=azure-devops&preserve-view=true).

## <a name="see-also"></a>Voir aussi

[Déployer sur Azure App service](deploy-app-service.md) 
 [Outils de conteneur Visual Studio](./index.yml).