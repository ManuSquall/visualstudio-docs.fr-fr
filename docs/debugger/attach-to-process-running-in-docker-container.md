---
title: Attacher à un processus en cours d’exécution sur un conteneur d’ancrage
description: Découvrez comment déboguer une application qui exécute un conteneur d’ancrage à l’aide de Visual Studio
ms.date: 11/11/2020
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux Docker container
- debugging, Docker container
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 4f39d4ecd69b726c1d549d723fadd324b1edd722
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857927"
---
# <a name="attach-to-a-process-running-on-a-docker-container"></a>Attacher à un processus en cours d’exécution sur un conteneur d’ancrage 

Vous pouvez déboguer des applications qui s’exécutent dans un conteneur Windows Dockr ou un conteneur Linux Core Linux Core à l’aide de Visual Studio.

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a>Attachement à un processus en cours d’exécution sur un conteneur d’ancrage Linux

Vous pouvez attacher le débogueur Visual Studio à un processus en cours d’exécution dans un conteneur Linux Core Linux Core sur votre ordinateur local ou distant à l’aide de la boîte **de dialogue Attacher au processus** .

> [!IMPORTANT]
> Pour utiliser cette fonctionnalité, vous devez installer la charge de travail de développement multiplateforme .NET Core et disposer d’un accès local au code source.

**Pour attacher un processus en cours d’exécution dans un conteneur d’ancrage Linux :**

1. Dans Visual Studio, sélectionnez **Déboguer > attacher au processus (Ctrl + Alt + P)** pour ouvrir la boîte de dialogue **attacher au processus** .

![Capture d’écran de la boîte de dialogue Attacher au processus dans Visual Studio montrant un type de connexion Dockr (conteneur Linux).](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Définissez le **type de connexion** sur **Dockr (conteneur Linux)**.
3. Sélectionnez **Rechercher...** pour définir la **cible de connexion** via la boîte de dialogue **Sélectionner un conteneur d’ancrage** .

    Vous pouvez déboguer un processus de conteneur de l’ancrage localement ou à distance.

    **Pour déboguer un processus de conteneur d’ancrage localement :**
    1. Définissez l’ordinateur hôte de l’interface de commande de l' **arrimeur** sur l' **ordinateur local**.
    1. Sélectionnez un conteneur en cours d’exécution auquel effectuer l’attachement dans la liste et appuyez sur **OK**.

    ![Menu Sélectionner le conteneur de l’ancrage](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")

    **P. Pour déboguer un processus de conteneur d’ancrage à distance :**

    > [!NOTE]
    > Il existe deux options pour la connexion à distance à un processus en cours d’exécution dans un conteneur d’ancrage. La première option, pour utiliser SSH, est idéale si vous n’avez pas installé les outils de l’outil d’ancrage sur votre ordinateur local.  Si vous avez installé les outils de l’outil d’amarrage localement et que vous disposez d’un démon de station d’accueil configuré pour accepter les demandes distantes, essayez la deuxième option, à l’aide d’un démon de station d’accueil.

    1. ***Pour vous connecter à une machine distante via SSH :***
        1. Sélectionnez **Ajouter...** pour vous connecter à un système distant.<br/>
        ![Se connecter à un système distant](../debugger/media/connect-remote-system.png "Se connecter à un système distant")
        1. Sélectionnez un conteneur en cours d’exécution auquel effectuer l’attachement après vous être connecté au démon SSH ou démon, puis cliquez sur **OK**.

    1. ***Pour définir la cible sur un conteneur distant exécutant un processus via un [démon d’ancrage](https://docs.docker.com/engine/reference/commandline/dockerd/)***
        1. Spécifiez l’adresse du démon (par exemple, via TCP, IP, etc.) sous hôte de l' **ordinateur de point de connexion (facultatif)** , puis cliquez sur le lien Actualiser.
        1. Sélectionnez un conteneur en cours d’exécution auquel effectuer l’attachement après avoir réussi à vous connecter au démon et cliqué sur **OK**.

4. Choisissez le processus de conteneur correspondant dans la liste des **processus disponibles** , puis sélectionnez **attacher** pour démarrer le débogage de votre processus de conteneur C# dans Visual Studio.

    ![Capture d’écran de la boîte de dialogue Attacher au processus dans Visual Studio. Le type de connexion est défini sur docker (conteneur Linux) et le processus dotnet est sélectionné.](../debugger/media/docker-attach-complete.png "Menu attacher de l’Ancreur Linux terminé")

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a>Attacher à un processus en cours d’exécution sur un conteneur d’ancrage Windows

Vous pouvez attacher le débogueur Visual Studio à un processus en cours d’exécution dans un conteneur d’ancrage Windows sur votre ordinateur local à l’aide de la boîte **de dialogue Attacher au processus** .

> [!IMPORTANT]
> Pour utiliser cette fonctionnalité avec un processus .NET Core, vous devez installer la charge de travail de développement multiplateforme .NET Core et disposer d’un accès local au code source.

**Pour attacher un processus en cours d’exécution dans un conteneur Windows Dockr :**

1. Dans Visual Studio, sélectionnez **Déboguer > attacher au processus** (ou **CTRL + ALT + P**) pour ouvrir la boîte de dialogue **attacher au processus** .

   ![Capture d’écran de la boîte de dialogue Attacher au processus dans Visual Studio montrant un type de connexion ancrage (conteneur Windows).](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Définissez le **type de connexion** sur **Dockr (conteneur Windows)**.
3. Sélectionnez **Rechercher...** pour définir la **cible de connexion** à l’aide de la boîte de dialogue **Sélectionner un conteneur d’ancrage** .

    > [!IMPORTANT]
    > Le processus cible doit avoir la même architecture de processeur que le conteneur Windows de l’Arrimateur sur lequel il s’exécute.

   La définition de la cible sur un conteneur distant via SSH n’est pas disponible et ne peut être effectuée qu’à l’aide d’un démon de station d’accueil.

    ***Pour définir la cible sur un conteneur distant exécutant un processus via un [démon d’ancrage](https://docs.docker.com/engine/reference/commandline/dockerd/)***
    1. Spécifiez l’adresse du démon (par exemple, via TCP, IP, etc.) sous hôte de l' **ordinateur de point de connexion (facultatif)** , puis cliquez sur le lien Actualiser.

    1. Sélectionnez un conteneur en cours d’exécution auquel effectuer l’attachement après avoir réussi à vous connecter au démon, puis cliquez sur OK.

4. Choisissez le processus de conteneur correspondant dans la liste des **processus disponibles** , puis sélectionnez **attacher** pour démarrer le débogage de votre processus de conteneur C#.

    ![Capture d’écran de la boîte de dialogue Attacher au processus dans Visual Studio. Le type de connexion est défini sur docker (conteneur Windows) et le processus de dotnet.exe est sélectionné.](../debugger/media/docker-attach-complete-windows.png "Menu attacher de l’Ancreur Windows terminé")

5. Choisissez le processus de conteneur correspondant dans la liste des processus disponibles, puis choisissez **attacher** pour démarrer le débogage de votre processus de conteneur C#.