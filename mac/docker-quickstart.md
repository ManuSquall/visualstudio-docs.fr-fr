---
title: Prise en main de Docker
description: Apprendre à ajouter Docker à vos projets dans Visual Studio pour Mac
author: asb3993
ms.author: amburns
ms.date: 06/17/2019
ms.openlocfilehash: b456b3d285c167f97570c39d9eb6fd1abfc27e45
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68872182"
---
# <a name="get-started-with-docker-in-visual-studio-for-mac"></a>Bien démarrer avec Docker dans Visual Studio pour Mac

Avec Visual Studio pour Mac, vous pouvez facilement générer, déboguer et exécuter des applications ASP.NET Core dans des conteneurs et les publier sur Azure.

## <a name="prerequisites"></a>Prérequis

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio pour Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="installation-and-setup"></a>Installation et configuration

Pour l’installation de Docker, passez en revue et suivez les instructions [d’Installer Docker Desktop pour Mac](https://docs.docker.com/docker-for-mac/install/).

## <a name="creating-an-aspnet-core-web-application-and-adding-docker-support"></a>Créer une application web ASP.NET Core et ajouter la prise en charge de Docker

1. Créez une solution en accédant à **Fichier > Nouvelle solution**.
1. Sous **.NET Core > Application** choisissez le modèle **Application web** : ![Créer une application ASP.NET](media/docker-quickstart-1.png)
1. Sélectionnez le framework cible. Dans cet exemple, nous utiliserons .NET Core 2.2 : ![Définir le framework cible](media/docker-quickstart-2.png)
1. Entrez les détails du projet, comme son nom (_DockerDemo_ dans cet exemple). Le projet créé contient tous les éléments de base pour générer et exécuter un site web ASP.NET Core.
1. Dans le panneau Solutions, cliquez avec le bouton droit sur le projet DockerDemo et sélectionnez **Ajouter > Ajouter la prise en charge Docker** : ![Ajouter la prise en charge Docker](media/docker-quickstart-3.png)

Visual Studio pour Mac ajoute automatiquement un nouveau projet appelé **docker-compose** à votre solution et un **Dockerfile** à votre projet existant.

![Fichiers de prise en charge Docker générés](media/docker-quickstart-4.png)

## <a name="dockerfile-overview"></a>Vue d’ensemble du fichier Dockerfile

Un fichier Docker, la recette permettant de créer une image Docker finale. Reportez-vous à [Informations de référence sur Dockerfile](https://docs.docker.com/engine/reference/builder/) pour comprendre les commandes qu’il contient.

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/dotnet:2.2-sdk AS build
WORKDIR /src
COPY DockerDemo/DockerDemo.csproj DockerDemo/
RUN dotnet restore DockerDemo/DockerDemo.csproj
COPY . .
WORKDIR /src/DockerDemo
RUN dotnet build DockerDemo.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish DockerDemo.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "DockerDemo.dll"]
```

Le *Dockerfile* précédent est basé sur l’image [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/). Il comprend des instructions pour modifier l’image de base en générant votre projet et en l’ajoutant au conteneur.

> [!NOTE]
> Le Dockerfile créé par défaut par Visual Studio pour Mac expose le port 80 pour le trafic HTTP. Pour activer le trafic HTTPS, ajoutez `Expose 443` au Dockerfile.

## <a name="debugging"></a>Débogage

Sélectionnez le projet `docker-compose` comme projet de démarrage et commencez à déboguer (**Exécuter > Démarrer le débogage**). Cela générera, déploiera et lancera le projet ASP.NET dans un conteneur.

> [!TIP]
> Lors de la première exécution après l’installation de Docker Desktop, vous pourriez recevoir l’erreur suivante lorsque vous tentez de déboguer : `Cannot start service dockerdemo: Mounts denied`
>
> Ajoutez `/usr/local/share/dotnet/sdk/NuGetFallbackFolder` à l’onglet File Sharing dans Docker Desktop :
>
> ![Ajout du dossier NuGetFallbackFolder au partage de fichiers](media/docker-quickstart-5.png)

Lorsque la génération est terminée, l’application est lancée dans Safari :

![Exécution du projet Docker par défaut dans Safari](media/docker-quickstart-6.png)

Notez que le conteneur écoute sur un port, `http://localhost:32768` par exemple, et que ce port peut varier.

Pour afficher la liste des conteneurs en cours d’exécution, utilisez la commande `docker ps` dans un Terminal.

Notez le relais de port dans la capture d’écran ci-dessous (sous **PORTS**). Cela indique que le conteneur écoute sur le port que nous avons vu dans Safari ci-dessus et relaie les demandes vers le serveur web interne sur le port 80 (comme défini dans le Dockerfile). Du point de vue de l’application, il écoute sur le port 80 :

![Liste de conteneurs Docker](media/docker-quickstart-7.png)
