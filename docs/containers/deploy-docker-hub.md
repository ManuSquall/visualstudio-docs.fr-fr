---
title: Déployer un conteneur d’ancrage ASP.NET Core sur le hub d’ancrage | Microsoft Docs
description: Découvrez comment utiliser les outils de conteneur Visual Studio pour déployer une application Web ASP.NET Core sur le hub d’ancrage
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 07/23/2019
ms.author: ghogen
ms.openlocfilehash: 18e2789af3a699dacee9a9e8c1f1846ee8622800
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283175"
---
# <a name="deploy-to-docker-hub"></a>Déployer sur Docker Hub

Le hub d’ancrage fournit un service d’hébergement pratique pour vos référentiels d’images. Vous pouvez facilement effectuer un déploiement sur le hub d’ancrage manuellement à partir de Visual Studio.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Créer un compte d’ancrage et un référentiel de hub d’ancrage

[Inscrivez](https://hub.docker.com/signup) -vous pour obtenir un compte d’ancrage, si vous n’en avez pas déjà un.

Si vous n’avez pas de référentiel du hub d’ancrage, créez-en un dans le hub de l' [ancrage](https://hub.docker.com/).

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Publier l’image d’un seul projet vers le hub d’ancrage

1. Cliquez avec le bouton droit sur le nœud du projet et choisissez **publier...**. Un écran affichant les options de déploiement s’affiche.

   ![](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. Sous **choisir une cible de publication**, choisissez **Container Registry**, puis cliquez sur **hub d’ancrage**. La boîte de dialogue **hub d’ancrage** s’affiche.

   ![](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Si vous vous connectez à votre propre référentiel (ne faisant pas partie d’une organisation), laissez la case à cocher **publier sur un dépôt personnel** cochée. Si le référentiel est détenu par une organisation, désactivez la case à cocher, puis entrez le nom de l’organisation. Entrez votre nom d’utilisateur et votre mot de passe pour votre compte d’ancrage qui dispose des autorisations d’accès au référentiel auquel vous vous connectez, puis sélectionnez **Enregistrer**.  

   Visual Studio tente de déployer votre image sur le hub d’ancrage.  En cas de réussite, l’écran de **publication** s’affiche avec l’URL de l’image du référentiel, la balise d’image, le référentiel et la configuration de build * * (par exemple, **Release**).

   ![](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. Vous pouvez mettre à jour l’image à tout moment en cliquant sur le bouton **publier** dans cette page.  Vous pouvez modifier ou supprimer le profil en utilisant les liens sous l’URL.

## <a name="next-steps"></a>Étapes suivantes

Publiez sur [Azure Container Registry](/azure/container-registry/) en suivant les étapes décrites dans [déployer sur Azure Container Registry](hosting-web-apps-in-docker.md).

Configurez l’intégration et la livraison continues (CI/CD) avec [Azure pipelines](/azure/devops/pipelines/?view=azure-devops).

## <a name="see-also"></a>Voir aussi

[Déployer sur Azure App service](deploy-app-service.md) 
 [Outils de conteneur Visual Studio](/visualstudio/containers/).