---
title: Exemple avancé pour les conteneurs
description: En savoir plus sur un exemple avancé pour les conteneurs de l’ancrage. Cet exemple fichier dockerfile utilise une balise de version spécifique de l’image Microsoft/DotNet-Framework.
ms.custom: SEO-VS-2020
ms.date: 03/25/2020
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2860a19592667008f585a4608eab23e0180dd2ac
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307698"
---
# <a name="advanced-example-for-containers"></a>Exemple avancé pour les conteneurs

::: moniker range="vs-2017"

L’exemple de Dockerfile dans [Installer Build Tools dans un conteneur](build-tools-container.md) utilise toujours l’image [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) basée sur la dernière image microsoft/windowsservercore et sur la dernière version du programme d’installation Visual Studio Build Tools. Si vous publiez cette image dans un [registre Docker](https://azure.microsoft.com/services/container-registry) pour que les utilisateurs puissent l’extraire, celle-ci devrait convenir à de nombreux scénarios. Toutefois, en pratique, il est plus courant de préciser l’image de base que vous utilisez, les binaires que vous téléchargez et les versions des outils que vous installez.

::: moniker-end

::: moniker range=">=vs-2022"

>[!IMPORTANT]
> Visual Studio 2022 est actuellement en version préliminaire et n’est pas [concédé sous licence pour une](https://visualstudio.microsoft.com/license-terms/vs2022-prerelease/) utilisation dans des environnements de production.

::: moniker-end

::: moniker range=">=vs-2019"

L’exemple de fichier Dockerfile décrit dans [Installer Build Tools dans un conteneur](build-tools-container.md) utilise toujours l’image [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) basée sur la dernière image microsoft/windowsservercore et sur la dernière version du programme d’installation de Visual Studio Build Tools. Si vous publiez cette image dans un [registre Docker](https://azure.microsoft.com/services/container-registry) pour que les utilisateurs puissent l’extraire, celle-ci devrait convenir à de nombreux scénarios. Toutefois, en pratique, il est plus courant de préciser l’image de base que vous utilisez, les binaires que vous téléchargez et les versions des outils que vous installez.

::: moniker-end

L’exemple de fichier Dockerfile suivant utilise une étiquette de version spécifique de l’image microsoft/dotnet-framework. L’utilisation d’une balise spécifique pour une image de base est très répandue et permet de garder à l’esprit que la génération et la regénération des images ont toujours la même base.

> [!NOTE]
> Vous ne pouvez pas installer Visual Studio dans l’image microsoft/windowsservercore:10.0.14393.1593 ou toute autre image basée sur celle-ci, en raison de problèmes connus liés au lancement du programme d’installation dans un conteneur. Pour plus d’informations, consultez [Problèmes connus liés aux conteneurs](build-tools-container-issues.md).

L’exemple suivant télécharge la dernière version de Build Tools. Si vous voulez utiliser une version antérieure de Build Tools pour l’installer plus tard dans un conteneur, vous devez d’abord [créer](create-an-offline-installation-of-visual-studio.md) et [gérer](update-a-network-installation-of-visual-studio.md) une disposition.

## <a name="install-script"></a>Script d’installation

Pour collecter des journaux quand une erreur d’installation se produit, créez un script de commandes par lots nommé « Install.cmd » dans le répertoire de travail et ayant le contenu suivant :

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

::: moniker range="vs-2017"

```dockerfile
# escape=`

# Use a specific tagged image.
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/runtime:4.8
FROM ${FROM_IMAGE}

# Restore the default Windows shell for correct batch processing.
SHELL ["cmd", "/S", "/C"]

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/15/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --add Microsoft.VisualStudio.Workload.AzureBuildTools `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Define the entry point for the Docker container.
# This entry point starts the developer command prompt and launches the PowerShell shell.
ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

   > [!WARNING]
   > Quel que soit le produit, Visual Studio 2017 version 15.8 ou antérieure ne s’installe pas correctement sur mcr\.microsoft\.com\/windows\/servercore:1809 ou ultérieur. Aucune erreur ne s’affiche.
   >
   > Pour plus d’informations, voir [Problèmes de conteneurs connus](build-tools-container-issues.md).

::: moniker-end

::: moniker range="vs-2019"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:324e9ab7262331ebb16a4100d0fb1cfb804395a766e3bb1806c62989d1fc1326
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019
FROM ${FROM_IMAGE}

# Restore the default Windows shell for correct batch processing.
SHELL ["cmd", "/S", "/C"]

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/16/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --add Microsoft.VisualStudio.Workload.AzureBuildTools `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Define the entry point for the Docker container.
# This entry point starts the developer command prompt and launches the PowerShell shell.
ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

::: moniker-end

::: moniker range=">=vs-2022"

>[!IMPORTANT]
> Visual Studio 2022 est actuellement en version préliminaire et n’est pas [concédé sous licence pour une](https://visualstudio.microsoft.com/license-terms/vs2022-prerelease/) utilisation dans des environnements de production.

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:324e9ab7262331ebb16a4100d0fb1cfb804395a766e3bb1806c62989d1fc1326
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019
FROM ${FROM_IMAGE}

# Restore the default Windows shell for correct batch processing.
SHELL ["cmd", "/S", "/C"]

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/17/preview/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
ADD https://aka.ms/vs/17/preview/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --add Microsoft.VisualStudio.Workload.AzureBuildTools `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Define the entry point for the Docker container.
# This entry point starts the developer command prompt and launches the PowerShell shell.
ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

::: moniker-end

Exécutez la commande suivante pour générer l’image dans le répertoire de travail actuel :

::: moniker range="vs-2017"

```shell
docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
```

::: moniker-end

::: moniker range="vs-2019"

```shell
docker build -t buildtools2019:16.0.28714.193 -t buildtools2019:latest -m 2GB .
```

::: moniker-end

::: moniker range=">=vs-2022"

```shell
docker build -t buildtools2022:17.0 -t buildtools2022:latest -m 2GB .
```

::: moniker-end

Vous pouvez éventuellement passer l’argument `FROM_IMAGE`, l’argument `CHANNEL_URL` ou les deux à la fois, à l’aide du commutateur de ligne de commande `--build-arg` pour spécifier une autre image de base ou l’emplacement d’une disposition interne pour gérer une image fixe.

> [!TIP]
> Pour obtenir la liste des charges de travail et des composants, consultez le [répertoire du composant Visual Studio Build Tools](workload-component-id-vs-build-tools.md).
>

## <a name="diagnosing-install-failures"></a>Diagnostiquer les échecs d’installation

Cet exemple télécharge certains outils et vérifie que les hachages correspondent. Il télécharge également le dernier utilitaire de collecte de journaux Visual Studio et .NET. Ainsi, en cas d’échec de l’installation, vous pouvez copier les journaux sur votre machine hôte pour analyser le problème.

::: moniker range="vs-2017"

```shell
> docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

::: moniker range="vs-2019"

```shell
> docker build -t buildtools2019:16.0.28714.193 -t buildtools2019:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

::: moniker range=">=vs-2022"

```shell
> docker build -t buildtools2022:17.0 -t buildtools2022:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

Une fois la dernière ligne exécutée, ouvrez « %TEMP%\vslogs.zip » sur votre machine ou soumettez le problème sur le site web de la [Communauté des développeurs](https://aka.ms/feedback/suggest?space=8).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Build Tools dans un conteneur](build-tools-container.md)
* [Problèmes connus liés aux conteneurs](build-tools-container-issues.md)
* [ID de composant et de charge de travail de Visual Studio Build Tools](workload-component-id-vs-build-tools.md)
