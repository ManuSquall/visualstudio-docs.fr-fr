---
title: Outils de conteneur Visual Studio avec ASP.NET Core et REACT. js
author: ghogen
description: Découvrir comment utiliser les outils de conteneur Visual Studio et le client Docker pour Windows
ms.author: ghogen
ms.date: 05/14/2020
ms.technology: vs-azure
ms.topic: quickstart
ms.openlocfilehash: f7dfc0aa1346c4e888f64f7cd8f23add3056c070
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84182784"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>Démarrage rapide : utiliser l’amarrage avec une application à page unique REACT dans Visual Studio

Avec Visual Studio, vous pouvez facilement générer, déboguer et exécuter des applications ASP.NET Core conteneurisées, y compris celles avec JavaScript côté client telle que l’application à page unique React.js et les publier sur ACR (Azure Container Registry), Docker Hub, Azure App Service ou votre propre registre de conteneurs. Dans cet article, nous allons effectuer la publication sur ACR.

## <a name="prerequisites"></a>Prérequis

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) avec la charge de travail **Développement web**, **Azure Tools** et/ou la charge de travail **Développement multiplateforme .NET Core**
* Pour publier sur Azure Container Registry, un abonnement Azure. [Inscrivez-vous pour obtenir une version d’évaluation gratuite](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.JS](https://nodejs.org/en/download/)
* Pour les conteneurs Windows, Windows 10 version 1903 ou ultérieure, pour utiliser les images de l’ancrage référencées dans cet article.
::: moniker-end
::: moniker range=">=vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) avec la charge de travail **Développement web**, **Outils Azure** et/ou la charge de travail **Développement multiplateforme .NET Core** installée
* [Outils de développement .NET core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) pour le développement avec .NET Core 2.2
* Pour publier sur Azure Container Registry, un abonnement Azure. [Inscrivez-vous pour obtenir une version d’évaluation gratuite](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.JS](https://nodejs.org/en/download/)
* Pour les conteneurs Windows, Windows 10 version 1903 ou ultérieure, pour utiliser les images de l’ancrage référencées dans cet article.
::: moniker-end

## <a name="installation-and-setup"></a>Installation et configuration

Pour l’installation de l’ordinateur d’amarrage, commencez par examiner les informations sur le [Bureau de station d’accueil Desktop pour Windows : ce que vous devez savoir avant d’installer](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install). Installez ensuite [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="create-a-project-and-add-docker-support"></a>Créer un projet et ajouter le support Docker

::: moniker range="vs-2017"
1. Créez un nouveau projet à l’aide du modèle **Application web ASP.NET Core**.
1. Sélectionnez **React.js**. Vous ne pouvez pas sélectionner **Activer le support Docker**, mais ne vous inquiétez pas, vous pouvez ajouter ce support après avoir créé le projet.

   ![Capture d’écran du nouveau projet React.js](media/container-tools-react/vs2017/new-react-project.png)

1. Cliquez avec le bouton de droite sur le nœud du projet, puis choisissez **Ajouter** > **Support Docker** pour ajouter un fichier Dockerfile à votre projet.

   ![Ajouter la prise en charge Docker](media/container-tools-react/vs2017/add-docker-support.png)

1. Sélectionnez le type de conteneur, puis cliquez sur **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. Créez un nouveau projet à l’aide du modèle **Application web ASP.NET Core**.
1. Sélectionnez **React.js**, puis cliquez sur **Créer**. Vous ne pouvez pas sélectionner **Activer le support Docker**, mais ne vous inquiétez pas, vous pouvez ajouter ce support plus tard.

   ![Capture d’écran du nouveau projet React.js](media/container-tools-react/vs2019/new-react-project.png)

1. Cliquez avec le bouton de droite sur le nœud du projet, puis choisissez **Ajouter** > **Support Docker** pour ajouter un fichier Dockerfile à votre projet.

   ![Ajouter la prise en charge Docker](media/container-tools-react/vs2017/add-docker-support.png)

1. Sélectionnez le type de conteneur.
::: moniker-end

L’étape suivante est différente selon que vous utilisez des conteneurs Linux ou des conteneurs Windows.

## <a name="modify-the-dockerfile-linux-containers"></a>Modifier les fichier dockerfile (conteneurs Linux)

Un *fichier Docker*, la recette permettant de créer une image Docker finale, est créé dans le projet. Reportez-vous à la [référence fichier dockerfile](https://docs.docker.com/engine/reference/builder/) pour connaître les commandes qu’il contient.

Ouvrez le *Dockerfile* dans le projet et ajoutez les lignes suivantes pour installer Node.js 10.x dans le conteneur. Veillez à ajouter ces lignes dans la première section pour ajouter l’installation du gestionnaire de package node *NPM. exe* à l’image de base, ainsi que dans la `build` section.

```Dockerfile
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

Le *Dockerfile* doit ressembler à ceci :

```Dockerfile
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80 
EXPOSE 443
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs

FROM microsoft/dotnet:2.2-sdk-stretch AS build
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
WORKDIR /src
COPY ["WebApplication37/WebApplication37.csproj", "WebApplication37/"]
RUN dotnet restore "WebApplication37/WebApplication37.csproj"
COPY . .
WORKDIR "/src/WebApplication37"
RUN dotnet build "WebApplication37.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "WebApplication37.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication37.dll"]
```

Le *Dockerfile* précédent est basé sur l’image [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/). Il comprend des instructions pour modifier l’image de base en générant votre projet et en l’ajoutant au conteneur.

Quand la case **Configurer pour HTTPS** de la boîte de dialogue du nouveau projet est cochée, le fichier *Dockerfile* expose deux ports. Un port est utilisé pour le trafic HTTP tandis que l’autre est utilisé pour HTTPS. Si la case n’est pas cochée, un seul port (80) est exposé pour le trafic HTTP.

## <a name="modify-the-dockerfile-windows-containers"></a>Modifier le fichier dockerfile (conteneurs Windows)

Ouvrez le fichier projet en double-cliquant sur le nœud du projet et mettez à jour le fichier projet (*. csproj) en ajoutant la propriété suivante en tant qu’enfant de l' `<PropertyGroup>` élément :

   ```xml
    <DockerfileFastModeStage>base</DockerfileFastModeStage>
   ```

Mettez à jour le fichier dockerfile en ajoutant les lignes suivantes. Cela va copier node et NPM vers le conteneur.

   1. Ajouter ``# escape=` `` à la première ligne du fichier dockerfile
   1. Ajoutez les lignes suivantes avant`FROM … base`

      ```Dockerfile
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs
      ```

   1. Ajoutez la ligne suivante avant et après`FROM … build`

      ```Dockerfile
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      ```

   1. Le fichier dockerfile complet doit maintenant ressembler à ceci :

      ```Dockerfile
      # escape=`
      #Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
      #For more information, please see https://aka.ms/containercompat
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      RUN mkdir -p C:\nodejsfolder
      WORKDIR C:\nodejsfolder
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs

      FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1903 AS base
      WORKDIR /app
      EXPOSE 80
      EXPOSE 443
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\

      FROM mcr.microsoft.com/dotnet/core/sdk:2.2-nanoserver-1903 AS build
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      WORKDIR /src
      COPY ["WebApplication7/WebApplication37.csproj", "WebApplication37/"]
      RUN dotnet restore "WebApplication7/WebApplication7.csproj"
      COPY . .
      WORKDIR "/src/WebApplication37"
      RUN dotnet build "WebApplication37.csproj" -c Release -o /app/build

      FROM build AS publish
      RUN dotnet publish "WebApplication37.csproj" -c Release -o /app/publish

      FROM base AS final
      WORKDIR /app
      COPY --from=publish /app/publish .
      ENTRYPOINT ["dotnet", "WebApplication37.dll"]
      ```

1. Mettez à jour le fichier. dockerignore en supprimant le `**/bin` .

## <a name="debug"></a>Débogage

Sélectionnez **Docker** dans la liste déroulante de débogage dans la barre d’outils et démarrez le débogage de l’application. Vous pouvez être amené à voir s’afficher un message vous invitant à approuver un certificat. Choisissez d’approuver le certificat pour continuer.  La première fois que vous générez, l’arrimeur télécharge les images de base, ce qui peut prendre un peu plus de temps.

L’option **Outil conteneur** dans la fenêtre **Sortie** indique les actions en cours. Vous devez voir les étapes d’installation associés à *npm.exe*.

Le navigateur affiche la page d’accueil de l’application.

::: moniker range="vs-2017"
   ![Capture d’écran de l’application en cours d’exécution](media/container-tools-react/vs2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Capture d’écran de l’application en cours d’exécution](media/container-tools-react/vs2019/running-app.png)
::: moniker-end

Essayez d’accéder à la page *Compteur* et de tester le code côté client pour le compteur en cliquant sur le bouton **Incrément**.

Ouvrez la **Console du Gestionnaire de package** à partir du menu **Outils**> Gestionnaire de package NuGet, **Console du Gestionnaire de package**.

L’image Docker obtenue de l’application est marquée avec la balise *dev*. L’image est basée sur la balise *2.2-aspnetcore-runtime* de l’image de base *microsoft/dotnet*. Exécutez la commande `docker images` dans la fenêtre **Console du Gestionnaire de package**. Les images sur la machine s’affichent :

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
webapplication37  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> L’image **dev** ne contient pas les fichiers binaires de l’application ni aucun autre contenu. En effet, les configurations **Debug** utilisent le montage de volume pour fournir l’expérience de modification et de débogage itérative. Pour créer une image de production incluant tout le contenu, utilisez la configuration **Release**.

Exécutez la commande `docker ps` dans la console du Gestionnaire de package. Notez que l’application s’exécute à l’aide du conteneur :

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        webapplication37:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
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
    | **[PAIRE](/azure/container-registry/container-registry-skus)** | standard | Niveau de service du registre de conteneurs  |
    | **Emplacement du registre** | Un emplacement proche de vous | Choisissez un emplacement dans une [région](https://azure.microsoft.com/regions/) près de chez vous ou près d’autres services que votre registre de conteneurs va utiliser. |

    ![Boîte de dialogue de création d’un registre de conteneurs Azure dans Visual Studio][0]

1. Cliquez sur **Créer**.

   ![Capture d’écran affichant la réussite de la publication](media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez désormais extraire le conteneur à partir du registre sur tout hôte en mesure d’exécuter des images Docker, par exemple [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="additional-resources"></a>Ressources supplémentaires

* [Développement de conteneurs avec Visual Studio](/visualstudio/containers)
* [Détecter un problème de développement Visual Studio avec Docker](troubleshooting-docker-errors.md)
* [Référentiel GitHub des outils de conteneur Visual Studio](https://github.com/Microsoft/DockerTools)

::: moniker range="vs-2017"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
::: moniker-end
::: moniker range=">=vs-2019"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
::: moniker-end