---
title: Débogage à distance de .NET Core sur Linux | Microsoft Docs
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d66181f5e6720348e18c34b735ef29e24c0111a
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796301"
---
# <a name="remote-debug-net-core-on-linux-using-ssh"></a>Déboguer à distance .NET Core sur Linux à l’aide de SSH

À compter de Visual Studio 2017, vous pouvez attacher des processus .NET Core s’exécutant sur Linux sur SSH. Cet article explique comment configurer le débogage et comment déboguer.

## <a name="prerequisites"></a>Prérequis

Sur l’ordinateur Visual Studio, vous devez installer la charge de travail **développement ASP.net et Web** ou la charge de travail **développement multiplateforme .net Core** .

Sur le serveur Linux, vous devez installer le serveur SSH, décompresser et installer avec la boucle wget. Par exemple, sur Ubuntu, vous pouvez le faire en exécutant :

``` cmd
sudo apt-get install openssh-server unzip curl
```

## <a name="build-and-deploy-the-application"></a>Générer et déployer l’application

Pour préparer votre application pour le débogage :

- Envisagez d’utiliser une configuration de débogage lorsque vous générez l’application. Il est beaucoup plus difficile de déboguer le code compilé au détail (une configuration Release) que le code compilé par débogage. Si vous devez utiliser une configuration Release, désactivez d’abord Uniquement mon code. Pour désactiver ce paramètre, choisissez **Outils**  >  **options** de  >  **débogage** , puis désélectionnez **activer uniquement mon code** .

- Assurez-vous que votre projet est configuré pour produire des fichiers [PDB portables](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) (qui est le paramètre par défaut) et assurez-vous que les PBDs se trouvent dans le même emplacement que la dll. Pour configurer cela dans Visual Studio, cliquez avec le bouton droit sur le projet, puis choisissez **Propriétés**  >  **générer** des informations de  >  **Advanced**  >  **débogage** avancées.

Vous pouvez utiliser plusieurs méthodes pour déployer l’application avant le débogage. Par exemple, vous pouvez :

- Copiez les sources sur l’ordinateur cible et créez avec ```dotnet build``` sur l’ordinateur Linux.

- Générez l’application sur Windows, puis transférez les artefacts de build à la machine Linux. (Les artefacts de build se composent de l’application elle-même, des bibliothèques Runtime dont elles peuvent dépendre, et du *.deps.jssur* le fichier.)

## <a name="attach-the-debugger"></a>Attacher le débogueur

Une fois les ordinateurs configurés, démarrez l’application sur l’ordinateur Linux, puis vous êtes prêt à attacher le débogueur.

1. Dans Visual Studio, choisissez **Déboguer**  >  **attacher au processus...** .

1. Dans la liste **type de connexion** , sélectionnez **SSH** .

1. Remplacez la **cible de connexion** par l’adresse IP ou le nom d’hôte de l’ordinateur cible.

1. Recherchez le processus que vous souhaitez déboguer.

   Votre code s’exécute soit dans un nom de processus unique, soit dans un processus nommé dotnet. Pour trouver le processus qui vous intéresse, consultez la colonne **titre** , qui indique les arguments de ligne de commande pour le processus.

   Dans l’exemple suivant, vous voyez une liste de processus à partir d’une machine Linux distante sur un transport SSH affiché dans la boîte de dialogue **attacher au processus** .

   ![Attachement à un processus Linux](media/remote-debug-linux-over-ssh-attach.png)

1. Choisissez **Attacher** .

1. Dans la boîte de dialogue qui s’affiche, sélectionnez le type de code que vous souhaitez déboguer. Choisissez **géré (.net Core pour UNIX)** .

1. Utilisez les fonctionnalités de débogage de Visual Studio pour déboguer l’application.

   Dans l’exemple suivant, vous voyez le débogueur Visual Studio arrêté à un point d’arrêt dans le code qui s’exécute sur une machine Linux distante.

   ![Atteindre un point d’arrêt](media/remote-debug-linux-over-ssh-hit-breakpoint.png)