---
title: Résolution des problèmes liés aux erreurs du client Docker sur Windows | Microsoft Docs
description: Résolvez les problèmes d’utilisation de Visual Studio pour créer et déployer des applications web dans Docker sur Windows avec Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: troubleshooting
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 31b9d8649abed0f9901aa872ff3939c25e3025b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87235106"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Résoudre les problèmes de développement Visual Studio avec Docker

Lorsque vous utilisez les outils de conteneur Visual Studio, vous pouvez rencontrer des problèmes lors de la génération ou du débogage de votre application. Voici certains problèmes courants et les étapes de dépannage correspondantes.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Le partage de volume n’est pas activé. Activez le volume de partage dans les paramètres de Docker CE pour Windows (uniquement pour les conteneurs Linux)

Pour résoudre ce problème :

1. Dans la zone de notification, cliquez avec le bouton droit sur **Docker pour Windows**, puis sélectionnez **Paramètres**.
1. Sélectionnez **Lecteurs partagés**, puis partagez le lecteur système et le lecteur où se trouve le projet.

> [!NOTE]
> Si les fichiers sont affichés comme partagés, cliquez sur le lien « Réinitialiser les informations d’identification... » en bas de la boîte de dialogue pour réactiver le partage de volume. Pour continuer après la réinitialisation des informations d’identification, vous devrez peut-être redémarrer Visual Studio.

![lecteurs partagés](media/troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> Les versions de Visual Studio postérieures à Visual Studio 2017 version 15,6 invitent lorsque les **lecteurs partagés** ne sont pas configurés.

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

## <a name="docker-users-group"></a>Groupe d’utilisateurs de l’ancrage

Vous pouvez rencontrer l’erreur suivante dans Visual Studio lors de l’utilisation de conteneurs :

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Vous devez être membre du groupe « docker-utilisateurs » pour avoir les autorisations nécessaires pour utiliser les conteneurs de l’ancrage.  Pour vous ajouter au groupe dans Windows 10, procédez comme suit :

1. Dans le menu Démarrer, ouvrez **gestion**de l’ordinateur.
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

Par défaut, Dockr stocke les images dans le dossier *% ProgramData%/docker/* , qui se trouve généralement sur le lecteur système, * C:\ProgramData\Docker \* . Pour empêcher les images d’occuper de l’espace sur le lecteur système, vous pouvez modifier l’emplacement du dossier d’images.  À partir de l’icône de l’Ancreur, dans la barre des tâches, ouvrez paramètres de l’ancrage, choisissez **démon**et passez de **basique** à **avancé**. Dans le volet de modification, ajoutez le `graph` paramètre de propriété avec la valeur de l’emplacement souhaité pour les images de l’ancrage :

```json
    "graph": "D:\\mypath\\images"
```

![Capture d’écran du paramètre d’emplacement de l’image de l’ancrage](media/troubleshooting-docker-errors/docker-settings-image-location.png)

Cliquez sur **appliquer** pour redémarrer l’ancrage. Les étapes suivantes modifient le fichier de configuration à *% ProgramData% \docker\config\daemon.jssur*. Les images générées précédemment ne sont pas déplacées.

## <a name="microsoftdockertools-github-repo"></a>Référentiel GitHub Microsoft/DockerTools

Pour tout autre problème que vous rencontrez, consultez les problèmes répertoriés dans [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues).

## <a name="see-also"></a>Voir aussi

- [Résolution des problèmes de Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)