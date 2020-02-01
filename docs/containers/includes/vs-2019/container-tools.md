---
title: Visual Studio Tools pour Docker avec ASP.NET
author: ghogen
description: Découvrez comment utiliser les outils Visual Studio 2019 et Docker pour Windows
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 3869cf025b4ed0e744a7fea929aac38acb7dd816
ms.sourcegitcommit: 4be64917e4224fd1fb27ba527465fca422bc7d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76922980"
---
Avec Visual Studio, vous pouvez facilement générer, déboguer et exécuter des applications .NET, ASP.NET et ASP.NET Core en conteneur, et les publier sur Azure Container Registry (ACR), sur le hub d’ancrage, Azure App Service ou sur votre propre registre de conteneurs. Dans cet article, nous allons publier une application ASP.NET Core sur ACR.

## <a name="prerequisites"></a>Prerequisites

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) avec la charge de travail **Développement web**, **Outils Azure** et/ou la charge de travail **Développement multiplateforme .NET Core** installée
* [Outils de développement .net Core](https://dotnet.microsoft.com/download/dotnet-core/) pour le développement avec .net Core
* Pour publier sur Azure Container Registry, un abonnement Azure. [Inscrivez-vous pour obtenir un essai gratuit](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="installation-and-setup"></a>Installation et configuration

Pour l’installation de l’ordinateur d’amarrage, commencez par examiner les informations sur le [Bureau de station d’accueil Desktop pour Windows : ce que vous devez savoir avant d’installer](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install). Installez ensuite [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Ajouter un projet à un conteneur Docker

1. Créez un projet à l’aide du modèle d' **application web ASP.net Core** ou si vous souhaitez utiliser le .NET Framework au lieu de .net Core, choisissez **application web ASP.net (.NET Framework)** .
1. Sélectionnez **application Web**et assurez-vous que la case **activer la prise en charge** de l’ancrage est cochée.

   ![Case Activer la prise en charge de Docker](../../media/container-tools/vs-2019/create-new-web-application.PNG)

   La capture d’écran montre .NET Core ; Si vous utilisez .NET Framework, cela semble un peu différent.

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

Le *Dockerfile* précédent est basé sur l’image [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/). Il comprend des instructions pour modifier l’image de base en générant votre projet et en l’ajoutant au conteneur. Si vous utilisez le .NET Framework, l’image de base sera différente.

Quand la case **Configurer pour HTTPS** de la boîte de dialogue du nouveau projet est cochée, le fichier *Dockerfile* expose deux ports. Un port est utilisé pour le trafic HTTP tandis que l’autre est utilisé pour HTTPS. Si la case n’est pas cochée, un seul port (80) est exposé pour le trafic HTTP.

## <a name="debug"></a>Déboguer

Sélectionnez **Docker** dans la liste déroulante de débogage dans la barre d’outils et démarrez le débogage de l’application. Vous pouvez être amené à voir s’afficher un message vous invitant à approuver un certificat. Choisissez d’approuver le certificat pour continuer.

L’option **Outil conteneur** dans la fenêtre **Sortie** indique les actions en cours. La première fois, elle peut prendre un certain temps pour télécharger l’image de base, mais elle est beaucoup plus rapide lors des exécutions suivantes.

## <a name="containers-window"></a>Fenêtre conteneurs

Si vous disposez de Visual Studio 2019 version 16,4 ou ultérieure, vous pouvez utiliser la fenêtre **conteneurs** pour afficher les conteneurs en cours d’exécution sur votre ordinateur, ainsi que les images que vous avez disponibles.

Ouvrez la fenêtre **conteneurs** à l’aide de la zone de recherche dans l’IDE (appuyez sur **CTRL**+**Q** pour l’utiliser), tapez `container`, puis choisissez la fenêtre **conteneurs** dans la liste.

Vous pouvez monter la fenêtre **conteneurs** à un emplacement pratique, tel que sous l’éditeur, en la déplaçant et en suivant les repères de positionnement de la fenêtre.

Dans la fenêtre, recherchez votre conteneur et parcourez chaque onglet pour afficher les variables d’environnement, les mappages de port, les journaux et le système de fichiers.

![Capture d’écran de la fenêtre conteneurs](../../media/overview/vs-2019/container-tools-window.png)

Pour plus d’informations, consultez [afficher et diagnostiquer des conteneurs et des images dans Visual Studio](../../view-and-diagnose-containers.md).

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
    | **Abonnement** | Choisissez votre abonnement | Abonnement Azure à utiliser. |
    | **[Groupe de ressources](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nom du groupe de ressources où créer votre registre de conteneurs. Choisissez **Nouveau** pour créer un groupe de ressources.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Niveau de service du registre de conteneurs  |
    | **Emplacement du registre** | Un emplacement proche de vous | Choisissez un emplacement dans une [région](https://azure.microsoft.com/regions/) près de chez vous ou près d’autres services que votre registre de conteneurs va utiliser. |

    ![Boîte de dialogue de création d’un registre de conteneurs Azure dans Visual Studio][0]

1. Cliquez sur **Créer**

   ![Capture d’écran affichant la réussite de la publication](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez désormais extraire le conteneur à partir du registre sur tout hôte en mesure d’exécuter des images Docker, par exemple [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
