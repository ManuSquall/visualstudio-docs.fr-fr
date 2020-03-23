---
title: Déployer ASP.NET conteneur Docker au registre de l’ACR
description: Apprenez à utiliser Visual Studio Container Tools pour déployer une application web ASP.NET ou ASP.NET Core à un registre de conteneurs
author: ghogen
manager: jillfra
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: conceptual
ms.technology: vs-azure
ms.date: 03/14/2019
ms.author: ghogen
ms.openlocfilehash: cfed918633f62700f464ee5f9911fbbfc6463c36
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75916912"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Déployer un conteneur ASP.NET dans un registre de conteneurs à l’aide de Visual Studio

## <a name="overview"></a>Vue d’ensemble

Docker est un moteur de conteneur léger, semblable à certains égards à une machine virtuelle, que vous pouvez utiliser pour héberger des applications et des services.
Ce tutoriel vous guide dans l’utilisation de Visual Studio pour publier votre application en conteneur sur un [registre de conteneurs Azure](https://azure.microsoft.com/services/container-registry).

Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) avant de commencer.

## <a name="prerequisites"></a>Conditions préalables requises

Pour suivre ce tutoriel :

::: moniker range="vs-2017"
* Installer la dernière version de [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)avec la charge de travail "ASP.NET et développement web"
::: moniker-end
::: moniker range=">=vs-2019"
* Installer la dernière version de [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) avec la charge de travail "ASP.NET et développement web"
::: moniker-end
* Installer [Docker pour Windows](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Créez une application web ASP.NET Core
La procédure suivante vous accompagne dans la création d’une application ASP.NET Core qui sera utilisée dans ce didacticiel. Si vous avez déjà un projet, vous pouvez sauter cette section.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">=vs-2019"
[!INCLUDE [create-aspnet5-app](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

## <a name="publish-your-container-to-azure-container-registry"></a>Publier votre conteneur Docker sur Azure Container Registry
1. Cliquez avec le bouton droit sur votre projet dans l’**Explorateur de solutions** et choisissez **Publier**.
2. Dans la boîte de dialogue de la cible de publication, sélectionnez l’onglet **Registre de conteneurs**.
3. Choisissez **Nouveau registre de conteneurs Azure** et cliquez sur **Publier**.
4. Renseignez les valeurs souhaitées dans **Créer un registre de conteneurs Azure**.

    | Paramètre      | Valeur suggérée  | Description                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Préfixe DNS** | Nom globalement unique | Nom qui identifie uniquement votre registre de conteneurs. |
    | **Abonnement** | Choisir votre abonnement | Sélectionnez l’abonnement Azure à utiliser. |
    | **[Groupe de ressources](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nom du groupe de ressources où créer votre registre de conteneurs. Choisissez **Nouveau** pour créer un groupe de ressources.|
    | **[Sku](/azure/container-registry/container-registry-skus)** | standard | Niveau de service du registre de conteneurs  |
    | **Emplacement du registre** | Un emplacement proche de vous | Choisissez un emplacement dans une [région](https://azure.microsoft.com/regions/) près de chez vous ou près d’autres services que votre registre de conteneurs va utiliser. |

    ![Boîte de dialogue de création d’un registre de conteneurs Azure dans Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. Cliquez **sur Créer**

Vous pouvez désormais extraire le conteneur à partir du registre sur tout hôte en mesure d’exécuter des images Docker, par exemple [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="see-also"></a>Voir aussi

[Quickstart: Déployer une instance de conteneurs en Azure à l’aide de l’Azure CLI](/azure/container-instances/container-instances-quickstart)
