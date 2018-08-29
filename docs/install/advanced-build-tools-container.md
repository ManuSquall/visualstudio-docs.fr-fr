---
title: Exemple avancé pour les conteneurs
description: ''
ms.custom: ''
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b8d779dec88bf912f04dca6d8b736fb5f3e53dd
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43139299"
---
# <a name="advanced-example-for-containers"></a>Exemple avancé pour les conteneurs

L’exemple de fichier Dockerfile décrit dans [Installer Build Tools dans un conteneur](build-tools-container.md) utilise toujours l’image [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) en fonction de la dernière image microsoft/windowsservercore et de la dernière version du programme d’installation de Visual Studio Build Tools 2017. Si vous publiez cette image dans un [registre Docker](https://azure.microsoft.com/services/container-registry) pour que les utilisateurs puissent la tirer (pull), elle conviendra dans de nombreux scénarios. Toutefois, en pratique, il est plus courant de préciser l’image de base que vous utilisez, les binaires que vous téléchargez et les versions des outils que vous installez.

L’exemple de fichier Dockerfile suivant utilise une étiquette de version spécifique de l’image microsoft/dotnet-framework. L’utilisation d’une balise spécifique pour une image de base est très répandue et permet de garder à l’esprit que la génération et la regénération des images ont toujours la même base.

> [!NOTE]
> Vous ne pouvez pas installer Visual Studio dans l’image microsoft/windowsservercore:10.0.14393.1593 ou toute autre image basée sur celle-ci, en raison de problèmes connus liés au lancement du programme d’installation dans un conteneur. Pour plus d’informations, consultez la section [Problèmes connus](build-tools-container-issues.md).

L’exemple ci-dessous télécharge la dernière version de Build Tools 2017. Si vous souhaitez utiliser une ancienne version de Build Tools que vous pourrez installer plus tard dans un conteneur, vous devez d’abord [créer](create-an-offline-installation-of-visual-studio.md) et [gérer](update-a-network-installation-of-visual-studio.md) une disposition.

## <a name="install-script"></a>Script d’installation

Pour collecter des journaux quand une erreur d’installation se produit, dans le répertoire de travail, créez un script de commandes par lot nommé « Install.cmd » et ayant le contenu suivant :

```shell
@if not defined _echo echo off
setlocal enabledelayedexpansion

call %*
if "%ERRORLEVEL%"=="3010" (
    exit /b 0
) else (
    if not "%ERRORLEVEL%"=="0" (
        set ERR=%ERRORLEVEL%
        call C:\TEMP\collect.exe -zip:C:\vslogs.zip

        exit /b !ERR!
    )
)
```

## <a name="dockerfile"></a>Dockerfile

Dans le répertoire de travail, créez un fichier « Dockerfile » ayant le contenu suivant :

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:1a66e2b5f3a5b8b98ac703a8bfd4902ae60d307ed9842978df40dbc04ac86b1b
ARG FROM_IMAGE=microsoft/dotnet-framework:4.7.1-20180410-windowsservercore-1709
FROM ${FROM_IMAGE}

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/15/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Download and install Build Tools excluding workloads and components with known issues.
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --all `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

Exécutez la commande suivante pour générer l’image dans le répertoire de travail actuel :

```shell
docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
```

Vous pouvez éventuellement passer l’argument `FROM_IMAGE`, l’argument `CHANNEL_URL` ou les deux à la fois, à l’aide du commutateur de ligne de commande `--build-arg` pour spécifier une autre image de base ou l’emplacement d’une disposition interne pour gérer une image fixe.

## <a name="diagnosing-install-failures"></a>Diagnostiquer les échecs d’installation

Cet exemple télécharge certains outils et vérifie que les hachages correspondent. Il télécharge également le dernier utilitaire de collecte de journaux Visual Studio et .NET. Ainsi, en cas d’échec de l’installation, vous pouvez copier les journaux sur votre machine hôte pour analyser le problème.

```shell
> docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
Sending build context to Docker daemon
...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

Une fois la dernière ligne exécutée, ouvrez « %TEMP%\vslogs.zip » sur votre machine, ou soumettez le problème sur le site web de la [Communauté des développeurs](https://developercommunity.visualstudio.com).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer les outils de génération dans un conteneur](build-tools-container.md)
* [Problèmes de conteneurs connus](build-tools-container-issues.md)
* [ID de composant et de charge de travail de Visual Studio Build Tools 2017](workload-component-id-vs-build-tools.md)
