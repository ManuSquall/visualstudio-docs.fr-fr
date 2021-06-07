---
title: Conteneurs Docker et R
description: Guide pratique pour configurer des conteneurs Docker pour R et s’y connecter avec Visual Studio.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 3aefba3880443269dbdb1c933e2c12b2f8001469
ms.sourcegitcommit: fc05a763b59e212c86350d117a1900a1f2686ec8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2021
ms.locfileid: "111551278"
---
# <a name="use-docker-containers-with-r-tools-for-visual-studio"></a>Utiliser des conteneurs Docker avec Outils R pour Visual Studio

Outils R pour Visual Studio (RTVS) version 1.3+, parallèlement à une installation de [Docker pour Windows](https://www.docker.com/docker-windows), prend en charge l’utilisation des conteneurs Docker.

## <a name="create-a-container"></a>Créer un conteneur

1. Sélectionnez le bouton **Conteneurs** dans le coin droit de la fenêtre **Espaces de travail** (**Outils R** > **Windows** > **Espaces de travail**). La fenêtre vous informe si vous n’avez pas installé Docker pour Windows et fournit un lien pour son téléchargement. L’installation de Docker peut nécessiter un redémarrage de l’ordinateur.

    ![Fenêtre Espaces de travail dans Outils R pour Visual Studio (VS2017) avec la commande Conteneurs](media/container-workspaces-window.png)

1. Dans la fenêtre **Conteneurs**, sélectionnez **Créer** :

    ![Commande Créer dans la fenêtre Conteneurs](media/containers-window-create.png)

1. Complétez les informations requises dans la boîte de dialogue et sélectionnez **Créer**. Les informations d’identification que vous entrez sont également utilisées pour créer un compte sur Linux, avec lequel vous vous connecterez ultérieurement.

    ![Entrée d’un nom de conteneur et d’informations d’identification lors de la création d’un conteneur](media/containers-window-create-fill.png)

1. La génération de l’image par RTVS peut prendre un certain temps. La fenêtre **Sortie** dans Visual Studio indique la progression, mais peut sembler figée lors des longs téléchargements d’images ; armez-vous de patience. Une fois l’image créée, RTVS démarre le conteneur, et celui-ci apparaît dans la fenêtre **Conteneur**. Les contrôles situés à droite permettent d’arrêter, de supprimer ou de redémarrer le conteneur.

    ![Fenêtre Conteneurs montrant un conteneur terminé](media/containers-window-created.png)

## <a name="connect-to-a-container"></a>Se connecter à un conteneur

1. La section **Conteneurs en cours d’exécution locaux** de la fenêtre **Espaces de travail** présente les conteneurs qui exécutent le démon RTVS sur le port 5444. (Consultez [R Server distant pour Linux](setting-up-remote-r-service-on-linux.md) pour plus d’informations sur la façon dont le démon est configuré.)

    ![Fenêtre Espaces de travail montrant les conteneurs disponibles](media/workspaces-window-running-containers.png)

1. Pour vous connecter à un conteneur, double-cliquez sur son nom ou sélectionnez la flèche située à sa droite. Une fois connecté, une fenêtre **interactive R** apparaît (consultez [Utiliser la fenêtre interactive R](interactive-repl-for-r-in-visual-studio.md)) :

    ![Fenêtre Espaces de travail et fenêtre REPL ouvertes pour un conteneur](media/workspaces-window-container-connected.png)

## <a name="use-custom-built-images"></a>Utiliser des images personnalisées

RTVS détecte et autorise la gestion des conteneurs créés à l’aide d’images personnalisées, comme l’image microsoft/rtvs décrite dans le fichier Docker ci-dessous. L’image de base utilisée ici a rtvs-daemon, R 3.4.2 et les packages R courants préinstallés. **Remarque** : modifiez le nom d’utilisateur et le mot de passe indiqués ici, si nécessaire.

```docker
FROM mcr.microsoft.com/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Utilisez la commande suivante pour générer l’image, en changeant le nom du conteneur (argument `--name`) à votre gré :

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

L’argument `-p 6056:5444` mappe le port 6056 sur le port interne 5444, que RTVS utilise pour détecter rtvs-daemon. Tout conteneur qui expose le port du conteneur 5444 est répertorié dans la fenêtre **Espaces de travail**. Vous pouvez alors utiliser la fenêtre **Espaces de travail** pour vous connecter à un conteneur en utilisant `<<unix>>\ruser1` comme nom d’utilisateur et « foobar » comme mot de passe, sauf si vous avez spécifié des informations d’identification différentes dans le fichier Docker.
