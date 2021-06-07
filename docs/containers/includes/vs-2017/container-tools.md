---
title: Outils de conteneur Visual Studio avec ASP.NET Core
author: ghogen
description: Découvrir comment utiliser les outils Visual Studio 2017 et Docker pour Windows
ms.author: ghogen
ms.date: 02/01/2019
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 53bf0d559d9737494567b079621879b97a403a95
ms.sourcegitcommit: fc05a763b59e212c86350d117a1900a1f2686ec8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2021
ms.locfileid: "111564700"
---
Avec Visual Studio, vous pouvez facilement générer, déboguer et exécuter des applications de ASP.NET Core en conteneur et les publier sur Azure Container Registry (ACR), un hub d’ancrage, Azure App Service ou votre propre registre de conteneurs. Dans cet article, nous allons effectuer la publication sur ACR.

## <a name="prerequisites"></a>Prérequis

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) avec la charge de travail **Développement web**, **Azure Tools** et/ou la charge de travail **Développement multiplateforme .NET Core**
* Pour publier sur Azure Container Registry, un abonnement Azure. [Inscrivez-vous pour un essai gratuit](https://azure.microsoft.com/free/dotnet/).

## <a name="installation-and-setup"></a>Installation et configuration

Pour l’installation de l’ordinateur d’amarrage, commencez par examiner les informations sur le [Bureau de station d’accueil Desktop pour Windows : ce que vous devez savoir avant d’installer](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install). Installez ensuite [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Ajouter un projet à un conteneur Docker

1. Dans le menu Visual Studio, sélectionnez **Fichier > Nouveau > Projet**.
1. Sous la section **Modèles** de la boîte de dialogue **Nouveau projet**, sélectionnez **Visual C# > Web**.
1. Sélectionnez **ASP.net Core application Web** ou si vous souhaitez utiliser le .NET Framework au lieu de .net Core, sélectionnez **application Web ASP.net**.
1. Donnez un nom à votre nouvelle application (ou utilisez la valeur par défaut) et sélectionnez **OK**.
1. Sélectionnez **application Web**.
1. Cochez la case **Activer la prise en charge de Docker**.

   ![Case Activer la prise en charge de Docker](../../media/container-tools/enable-docker-support.PNG)

   La capture d’écran montre .NET Core ; Si vous utilisez .NET Framework, cela semble un peu différent.

1. Sélectionnez le type de conteneur souhaité (Windows ou Linux) et cliquez sur **OK**.

## <a name="dockerfile-overview"></a>Vue d’ensemble du fichier Dockerfile

Un *fichier Docker*, la recette permettant de créer une image Docker finale, est créé dans le projet. Consultez les [Informations de référence sur Dockerfile](https://docs.docker.com/engine/reference/builder/) pour comprendre les commandes qu’il contient.

```
FROM mcr.microsoft.com/dotnet/aspnet:2.1 AS base
WORKDIR /app
EXPOSE 59518
EXPOSE 44364

FROM mcr.microsoft.com/dotnet/sdk:2.1 AS build
WORKDIR /src
COPY HelloDockerTools/HelloDockerTools.csproj HelloDockerTools/
RUN dotnet restore HelloDockerTools/HelloDockerTools.csproj
COPY . .
WORKDIR /src/HelloDockerTools
RUN dotnet build HelloDockerTools.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish HelloDockerTools.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

Le *Dockerfile* précédent est basé sur l’image [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/). Il comprend des instructions pour modifier l’image de base en générant votre projet et en l’ajoutant au conteneur. Si vous utilisez le .NET Framework, l’image de base sera différente.

Quand la case **Configurer pour HTTPS** de la boîte de dialogue du nouveau projet est cochée, le fichier *Dockerfile* expose deux ports. Un port est utilisé pour le trafic HTTP tandis que l’autre est utilisé pour HTTPS. Si la case n’est pas cochée, un seul port (80) est exposé pour le trafic HTTP.

## <a name="debug"></a>Débogage

Sélectionnez **Docker** dans la liste déroulante de débogage dans la barre d’outils et démarrez le débogage de l’application. Vous pouvez être amené à voir s’afficher un message vous invitant à approuver un certificat. Choisissez d’approuver le certificat pour continuer.

La fenêtre **Sortie** indique les actions en cours.

Ouvrez la **Console du Gestionnaire de package** à partir du menu **Outils**> Gestionnaire de package NuGet, **Console du Gestionnaire de package**.

L’image Docker obtenue de l’application est marquée avec la balise *dev*. L’image est basée sur la balise *2.1-aspnetcore-runtime* de l’image de base *microsoft/dotnet*. Exécutez la commande `docker images` dans la fenêtre **Console du Gestionnaire de package**. Les images sur la machine s’affichent :

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.1-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> L’image **dev** ne contient pas les fichiers binaires de l’application ni aucun autre contenu. En effet, les configurations **Debug** utilisent le montage de volume pour fournir l’expérience de modification et de débogage itérative. Pour créer une image de production incluant tout le contenu, utilisez la configuration **Release**.

Exécutez la commande `docker ps` dans la console du Gestionnaire de package. Notez que l’application s’exécute à l’aide du conteneur :

```console
CONTAINER ID        IMAGE                  COMMAND                   CREATED             STATUS              PORTS                   NAMES
baf9a678c88d        hellodockertools:dev   "C:\\remote_debugge..."   21 seconds ago      Up 19 seconds       0.0.0.0:37630->80/tcp   dockercompose4642749010770307127_hellodockertools_1
```

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
    | **[PAIRE](/azure/container-registry/container-registry-skus)** | Standard | Niveau de service du registre de conteneurs  |
    | **Emplacement du registre** | Un emplacement proche de vous | Choisissez un emplacement dans une [région](https://azure.microsoft.com/regions/) près de chez vous ou près d’autres services que votre registre de conteneurs va utiliser. |

    ![Boîte de dialogue de création d’un registre de conteneurs Azure dans Visual Studio][0]

1. Cliquez sur **Créer**

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez désormais extraire le conteneur à partir du registre sur tout hôte en mesure d’exécuter des images Docker, par exemple [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
