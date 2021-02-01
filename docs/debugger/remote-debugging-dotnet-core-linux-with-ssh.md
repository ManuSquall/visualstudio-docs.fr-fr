---
title: Déboguer .NET Core sur Linux
description: Déboguez .NET Core sur Linux à l’aide de Secure Shell (SSH) en vous attachant à un processus. Préparez votre application pour le débogage. Générez et déployez l’application. Attachez le débogueur.
ms.custom: SEO-VS-2020
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 599ebe86867e78d17029b2787b9f35b6755c3040
ms.sourcegitcommit: 586369f5aa61d4a0330802f718f0ceaa55d7e9c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2021
ms.locfileid: "99224351"
---
# <a name="debug-net-core-on-linux-using-ssh-by-attaching-to-a-process"></a>Déboguer .NET Core sur Linux à l’aide de SSH en vous attachant à un processus

À compter de Visual Studio 2017, vous pouvez attacher des processus .NET Core s’exécutant sur un déploiement Linux local ou distant via SSH. Cet article explique comment configurer le débogage et comment déboguer. Pour obtenir des scénarios de débogage à l’aide de conteneurs dockers, consultez [attacher à un processus en cours d’exécution sur un conteneur d’ancrage](../debugger/attach-to-process-running-in-docker-container.md) et les articles d' [outils de conteneur](../containers/edit-and-refresh.md) à la place. Pour déboguer Linux sur WSL 2 à partir de Visual Studio (pas d’attachement au processus), consultez [Déboguer des applications .net core dans WSL 2 avec Visual Studio](../debugger/debug-dotnet-core-in-wsl-2.md).

## <a name="prerequisites"></a>Prérequis

- Sur l’ordinateur Visual Studio, vous devez installer la charge de travail **développement ASP.net et Web** ou la charge de travail **développement multiplateforme .net Core** .

- Sur le serveur Linux, vous devez installer le serveur SSH, décompresser et installer avec la boucle wget. Par exemple, sur Ubuntu, vous pouvez le faire en exécutant :

  ``` cmd
  sudo apt-get install openssh-server unzip curl
  ```

- Sur le serveur Linux, [Installez le Runtime .net sur Linux](/dotnet/core/install/linux)et recherchez la page correspondant à votre distribution Linux (par exemple, Ubuntu). Le kit de développement logiciel (SDK) .NET n’est pas requis.

- Pour obtenir des instructions ASP.NET Core complètes, consultez la page [hôte ASP.net Core sur Linux avec Nginx](/aspnet/core/host-and-deploy/linux-nginx) et [Host ASP.net Core sur Linux avec Apache](/aspnet/core/host-and-deploy/linux-apache).

## <a name="prepare-your-application-for-debugging"></a>Préparer votre application pour le débogage

Pour préparer votre application pour le débogage :

- Envisagez d’utiliser une configuration de débogage lorsque vous générez l’application. Il est beaucoup plus difficile de déboguer le code compilé au détail (une configuration Release) que le code compilé par débogage. Si vous devez utiliser une configuration Release, désactivez d’abord Uniquement mon code. Pour désactiver ce paramètre, choisissez **Outils**  >  **options** de  >  **débogage**, puis désélectionnez **activer uniquement mon code**.

- Assurez-vous que votre projet est configuré pour produire des fichiers [PDB portables](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) (qui est le paramètre par défaut) et assurez-vous que les fichiers PDB se trouvent au même emplacement que la dll. Pour configurer cela dans Visual Studio, cliquez avec le bouton droit sur le projet, puis choisissez **Propriétés**  >  **générer** des informations de  >    >  **débogage** avancées.

## <a name="build-and-deploy-the-application"></a>Générer et déployer l’application

Vous pouvez utiliser plusieurs méthodes pour déployer l’application avant le débogage. Vous pouvez par exemple :

- Copiez les sources sur l’ordinateur cible et créez avec ```dotnet build``` sur l’ordinateur Linux.

- Générez l’application sur Windows, puis transférez les artefacts de build à la machine Linux. (Les artefacts de build se composent de l’application elle-même, des fichiers PDB portables, des bibliothèques Runtime dont elles peuvent dépendre, et du *.deps.js* fichier.)

Lorsque l’application est déployée, démarrez l’application.

## <a name="attach-the-debugger"></a>Attacher le débogueur

Lorsque l’application s’exécute sur l’ordinateur Linux, vous êtes prêt à attacher le débogueur.

1. Dans Visual Studio, choisissez **Déboguer**  >  **attacher au processus...**.

1. Dans la liste **type de connexion** , sélectionnez **SSH**.

1. Remplacez la **cible de connexion** par l’adresse IP ou le nom d’hôte de l’ordinateur cible.

   Si vous n’avez pas encore fourni d’informations d’identification, vous êtes invité à entrer un mot de passe et/ou un fichier de clé privée.

   Aucune configuration de port n’est requise pour la configuration, à l’exception du port sur lequel le serveur SSH s’exécute.

1. Recherchez le processus que vous souhaitez déboguer.

   Votre code s’exécute soit dans un nom de processus unique, soit dans un processus nommé dotnet. Pour trouver le processus qui vous intéresse, consultez la colonne **titre** , qui indique les arguments de ligne de commande pour le processus.

   Dans l’exemple suivant, vous voyez une liste de processus à partir d’une machine Linux distante sur un transport SSH affiché dans la boîte de dialogue **attacher au processus** .

   ![Attachement à un processus Linux](media/remote-debug-linux-over-ssh-attach.png)

1. Choisissez **Attacher**.

1. Dans la boîte de dialogue qui s’affiche, sélectionnez le type de code que vous souhaitez déboguer. Choisissez **géré (.net Core pour UNIX)**.

1. Utilisez les fonctionnalités de débogage de Visual Studio pour déboguer l’application.

   Dans l’exemple suivant, vous voyez le débogueur Visual Studio arrêté à un point d’arrêt dans le code qui s’exécute sur une machine Linux distante.

   ![Atteindre un point d’arrêt](media/remote-debug-linux-over-ssh-hit-breakpoint.png)