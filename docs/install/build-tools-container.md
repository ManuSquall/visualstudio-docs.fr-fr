---
title: Installer Visual Studio Build Tools dans un conteneur
titleSuffix: ''
description: Découvrez comment installer Visual Studio Build Tools dans un conteneur Windows pour permettre la prise en charge des flux de travail d’intégration continue (CI) et de livraison continue (CD).
ms.date: 03/25/2020
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fc3133692007a53b48d658ed284d6af0bde0af4a
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2021
ms.locfileid: "112043079"
---
# <a name="install-build-tools-into-a-container"></a>Installer Build Tools dans un conteneur

Vous pouvez installer Visual Studio Build Tools dans un conteneur Windows pour prendre en charge les flux de travail d’intégration continue (CI) et de livraison continue(CD). Cet article vous explique comment procéder aux modifications nécessaires de la configuration Docker, et vous donne les [charges de travail et composants](workload-component-id-vs-build-tools.md) que vous pouvez installer dans un conteneur.

Les [conteneurs](https://www.docker.com/what-container) sont un excellent moyen d’empaqueter un système de génération cohérent, que vous pouvez utiliser non seulement dans un environnement serveur CI/CD, mais également dans un environnement de développement. Par exemple, vous pouvez monter du code source dans un conteneur pour qu’il soit généré par un environnement personnalisé, tout en continuant à utiliser Visual Studio ou d’autres outils pour écrire votre code. Si votre flux de travail CI/CD utilise la même image de conteneur, vous avez la garantie que votre code est généré de manière cohérente. Vous pouvez également utiliser des conteneurs à des fins de cohérence d’exécution, ce qui est courant pour les microservices qui utilisent plusieurs conteneurs avec un système d’orchestration. Toutefois, cela dépasse le cadre de cet article.

Si Visual Studio Build Tools n’a pas ce dont vous avez besoin pour générer votre code source, vous pouvez utiliser ces étapes pour d’autres produits Visual Studio. Notez, toutefois, que les conteneurs Windows ne prennent pas en charge les interfaces utilisateur interactives, et que toutes les commandes doivent être automatisées.

## <a name="before-you-begin"></a>Avant de commencer

Il est utile d’acquérir des connaissances sur [Docker](https://www.docker.com/what-docker) pour ce qui suit. Si vous n’êtes pas déjà familiarisé avec l’exécution de Docker sur Windows, découvrez comment [installer et configurer le moteur Docker sur Windows](/virtualization/windowscontainers/manage-docker/configure-docker-daemon).

L’image de base ci-dessous est un exemple et peut ne pas fonctionner pour votre système. Lisez [compatibilité des versions du conteneur Windows](/virtualization/windowscontainers/deploy-containers/version-compatibility) pour déterminer quelle image de base utiliser pour votre environnement.

## <a name="create-and-build-the-dockerfile"></a>Créer et générer le fichier Dockerfile

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

   # Use the latest Windows Server Core image with .NET Framework 4.7.2.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   RUN `
       # Download the Build Tools bootstrapper.
       curl -SL --output vs_buildtools.exe https://aka.ms/vs/15/release/vs_buildtools.exe `
       `
       # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
       && (start /w vs_buildtools.exe --quiet --wait --norestart --nocache `
           --installPath C:\BuildTools `
           --add Microsoft.VisualStudio.Workload.AzureBuildTools `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
           --remove Microsoft.VisualStudio.Component.Windows81SDK `
           || IF "%ERRORLEVEL%"=="3010" EXIT 0) `
       `
       # Cleanup
       && del /q vs_buildtools.exe

   # Define the entry point for the Docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > Pour obtenir la liste des charges de travail et des composants, consultez le [répertoire du composant Visual Studio Build Tools](workload-component-id-vs-build-tools.md).
   >

   > [!WARNING]
   > Si vous basez votre image directement sur microsoft/windowsservercore ou mcr.microsoft.com/windows/servercore (voir [Microsoft syndicates container catalog](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/)) , l’installation du .NET Framework risque de ne pas s’effectuer correctement et aucune erreur d’installation ne sera signalée. Le code managé risque de ne pas s’exécuter une fois l’installation terminée. Basez plutôt votre image sur [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) ou une version ultérieure. Notez également que les images marquées avec la version 4.7.2 ou version ultérieure sont susceptibles d’utiliser PowerShell comme `SHELL` par défaut, ce qui provoque l’échec des instructions `RUN` et `ENTRYPOINT`.
   >
   > Visual Studio 2017 version 15.8 ou version antérieure (quel que soit le produit) ne s’installe pas correctement sur mcr.microsoft.com/windows/servercore:1809 ou version ultérieure. Aucune erreur ne s’affiche.
   >
   > Consultez la page [Compatibilité des versions de conteneur Windows](/virtualization/windowscontainers/deploy-containers/version-compatibility) pour voir quelles versions de conteneur du système d’exploitation sont prises en charge sur les versions de système d’exploitation hôte, et la page [Problèmes connus liés aux conteneurs](build-tools-container-issues.md) pour les problèmes connus.
   
   ::: moniker-end

   ::: moniker range="vs-2019"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.8.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   RUN `
       # Download the Build Tools bootstrapper.
       curl -SL --output vs_buildtools.exe https://aka.ms/vs/16/release/vs_buildtools.exe `
       `
       # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
       && (start /w vs_buildtools.exe --quiet --wait --norestart --nocache modify `
           --installPath "%ProgramFiles(x86)%\Microsoft Visual Studio\2019\BuildTools" `
           --add Microsoft.VisualStudio.Workload.AzureBuildTools `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
           --remove Microsoft.VisualStudio.Component.Windows81SDK `
           || IF "%ERRORLEVEL%"=="3010" EXIT 0) `
       `
       # Cleanup
       && del /q vs_buildtools.exe

   # Define the entry point for the docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > Pour obtenir la liste des charges de travail et des composants, consultez le [répertoire du composant Visual Studio Build Tools](workload-component-id-vs-build-tools.md).
   >

   > [!WARNING]
   > Si vous basez votre image directement sur microsoft/windowsservercore, l’installation du .NET Framework risque de ne pas s’effectuer correctement et aucune erreur d’installation ne sera signalée. Le code managé risque de ne pas s’exécuter une fois l’installation terminée. Basez plutôt votre image sur [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) ou une version ultérieure. Notez également que les images marquées avec la version 4.8 ou ultérieure sont susceptibles d’utiliser PowerShell comme `SHELL` par défaut, ce qui provoque l’échec des instructions `RUN` et `ENTRYPOINT`.
   >
   > Consultez la page [Compatibilité des versions de conteneur Windows](/virtualization/windowscontainers/deploy-containers/version-compatibility) pour voir quelles versions de conteneur du système d’exploitation sont prises en charge sur les versions de système d’exploitation hôte, et la page [Problèmes connus liés aux conteneurs](build-tools-container-issues.md) pour les problèmes connus.

   ::: moniker-end
   
   > [!NOTE]
   > Le code d’erreur `3010` est utilisé pour indiquer la réussite d’un redémarrage requis. pour plus d’informations, consultez [MsiExec.exe des messages d’erreur](/windows/win32/msi/error-codes) .

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

## <a name="using-the-built-image"></a>Utilisation de l’image générée

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

   > [!NOTE]
   > Si le conteneur d’ancrage ne parvient pas à démarrer, il s’agit probablement d’un problème d’installation de Visual Studio. Vous pouvez mettre à jour fichier dockerfile pour supprimer l’étape qui appelle la commande Batch de Visual Studio. Cela vous permet de démarrer le conteneur de l’ancrage et de lire les journaux des erreurs d’installation.
   >
   > Dans votre fichier fichier dockerfile, supprimez `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` les `&&` paramètres et de la `ENTRYPOINT` commande. La commande doit maintenant être `ENTRYPOINT ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]` . Ensuite, régénérez le fichier dockerfile et exécutez la `run` commande pour accéder aux fichiers de conteneur. Pour localiser les journaux des erreurs d’installation, accédez au `$env:TEMP` répertoire et localisez le `dd_setup_<timestamp>_errors.log` fichier.
   >
   > Après avoir identifié et corrigé le problème d’installation, vous pouvez rajouter les `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` `&&` paramètres et à la `ENTRYPOINT` commande, puis recréer votre fichier dockerfile.
   >
   > Pour plus d’informations, consultez [Problèmes connus liés aux conteneurs](build-tools-container-issues.md).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Exemple avancé pour les conteneurs](advanced-build-tools-container.md)
* [Problèmes connus liés aux conteneurs](build-tools-container-issues.md)
* [ID de composant et de charge de travail de Visual Studio Build Tools](workload-component-id-vs-build-tools.md)
