---
title: Déployer le conteneur d’ancrage ASP.NET dans le registre ACR
description: Découvrez comment utiliser les outils de conteneur Visual Studio pour déployer une application Web ASP.NET ou ASP.NET Core dans un registre de conteneurs
author: ghogen
manager: jillfra
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: how-to
ms.technology: vs-azure
ms.date: 03/14/2019
ms.author: ghogen
ms.openlocfilehash: 4626b64f5e733fec049d56dfe53407cc0fe31566
ms.sourcegitcommit: 2c26d6e6f2a5c56ae5102cdded7b02f2d0fd686c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88168690"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Déployer un conteneur ASP.NET dans un registre de conteneurs à l’aide de Visual Studio

## <a name="overview"></a>Vue d’ensemble

Docker est un moteur de conteneur léger, semblable à certains égards à une machine virtuelle, que vous pouvez utiliser pour héberger des applications et des services.
Ce tutoriel vous guide dans l’utilisation de Visual Studio pour publier votre application en conteneur sur un [registre de conteneurs Azure](https://azure.microsoft.com/services/container-registry).

Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) avant de commencer.

## <a name="prerequisites"></a>Prérequis

Pour suivre ce tutoriel :

::: moniker range="vs-2017"
* Installer la dernière version de [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)avec la charge de travail « développement web et ASP.net »
::: moniker-end
::: moniker range=">=vs-2019"
* Installer la dernière version de [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) avec la charge de travail « développement web et ASP.net »
::: moniker-end
* Installer [docker pour Windows](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Créez une application web ASP.NET Core

La procédure suivante vous accompagne dans la création d’une application ASP.NET Core qui sera utilisée dans ce didacticiel. Si vous disposez déjà d’un projet, vous pouvez ignorer cette section.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">=vs-2019"
[!INCLUDE [create-aspnet5-app](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

::: moniker range="vs-2017"

## <a name="publish-your-container-to-azure-container-registry"></a>Publier votre conteneur Docker sur Azure Container Registry

1. Cliquez avec le bouton droit sur votre projet dans l’**Explorateur de solutions** et choisissez **Publier**.
2. Dans la boîte de dialogue **cible de publication** , sélectionnez **Container Registry**.
3. Choisissez **Nouveau registre de conteneurs Azure** et cliquez sur **Publier**.
4. Renseignez les valeurs souhaitées dans **Créer un registre de conteneurs Azure**.

    | Paramètre      | Valeur suggérée  | Description                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Préfixe DNS** | Nom global unique | Nom qui identifie uniquement votre registre de conteneurs. |
    | **Abonnement** | Choisir votre abonnement | Sélectionnez l’abonnement Azure à utiliser. |
    | **[Groupe de ressources](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nom du groupe de ressources où créer votre registre de conteneurs. Choisissez **Nouveau** pour créer un groupe de ressources.|
    | **[PAIRE](/azure/container-registry/container-registry-skus)** | Standard | Niveau de service du registre de conteneurs  |
    | **Emplacement du registre** | Un emplacement proche de vous | Choisissez un emplacement dans une [région](https://azure.microsoft.com/regions/) près de chez vous ou près d’autres services que votre registre de conteneurs va utiliser. |

    ![Boîte de dialogue de création d’un registre de conteneurs Azure dans Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. Cliquez sur **Créer**
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="publish-your-container-to-azure-container-registry"></a>Publier votre conteneur Docker sur Azure Container Registry
1. Cliquez avec le bouton droit sur votre projet dans l’**Explorateur de solutions** et choisissez **Publier**.
2. Dans la boîte de dialogue **publier** , sélectionnez **ancrer Container Registry**.

   ![Capture d’écran de la boîte de dialogue publier-choisir un ancrage Container Registry](media/container-tools/vs-2019/docker-container-registry.png)

3. Choisissez **créer un Azure Container Registry**.
 
   ![Capture d’écran de la boîte de dialogue publier : choisissez créer un nouveau Azure Container Registry](media/container-tools/vs-2019/select-existing-or-create-new-azure-container-registry.png)

4. Renseignez les valeurs souhaitées dans la **Azure Container Registry** écran.

    | Paramètre      | Valeur suggérée  | Description                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Préfixe DNS** | Nom global unique | Nom qui identifie uniquement votre registre de conteneurs. |
    | **Abonnement** | Choisir votre abonnement | Sélectionnez l’abonnement Azure à utiliser. |
    | **[Groupe de ressources](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nom du groupe de ressources où créer votre registre de conteneurs. Choisissez **Nouveau** pour créer un groupe de ressources.|
    | **[PAIRE](/azure/container-registry/container-registry-skus)** | Standard | Niveau de service du registre de conteneurs  |
    | **Emplacement du registre** | Un emplacement proche de vous | Choisissez un emplacement dans une [région](https://azure.microsoft.com/regions/) près de chez vous ou près d’autres services que votre registre de conteneurs va utiliser. |

    ![Boîte de dialogue de création d’un registre de conteneurs Azure dans Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png)

5. Cliquez sur **Créer**.

6. Choisissez **Terminer** pour terminer le processus.
::: moniker-end

Vous pouvez désormais extraire le conteneur à partir du registre sur tout hôte en mesure d’exécuter des images Docker, par exemple [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="see-also"></a>Voir aussi

[Démarrage rapide : déployer une instance de conteneur dans Azure à l’aide du Azure CLI](/azure/container-instances/container-instances-quickstart)
