---
title: Installer Visual Studio Build Tools dans un conteneur
titleSuffix: ''
description: Découvrez comment installer Visual Studio Build Tools dans un conteneur Windows pour permettre la prise en charge des flux de travail d’intégration continue (CI) et de livraison continue (CD).
ms.date: 04/18/2018
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: cd2294d3018aba3d2e7ff8a0c0737b32a05214c0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974252"
---
# <a name="install-build-tools-into-a-container"></a>Installer Build Tools dans un conteneur

Vous pouvez installer Visual Studio Build Tools dans un conteneur Windows pour prendre en charge les flux de travail d’intégration continue (CI) et de livraison continue(CD). Cet article vous explique comment procéder aux modifications nécessaires de la configuration Docker, et vous donne les [charges de travail et composants](workload-component-id-vs-build-tools.md) que vous pouvez installer dans un conteneur.

Les [conteneurs](https://www.docker.com/what-container) sont un excellent moyen d’empaqueter un système de génération cohérent, que vous pouvez utiliser non seulement dans un environnement serveur CI/CD, mais également dans un environnement de développement. Par exemple, vous pouvez monter du code source dans un conteneur pour qu’il soit généré par un environnement personnalisé, tout en continuant à utiliser Visual Studio ou d’autres outils pour écrire votre code. Si votre flux de travail CI/CD utilise la même image de conteneur, vous avez la garantie que votre code est généré de manière cohérente. Vous pouvez également utiliser des conteneurs à des fins de cohérence d’exécution, ce qui est courant pour les microservices qui utilisent plusieurs conteneurs avec un système d’orchestration. Toutefois, cela dépasse le cadre de cet article.

Si Visual Studio Build Tools n’a pas ce dont vous avez besoin pour générer votre code source, vous pouvez utiliser ces étapes pour d’autres produits Visual Studio. Notez, toutefois, que les conteneurs Windows ne prennent pas en charge les interfaces utilisateur interactives, et que toutes les commandes doivent être automatisées.

## <a name="overview"></a>Vue d'ensemble

Avec [Docker](https://www.docker.com/what-docker), vous créez une image à partir de laquelle vous pouvez créer des conteneurs qui génèrent votre code source. L’exemple de fichier Dockerfile installe la dernière version de Visual Studio Build Tools, ainsi que d’autres programmes utiles souvent utilisés pour la génération de code source. Vous pouvez modifier davantage votre propre fichier Dockerfile en y ajoutant d’autres outils et scripts pour exécuter des tests, publier la sortie de génération, et bien plus encore.

Si vous avez déjà installé Docker pour Windows, vous pouvez passer à l’étape 3.

## <a name="step-1-enable-hyper-v"></a>Étape 1. Activer Hyper-V

Hyper-V n’est pas activé par défaut. Il doit être activé au démarrage de Docker pour Windows, puisque seule l’isolation Hyper-V est prise en charge par Windows 10.

* [Activer Hyper-V sur Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)
* [Activer Hyper-V sur Windows Server 2016](https://docs.microsoft.com/windows-server/virtualization/hyper-v/get-started/install-the-hyper-v-role-on-windows-server)

> [!NOTE]
> La virtualisation doit être activée sur votre machine. Elle est généralement activée par défaut. Toutefois, si l’installation d’Hyper-V échoue, reportez-vous à la documentation de votre système pour savoir comment activer la virtualisation.

## <a name="step-2-install-docker-for-windows"></a>Étape 2. Installer Docker pour Windows

Si vous utilisez Windows 10, vous pouvez [télécharger et installer Docker Community Edition](https://docs.docker.com/docker-for-windows/install). Si vous utilisez Windows Server 2016, suivez les [instructions d’installation de Docker Enterprise Edition](https://docs.docker.com/install/windows/docker-ee).

## <a name="step-3-switch-to-windows-containers"></a>Étape 3. Passer aux conteneurs Windows

Vous pouvez installer Build Tools seulement sur Windows, ce qui nécessite de [passer aux conteneurs Windows](https://docs.docker.com/docker-for-windows/#getting-started-with-windows-containers). Dans Windows 10, les conteneurs Windows prennent uniquement en charge [l’isolation Hyper-V](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container), alors que dans Windows Server 2016, les conteneurs Windows prennent en charge à la fois l’isolation Hyper-V et l’isolation des processus.

## <a name="step-4-expand-maximum-container-disk-size"></a>Étape 4. Augmenter la taille maximale du disque du conteneur

Visual Studio Build Tools, et plus généralement Visual Studio, nécessitent une grande quantité d’espace disque pour tous les outils à installer. Même si l’exemple de fichier Dockerfile désactive le cache de packages, vous devez augmenter la taille du disque des images conteneurs en fonction de l’espace nécessaire. Dans Windows, vous pouvez uniquement augmenter la taille du disque en modifiant la configuration de Docker.

**Sur Windows 10** :

1. [Cliquez avec le bouton droit sur l’icône de Docker pour Windows](https://docs.docker.com/docker-for-windows/#docker-settings) dans la barre d’état système, puis cliquez sur **Paramètres**.

1. [Cliquez sur la section Démon](https://docs.docker.com/docker-for-windows/#docker-daemon).

1. [Cliquez sur le bouton **De base**](https://docs.docker.com/docker-for-windows/#edit-the-daemon-configuration-file) pour basculer en mode **Avancé**.

1. Ajoutez la propriété de tableau JSON suivante pour augmenter l’espace disque à 120 Go (ce qui est plus que suffisant pour exécuter Build Tools et avoir une marge d’espace supplémentaire en cas de besoin).

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Cette propriété vient s’ajouter à ce qui est déjà défini. Par exemple, après avoir appliqué ces modifications au fichier de configuration du démon par défaut, vous devez voir ce qui suit :

   ```json
   {
     "registry-mirrors": [],
     "insecure-registries": [],
     "debug": true,
     "experimental": true,
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

1. Cliquez sur **Appliquer**.

**Sur Windows Server 2016** :

1. Arrêtez le service « docker » :

   ```shell
   sc.exe stop docker
   ```

1. À partir d’une invite de commandes avec élévation de privilèges, modifiez « %ProgramData%\Docker\config\daemon.json » (ou ce que vous avez spécifié sur `dockerd --config-file`).

1. Ajoutez la propriété de tableau JSON suivante pour augmenter l’espace disque à 120 Go (ce qui est plus que suffisant pour exécuter Build Tools et avoir une marge d’espace supplémentaire en cas de besoin).

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Cette propriété vient s’ajouter à ce qui est déjà défini.
 
1. Enregistrez et fermez le fichier.

1. Démarrez le service « docker » :

   ```shell
   sc.exe start docker
   ```

## <a name="step-5-create-and-build-the-dockerfile"></a>Étape 5. Créer et générer le fichier Dockerfile

Enregistrez l’exemple Dockerfile suivant dans un nouveau fichier sur votre disque. Si le fichier se nomme simplement « Dockerfile », il est reconnu par défaut.

> [!WARNING]
> Cet exemple de fichier Dockerfile exclut seulement les anciens SDK Windows qui ne peuvent pas être installés dans des conteneurs. Les versions précédentes font échouer la commande de build.

1. Ouvrez une invite de commandes.

1. Créez un répertoire (recommandé) :

   ```shell
   mkdir C:\BuildTools
   ```

1. Remplacez les répertoires par ce nouveau répertoire :

   ```shell
   cd C:\BuildTools
   ```

1. Enregistrez le contenu suivant dans C:\BuildTools\Dockerfile.
 
   ::: moniker range="vs-2017"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.1.
   FROM microsoft/dotnet-framework:4.7.1

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --all `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!WARNING]
   > Si vous basez votre image directement sur microsoft/windowsservercore, l’installation du .NET Framework risque de ne pas s’effectuer correctement et aucune erreur d’installation ne sera signalée. Le code managé risque de ne pas s’exécuter une fois l’installation terminée. Basez plutôt votre image sur [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) ou une version ultérieure. Notez également que les images étiquetées avec la version 4.7.1 ou ultérieure sont susceptibles d’utiliser PowerShell comme `SHELL` par défaut, ce qui provoque l’échec des instructions `RUN` et `ENTRYPOINT`.
   >
   > Quel que soit le produit, Visual Studio 2017 version 15.8 ou antérieure ne s’installe pas correctement sur mcr\.microsoft\.com\/windows\/servercore:1809 ou ultérieur. Aucune erreur ne s’affiche.
   >
   > Pour plus d’informations, voir [Problèmes de conteneurs connus](build-tools-container-issues.md).

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.1.
   FROM microsoft/dotnet-framework:4.7.1

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --all `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!WARNING]
   > Si vous basez votre image directement sur microsoft/windowsservercore, l’installation du .NET Framework risque de ne pas s’effectuer correctement et aucune erreur d’installation ne sera signalée. Le code managé risque de ne pas s’exécuter une fois l’installation terminée. Basez plutôt votre image sur [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) ou une version ultérieure. Notez également que les images étiquetées avec la version 4.7.1 ou ultérieure sont susceptibles d’utiliser PowerShell comme `SHELL` par défaut, ce qui provoque l’échec des instructions `RUN` et `ENTRYPOINT`.
   >
   > Pour plus d’informations, voir [Problèmes de conteneurs connus](build-tools-container-issues.md).

   ::: moniker-end

1. Exécutez la commande suivante dans ce répertoire.

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Cette commande permet de générer le fichier Dockerfile dans le répertoire actif, en utilisant 2 Go de mémoire. La valeur par défaut de 1 Go n’est pas suffisante quand certaines charges de travail sont installées ; la possibilité de générer avec seulement 1 Go de mémoire dépend cependant des exigences de votre build.

   L’image finale est marquée comme « buildtools2017:latest » pour que vous puissiez aisément l’exécuter dans un conteneur en tant que « buildtools2017 », puisque la marque « latest » est la valeur par défaut lorsqu’aucune marque n’est spécifiée. Si vous souhaitez utiliser une version spécifique de Visual Studio Build Tools 2017 dans un [scénario avancé](advanced-build-tools-container.md), marquez le conteneur avec un numéro de build Visual Studio spécifique et avec « latest », pour que les conteneurs puissent utiliser la même version.

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   Cette commande permet de générer le fichier Dockerfile dans le répertoire actif, en utilisant 2 Go de mémoire. La valeur par défaut de 1 Go n’est pas suffisante quand certaines charges de travail sont installées ; la possibilité de générer avec seulement 1 Go de mémoire dépend cependant des exigences de votre build.

   L’image finale est étiquetée « buildtools2019:latest » : vous pouvez donc l’exécuter facilement dans un conteneur en tant que « buildtools2019 », car l’étiquette « latest » est la valeur par défaut si aucune étiquette n’est spécifiée. Si vous voulez utiliser une version spécifique de Visual Studio Build Tools 2019 dans un [scénario avancé](advanced-build-tools-container.md), étiquetez le conteneur avec un numéro de build Visual Studio spécifique et avec « latest », pour que les conteneurs puissent utiliser la même version.

   ::: moniker-end

## <a name="step-6-using-the-built-image"></a>Étape 6. Utilisation de l’image générée

Maintenant que vous avez créé une image, vous pouvez l’exécuter dans un conteneur pour effectuer des générations automatisées et interactives. L’exemple utilise l’invite de commandes développeur. Votre chemin (PATH) et autres variables d’environnement sont donc déjà configurés.

1. Ouvrez une invite de commandes.

1. Exécutez le conteneur pour démarrer un environnement PowerShell avec toutes les variables d’environnement développeur définies :

   ::: moniker range="vs-2017"

   ```shell
   docker run -it buildtools2017
   ```

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker run -it buildtools2019
   ```

   ::: moniker-end

Pour utiliser cette image pour votre workflow CI/CD, vous pouvez la publier dans votre propre instance [Azure Container Registry](https://azure.microsoft.com/services/container-registry) ou dans un autre [registre Docker](https://docs.docker.com/registry/deploying) interne, pour que les serveurs doivent seulement l’extraire.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Exemple avancé pour les conteneurs](advanced-build-tools-container.md)
* [Problèmes de conteneurs connus](build-tools-container-issues.md)
* [ID de composant et de charge de travail de Visual Studio Build Tools](workload-component-id-vs-build-tools.md)
