---
title: Résolution des problèmes liés aux erreurs du client Docker sur Windows | Microsoft Docs
description: Résolvez les problèmes d’utilisation de Visual Studio pour créer et déployer des applications web dans Docker sur Windows avec Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jmartens
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: troubleshooting
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 5f48b5c06e91b9c05e6edc7e2a1738aeb677a7ba
ms.sourcegitcommit: 69456d802203d21dabc3ae8662547a3241c24f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2021
ms.locfileid: "110235909"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Résoudre les problèmes de développement Visual Studio avec Docker

Lorsque vous utilisez les outils de conteneur Visual Studio, vous pouvez rencontrer des problèmes lors de la génération ou du débogage de votre application. Voici certains problèmes courants et les étapes de dépannage correspondantes.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Le partage de volume n’est pas activé. Activez le volume de partage dans les paramètres de Docker CE pour Windows (uniquement pour les conteneurs Linux)

Le partage de fichiers doit être géré uniquement si vous utilisez Hyper-V avec l’arrimeur. Si vous utilisez WSL 2, les étapes suivantes ne sont pas nécessaires et l’option de partage de fichiers n’est pas visible. Pour résoudre ce problème :

1. Dans la zone de notification, cliquez avec le bouton droit sur **Docker pour Windows**, puis sélectionnez **Paramètres**.
1. Sélectionnez **ressources**  >  **partage de fichiers** et partagez le dossier auquel vous devez accéder. Le partage de l’ensemble de votre lecteur système est possible, mais n’est pas recommandé.

    :::image type="content" source="media//troubleshooting-docker-errors/docker-settings-image.png" alt-text="Lecteurs partagés":::

> [!TIP]
> Les versions de Visual Studio ultérieures à Visual Studio 2017 version 15,6 demandent quand les **lecteurs partagés** ne sont pas configurés.

## <a name="unable-to-start-debugging"></a>Impossible de démarrer le débogage

L’une des raisons peut être liée à la présence de composants de débogage obsolètes dans votre dossier de profil utilisateur. Exécutez les commandes suivantes pour supprimer ces dossiers. Les composants de débogage les plus récents seront téléchargés lors de la session de débogage suivante.

- del %userprofile%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Erreurs de réseau lors du débogage de votre application

Essayez d’exécuter le script téléchargeable à partir de [Cleanup Container Host Networking](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking). Ce script met à jour les composants réseau sur votre machine hôte.

## <a name="mounts-denied"></a>Montages refusés

Quand vous utilisez Docker pour macOS, vous pouvez rencontrer une erreur référençant le dossier /usr/local/share/dotnet/sdk/NuGetFallbackFolder. Ajoutez le dossier à l’onglet File Sharing dans Docker.

## <a name="docker-users-group"></a>Groupe d’utilisateurs de l’ancrage

Vous pouvez rencontrer l’erreur suivante dans Visual Studio lors de l’utilisation de conteneurs :

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Vous devez être membre du groupe « docker-utilisateurs » pour avoir les autorisations nécessaires pour utiliser les conteneurs de l’ancrage.  Pour vous ajouter au groupe dans Windows 10, procédez comme suit :

1. Dans le menu Démarrer, ouvrez **gestion** de l’ordinateur.
1. Développez **utilisateurs et groupes locaux**, puis choisissez **groupes**.
1. Recherchez le groupe **dockr-Users** , cliquez avec le bouton droit et choisissez **Ajouter au groupe**.
1. Ajoutez vos comptes d’utilisateur.
1. Déconnectez-vous, puis reconnectez-vous pour que ces modifications prennent effet.

Vous pouvez également utiliser la `net localgroup` commande à l’invite de commandes de l’administrateur pour ajouter des utilisateurs à des groupes spécifiques.

```cmd
net localgroup docker-users DOMAIN\username /add
```

Dans PowerShell, utilisez la fonction [Add-LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember) .

## <a name="low-disk-space"></a>Espace disque insuffisant

Par défaut, Dockr stocke les images dans le dossier *% ProgramData%/docker/* , qui se trouve généralement sur le lecteur système, * C:\ProgramData\Docker \* . Pour empêcher les images d’occuper de l’espace sur le lecteur système, vous pouvez modifier l’emplacement du dossier d’images. Pour cela, procédez de la façon suivante :

 1. Cliquez avec le bouton droit sur l’icône de l’ancrage dans la barre des tâches et sélectionnez **paramètres**.
 1. Sélectionnez **moteur** de l’ancrage. 
 1. Dans le volet de modification, ajoutez le `graph` paramètre de propriété avec la valeur de l’emplacement souhaité pour les images de l’ancrage :

```json
    "graph": "D:\\mypath\\images"
```

:::image type="content" source="media/troubleshooting-docker-errors/docker-daemon-settings.png" alt-text="Capture d’écran du partage de fichiers de l’arrimeur":::

Cliquez sur **appliquer & redémarrer**. Les étapes suivantes modifient le fichier de configuration à *% ProgramData% \docker\config\daemon.jssur*. Les images générées précédemment ne sont pas déplacées.

## <a name="container-type-mismatch"></a>Incompatibilité de type de conteneur

Quand vous ajoutez la prise en charge de Docker à un projet, choisissez un conteneur Windows ou Linux. Si l’hôte du serveur d’ancrage n’est pas configuré pour exécuter le même type de conteneur que la cible du projet, vous verrez probablement une erreur semblable à celle ci-dessous :

:::image type="content" source="media/troubleshooting-docker-errors/docker-host-config-change-linux-to-windows.png" alt-text="Capture d’écran de l’hôte et de l’incompatibilité de projet de l’arrimeur":::

Pour résoudre ce problème :

- Cliquez avec le bouton droit sur l’icône de Docker pour Windows dans la barre d’état système, puis choisissez **basculer vers les conteneurs Windows.** .. ou **basculer vers les conteneurs Linux...**.

## <a name="microsoftdockertools-github-repo"></a>Référentiel GitHub Microsoft/DockerTools

Pour tout autre problème que vous rencontrez, consultez les problèmes répertoriés dans [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues).

## <a name="see-also"></a>Voir aussi

- [Résolution des problèmes de Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
