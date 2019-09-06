---
title: Journaux de conteneurs, variables d’environnement, accès au système de fichiers &
description: Décrit comment améliorer votre capacité à déboguer et à diagnostiquer vos applications basées sur des conteneurs dans Visual Studio à l’aide d’une fenêtre outil pour voir ce qui se passe dans les conteneurs qui hébergent votre application.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 05/06/2019
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: 3fb9a52f990a2e492c63a6e71a7cc2063110c816
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70312164"
---
# <a name="how-to-view-and-diagnose-containers-in-visual-studio"></a>Comment afficher et diagnostiquer des conteneurs dans Visual Studio

Vous pouvez voir ce qui se passe dans les conteneurs qui hébergent votre application à l’aide de la fenêtre **conteneurs** . Si vous utilisez l’invite de commandes pour exécuter les commandes de l’éditeur de ligne de commande pour afficher et diagnostiquer ce qui se passe avec vos conteneurs, cette fenêtre offre un moyen plus pratique de surveiller vos conteneurs sans quitter l’IDE de Visual Studio.

> [!NOTE]
> La fenêtre conteneurs est actuellement disponible en tant qu’extension d’aperçu que vous pouvez [Télécharger](https://aka.ms/vscontainerspreview) pour Visual Studio 2019.

## <a name="prerequisites"></a>Prérequis

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- Installer [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
- Installer l' [extension de fenêtre conteneurs](https://aka.ms/vscontainerspreview)

## <a name="view-information-about-your-containers"></a>Afficher des informations sur vos conteneurs

La fenêtre **conteneurs** s’ouvre automatiquement lorsque vous démarrez un projet .net en conteneur. Pour afficher vos conteneurs dans Visual Studio à tout moment, utilisez **CTRL**+**Q** pour activer la zone de recherche Visual Studio, puis `Containers` tapez et choisissez le premier élément. Vous pouvez également ouvrir la fenêtre **conteneurs** à partir du menu principal. Utilisez le chemin d’accès au menu **Afficher** > les**autres** > **conteneurs**Windows.  

![Capture d’écran de l’onglet environnement dans la fenêtre conteneurs](media/view-and-diagnose-containers/container-window.png)

Sur le côté gauche, vous voyez la liste des conteneurs sur votre ordinateur local. Les conteneurs associés à votre solution s’affichent sous **conteneurs de solutions**. À droite, vous voyez un volet avec des onglets pour l' **environnement**, les **ports**, les **journaux**et les **fichiers**.

> [!TIP]
> Vous pouvez facilement personnaliser l’emplacement où la fenêtre outil **conteneurs** est ancrée dans Visual Studio. Consultez [Personnalisation des dispositions de fenêtres dans Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio). Par défaut, la fenêtre **conteneurs** est ancrée avec la fenêtre **Espion** lorsque le débogueur est en cours d’exécution.

## <a name="view-environment-variables"></a>Afficher les variables d’environnement

L’onglet **environnement** affiche les variables d’environnement dans le conteneur. Pour le conteneur de votre application, vous pouvez définir ces variables de nombreuses façons, par exemple dans le fichier dockerfile, dans un fichier. env ou à l’aide de l’option-e quand vous démarrez un conteneur à l’aide d’une commande Dockr.

![Capture d’écran de l’onglet environnement dans la fenêtre conteneurs](media/view-and-diagnose-containers/container-environment-vars.png)

> [!NOTE]
> Les modifications apportées aux variables d’environnement ne sont pas reflétées en temps réel. En outre, les variables d’environnement de cet onglet sont les variables d’environnement système sur le conteneur et ne reflètent pas les variables d’environnement utilisateur locales pour l’application.

## <a name="view-port-mappings"></a>Afficher les mappages de ports

Sous l’onglet **ports** , vous pouvez vérifier les mappages de port en vigueur pour votre conteneur.

![Capture d’écran de l’onglet ports dans la fenêtre conteneurs](media/view-and-diagnose-containers/container-ports.png)

Les ports connus sont liés. ainsi, si le contenu est disponible sur un port, vous pouvez cliquer sur le lien pour ouvrir le navigateur.

## <a name="view-logs"></a>Afficher les journaux d’activité

L’onglet **journaux** affiche les résultats de la `docker logs` commande. Par défaut, l’onglet affiche les flux STDOUT et stderr sur un conteneur, mais vous pouvez configurer la sortie. Pour plus d’informations, consultez [journalisation](https://docs.docker.com/config/containers/logging/)de l’ancrage.  Par défaut, l’onglet **journaux** diffuse les journaux, mais vous pouvez le désactiver en choisissant le bouton **arrêter** sous l’onglet.

![Capture d’écran de l’onglet journaux dans la fenêtre conteneurs](media/view-and-diagnose-containers/containers-logs.jpg)

Pour effacer les journaux, utilisez le bouton **Effacer** sous l’onglet **journaux** .  Pour récupérer tous les journaux, utilisez le bouton **Actualiser** .

> [!NOTE]
> Visual Studio redirige automatiquement stdout et stderr vers la fenêtre **sortie** . par conséquent, les conteneurs démarrés à partir de Visual Studio (autrement dit, les conteneurs de la section **conteneurs de solution** ) n’affichent pas les journaux dans cet onglet. Utilisez la fenêtre de **sortie** à la place.

## <a name="view-the-filesystem"></a>Afficher le système de fichiers

Dans l’onglet **fichiers** , vous pouvez afficher le système de fichiers du conteneur, y compris le dossier d’application qui contient votre projet.

![Capture d’écran de l’onglet fichiers dans la fenêtre conteneurs](media/view-and-diagnose-containers/container-filesystem.png)

Pour ouvrir des fichiers dans Visual Studio, accédez au fichier et double-cliquez dessus, ou cliquez avec le bouton droit et choisissez **ouvrir**. Visual Studio ouvre les fichiers en mode lecture seule.

![Capture d’écran de l’ouverture d’un fichier dans Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

À l’aide de l’onglet **fichiers** , vous pouvez afficher les journaux des applications, tels que les journaux IIS, les fichiers de configuration et d’autres fichiers de contenu dans le système de fichiers de votre conteneur.

## <a name="start-stop-and-remove-containers"></a>Démarrer, arrêter et supprimer des conteneurs

Par défaut, la fenêtre **conteneurs** affiche tous les conteneurs sur l’ordinateur géré par dockr. Vous pouvez utiliser les boutons de la barre d’outils pour démarrer, arrêter ou supprimer (supprimer) un conteneur dont vous n’avez plus besoin.  Cette liste est mise à jour dynamiquement au fur et à mesure de la création ou de la suppression de conteneurs.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les outils de conteneur disponibles dans Visual Studio, consultez [vue d’ensemble des outils de conteneur](overview.md).

## <a name="see-also"></a>Voir aussi

[Développement de conteneurs dans Visual Studio](/visualstudio/containers)

[Marketplace des extensions pour Visual Studio](https://marketplace.visualstudio.com/)
