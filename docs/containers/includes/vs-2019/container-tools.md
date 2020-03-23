---
title: Outils de studio visuel pour Docker avec ASP.NET
author: ghogen
description: Apprenez à utiliser Visual Studio 2019 outillage et Docker pour Windows
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 3869cf025b4ed0e744a7fea929aac38acb7dd816
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76922980"
---
Avec Visual Studio, vous pouvez facilement les construire, déboguer et exécuter des applications .NET, ASP.NET et ASP.NET Core et les publier au Registre des conteneurs Azure (ACR), Docker Hub, Azure App Service ou votre propre registre des conteneurs. Dans cet article, nous publierons une application ASP.NET Core à ACR.

## <a name="prerequisites"></a>Conditions préalables requises

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) avec la charge de travail **Développement web**, **Outils Azure** et/ou la charge de travail **Développement multiplateforme .NET Core** installée
* [.NET Core Development Tools](https://dotnet.microsoft.com/download/dotnet-core/) for development for development with .NET Core (en anglais)
* Pour publier sur Azure Container Registry, un abonnement Azure. [Inscrivez-vous à un essai gratuit](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="installation-and-setup"></a>Installation et configuration

Pour l’installation Docker, passez d’abord en revue les informations de [Docker Desktop pour Windows: Ce qu’il faut savoir avant d’installer](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install). Installez ensuite [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Ajouter un projet à un conteneur Docker

1. Créez un nouveau projet à l’aide du modèle **d’application Web ASP.NET Core** ou si vous souhaitez utiliser le cadre .NET au lieu de .NET Core, choisissez **ASP.NET application Web (.NET Framework)**.
1. Sélectionnez **l’application Web**et assurez-vous que la case à cocher **De support Enable Docker** est sélectionnée.

   ![Case Activer la prise en charge de Docker](../../media/container-tools/vs-2019/create-new-web-application.PNG)

   La capture d’écran montre .NET Core; si vous utilisez .NET Framework, il semble un peu différent.

1. Sélectionnez le type de conteneur souhaité (Windows ou Linux) et cliquez sur **Créer**.

## <a name="dockerfile-overview"></a>Vue d’ensemble du fichier Dockerfile

Un *fichier Docker*, la recette permettant de créer une image Docker finale, est créé dans le projet. Consultez les [Informations de référence sur Dockerfile](https://docs.docker.com/engine/reference/builder/) pour comprendre les commandes qu’il contient.

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM microsoft/dotnet:2.2-sdk-stretch AS build
WORKDIR /src
COPY ["HelloDockerTools/HelloDockerTools.csproj", "HelloDockerTools/"]
RUN dotnet restore "HelloDockerTools/HelloDockerTools.csproj"
COPY . .
WORKDIR "/src/HelloDockerTools"
RUN dotnet build "HelloDockerTools.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "HelloDockerTools.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

Le *Dockerfile* précédent est basé sur l’image [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/). Il comprend des instructions pour modifier l’image de base en générant votre projet et en l’ajoutant au conteneur. Si vous utilisez le cadre .NET, l’image de base sera différente.

Quand la case **Configurer pour HTTPS** de la boîte de dialogue du nouveau projet est cochée, le fichier *Dockerfile* expose deux ports. Un port est utilisé pour le trafic HTTP tandis que l’autre est utilisé pour HTTPS. Si la case n’est pas cochée, un seul port (80) est exposé pour le trafic HTTP.

## <a name="debug"></a>Débogage

Sélectionnez **Docker** dans la liste déroulante de débogage dans la barre d’outils et démarrez le débogage de l’application. Vous pouvez être amené à voir s’afficher un message vous invitant à approuver un certificat. Choisissez d’approuver le certificat pour continuer.

L’option **Outil conteneur** dans la fenêtre **Sortie** indique les actions en cours. La première fois, il peut prendre un certain temps pour télécharger l’image de base, mais il est beaucoup plus rapide sur les pistes suivantes.

## <a name="containers-window"></a>Fenêtre de conteneurs

Si vous avez Visual Studio 2019 version 16.4 ou plus tard, vous pouvez utiliser la fenêtre **Containers** pour afficher les conteneurs en marche sur votre machine, ainsi que les images que vous avez disponibles.

Ouvrez la fenêtre **Containers** en utilisant la boîte de recherche dans l’IDE (appuyez sur **Ctrl**+**Q** pour l’utiliser), tapez, `container`et choisissez la fenêtre **Conteneurs** de la liste.

Vous pouvez monter la fenêtre **Containers** dans un endroit pratique, comme en dessous de l’éditeur, en la déplaçant et en suivant les guides de placement de fenêtre.

Dans la fenêtre, trouvez votre conteneur et franchissez chaque onglet pour afficher les variables de l’environnement, les cartes portuaires, les journaux et le système de fichiers.

![Capture d’écran de la fenêtre Des conteneurs](../../media/overview/vs-2019/container-tools-window.png)

Pour plus d’informations, voir [Voir et diagnostiquer les contenants et les images dans Visual Studio](../../view-and-diagnose-containers.md).

## <a name="publish-docker-images"></a>Publier des images Docker

Une fois le cycle de développement et de débogage de l’application effectué, vous pouvez créer une image de production de l’application.

1. Changez la liste déroulante de configuration en **Release** et générez l’application.
1. Cliquez avec le bouton droit sur votre projet dans l’**Explorateur de solutions** et choisissez **Publier**.
1. Dans la boîte de dialogue de la cible de publication, sélectionnez l’onglet **Registre de conteneurs**.
1. Choisissez **Créer un registre de conteneurs Azure**, puis cliquez sur **Publier**.
1. Renseignez les valeurs souhaitées dans **Créer un registre de conteneurs Azure**.

    | Paramètre      | Valeur suggérée  | Description                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Préfixe DNS** | Nom globalement unique | Nom qui identifie uniquement votre registre de conteneurs. |
    | **Abonnement** | Choisir votre abonnement | Sélectionnez l’abonnement Azure à utiliser. |
    | **[Groupe de ressources](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nom du groupe de ressources où créer votre registre de conteneurs. Choisissez **Nouveau** pour créer un groupe de ressources.|
    | **[Sku](/azure/container-registry/container-registry-skus)** | standard | Niveau de service du registre de conteneurs  |
    | **Emplacement du registre** | Un emplacement proche de vous | Choisissez un emplacement dans une [région](https://azure.microsoft.com/regions/) près de chez vous ou près d’autres services que votre registre de conteneurs va utiliser. |

    ![Boîte de dialogue de création d’un registre de conteneurs Azure dans Visual Studio][0]

1. Cliquez **sur Créer**

   ![Capture d’écran affichant la réussite de la publication](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez désormais extraire le conteneur à partir du registre sur tout hôte en mesure d’exécuter des images Docker, par exemple [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
