---
title: Résolution des problèmes liés aux erreurs du client Docker sur Windows | Microsoft Docs
description: Résolvez les problèmes que vous rencontrez lors de l’utilisation de Visual Studio pour créer et déployer des applications Web sur un ancrage sur Windows à l’aide de Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: conceptual
ms.workload: multiple
ms.date: 10/13/2017
ms.author: ghogen
ms.openlocfilehash: ca43098740a1e8e940f27eae8d2c4d405c23230b
ms.sourcegitcommit: 16d8ffc624adb716753412a22d586eae68a29ba2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2019
ms.locfileid: "70312162"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Résoudre les problèmes de développement Visual Studio avec Docker

Lorsque vous utilisez les outils de conteneur Visual Studio, vous pouvez rencontrer des problèmes lors de la génération ou du débogage de votre application. Voici quelques étapes de dépannage courantes.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Le partage de volume n’est pas activé. Activer le partage de volume dans les paramètres de Docker CE pour Windows (conteneurs Linux uniquement)

Pour résoudre ce problème :

1. Cliquez avec le bouton droit sur **docker pour Windows** dans la zone de notification, puis sélectionnez **paramètres**.
1. Sélectionnez **lecteurs partagés** , puis partagez le lecteur système avec le lecteur sur lequel le projet se trouve.

> [!NOTE]
> Si les fichiers sont partagés, vous devrez peut-être encore cliquer sur « Réinitialiser les informations d’identification... ». en bas de la boîte de dialogue afin de réactiver le partage de volume. Pour continuer après avoir réinitialisé les informations d’identification, vous devrez peut-être redémarrer Visual Studio.

![lecteurs partagés](media/troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> Les versions de Visual Studio postérieures à Visual Studio 2017 version 15,6 invitent lorsque les **lecteurs partagés** ne sont pas configurés.

### <a name="container-type"></a>Type de conteneur

Quand vous ajoutez la prise en charge de Docker à un projet, choisissez un conteneur Windows ou Linux. L’hôte Docker doit exécuter le même type de conteneur. Pour changer le type de conteneur dans l’instance de Docker en cours d’exécution, cliquez avec le bouton droit sur l’icône Docker de la zone de notification, puis choisissez **Basculer vers les conteneurs Windows...** ou **Basculer vers les conteneurs Linux...** .

## <a name="unable-to-start-debugging"></a>Impossible de démarrer le débogage

L’une des raisons peut être liée à la présence de composants de débogage obsolètes dans votre dossier de profil utilisateur. Exécutez les commandes suivantes pour supprimer ces dossiers afin que les composants de débogage les plus récents soient téléchargés lors de la prochaine session de débogage.

- del%UserProfile%\vsdbg
- del%UserProfile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Erreurs spécifiques à la mise en réseau lors du débogage de votre application

Essayez d’exécuter le script téléchargeable à partir de la mise en réseau de l' [hôte du conteneur de nettoyage](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking), ce qui permet d’actualiser les composants liés au réseau sur votre ordinateur hôte.

## <a name="mounts-denied"></a>Montages refusés

Lorsque vous utilisez l’arrimeur pour macOS, vous pouvez rencontrer une erreur référençant le dossier/usr/local/share/dotnet/sdk/NuGetFallbackFolder. Ajouter le dossier à l’onglet File Sharing (Partage de fichiers) dans Docker

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

## <a name="microsoftdockertools-github-repo"></a>Référentiel GitHub Microsoft/DockerTools

Pour tout autre problème que vous rencontrez, consultez problèmes liés à [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues) .