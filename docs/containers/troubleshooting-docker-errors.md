---
title: Résolution des problèmes liés aux erreurs du client Docker sur Windows | Microsoft Docs
description: Résolvez les problèmes d’utilisation de Visual Studio pour créer et déployer des applications web dans Docker sur Windows avec Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: conceptual
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: d8aa3028a12bcfb49f2663b2bea688baf14fd7f2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027282"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Résoudre les problèmes de développement Visual Studio avec Docker

Lorsque vous travaillez avec Visual Studio Container Tools, vous pouvez rencontrer des problèmes lors de la construction ou de la débogage de votre application. Voici certains problèmes courants et les étapes de dépannage correspondantes.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Le partage de volume n’est pas activé. Activez le volume de partage dans les paramètres de Docker CE pour Windows (uniquement pour les conteneurs Linux)

Pour résoudre ce problème :

1. Dans la zone de notification, cliquez avec le bouton droit sur **Docker pour Windows**, puis sélectionnez **Paramètres**.
1. Sélectionnez **Lecteurs partagés**, puis partagez le lecteur système et le lecteur où se trouve le projet.

> [!NOTE]
> Si les fichiers sont affichés comme partagés, cliquez sur le lien « Réinitialiser les informations d’identification... » en bas de la boîte de dialogue pour réactiver le partage de volume. Pour continuer après la réinitialisation des informations d’identification, vous devrez peut-être redémarrer Visual Studio.

![lecteurs partagés](media/troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> Les versions Visual Studio plus tard que Visual Studio 2017 version 15.6 invite lorsque **les lecteurs partagés** ne sont pas configurés.

### <a name="container-type"></a>Type de conteneur

Quand vous ajoutez la prise en charge de Docker à un projet, choisissez un conteneur Windows ou Linux. L’hôte Docker doit exécuter le même type de conteneur. Pour changer le type de conteneur dans l’instance de Docker en cours d’exécution, cliquez avec le bouton droit sur l’icône Docker de la zone de notification, puis choisissez **Basculer vers les conteneurs Windows...** ou **Basculer vers les conteneurs Linux...**.

## <a name="unable-to-start-debugging"></a>Impossible de démarrer le débogage

L’une des raisons peut être liée à la présence de composants de débogage obsolètes dans votre dossier de profil utilisateur. Exécutez les commandes suivantes pour supprimer ces dossiers. Les composants de débogage les plus récents seront téléchargés lors de la session de débogage suivante.

- del %userprofile%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Erreurs de réseau lors du débogage de votre application

Essayez d’exécuter le script téléchargeable à partir de [Cleanup Container Host Networking](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking). Ce script met à jour les composants réseau sur votre machine hôte.

## <a name="mounts-denied"></a>Montages refusés

Quand vous utilisez Docker pour macOS, vous pouvez rencontrer une erreur référençant le dossier /usr/local/share/dotnet/sdk/NuGetFallbackFolder. Ajouter le dossier à l’onglet File Sharing (Partage de fichiers) dans Docker

## <a name="docker-users-group"></a>Groupe d’utilisateurs Docker

Vous pourriez rencontrer l’erreur suivante dans Visual Studio lorsque vous travaillez avec des conteneurs :

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Vous devez être membre du groupe des « docker-utilisateurs » afin d’avoir des autorisations de travailler avec des conteneurs Docker.  Pour vous ajouter au groupe dans Windows 10, suivez ces étapes :

1. Du menu Démarrer, open **Computer Management**.
1. Élargir **les utilisateurs locaux et les groupes**, et choisir les **groupes**.
1. Trouvez le groupe **docker-utilisateurs,** cliquez à droite et choisissez **Ajouter au groupe**.
1. Ajoutez votre compte d’utilisateur ou vos comptes.
1. Déconnectez-vous et connectez-vous à nouveau pour que ces modifications prennent effet.

Vous pouvez également `net localgroup` utiliser la commande à l’invitation de commande d’administrateur pour ajouter des utilisateurs à des groupes spécifiques.

```cmd
net localgroup docker-users DOMAIN\username /add
```

Dans PowerShell, utilisez la fonction [Add-LocalGroupMember.](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember)

## <a name="low-disk-space"></a>Espace disque insuffisant

Par défaut, Docker stocke des images dans le *dossier %ProgramData%/Docker/folder,* qui est\*généralement sur le lecteur du système, C: 'ProgramData’Docker . Pour empêcher les images de prendre de l’espace précieux sur le lecteur du système, vous pouvez modifier l’emplacement du dossier d’image.  De l’icône Docker sur la barre de travail, ouvrir les paramètres Docker, choisir **Daemon**, et passer de **Basic** à **Advanced**. Dans le volet d’édition, ajoutez le `graph` paramètre de propriété avec la valeur de votre emplacement désiré pour les images Docker :

```json
    "graph": "D:\\mypath\\images"
```

![Capture d’écran du paramètre de localisation d’image De Docker](media/troubleshooting-docker-errors/docker-settings-image-location.png)

Cliquez **sur Appliquer** pour redémarrer Docker. Ces étapes modifient le fichier de configuration à *%ProgramData%-docker-config-daemon.json*. Les images précédemment construites ne sont pas déplacées.

## <a name="microsoftdockertools-github-repo"></a>Référentiel GitHub Microsoft/DockerTools

Pour tout autre problème que vous rencontrez, consultez les problèmes répertoriés dans [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues).