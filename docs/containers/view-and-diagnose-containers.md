---
title: Journaux de conteneurs, variables d’environnement et accès au système de fichiers de l’ancrage
description: Décrit comment améliorer votre capacité à déboguer et à diagnostiquer vos applications basées sur des conteneurs dans Visual Studio à l’aide d’une fenêtre outil pour voir ce qui se passe dans les conteneurs qui hébergent votre application.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 01/20/2020
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: c870378cf277a6008f17ec42d960e07e18a53e86
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283123"
---
# <a name="how-to-view-and-diagnose-containers-and-images-in-visual-studio"></a>Comment afficher et diagnostiquer des conteneurs et des images dans Visual Studio

Vous pouvez voir ce qui se passe dans les conteneurs qui hébergent votre application à l’aide de la fenêtre **conteneurs** . Si vous utilisez l’invite de commandes pour exécuter les commandes de l’éditeur de ligne de commande pour afficher et diagnostiquer ce qui se passe avec vos conteneurs, cette fenêtre offre un moyen plus pratique de surveiller vos conteneurs sans quitter l’IDE de Visual Studio.

## <a name="prerequisites"></a>Prérequis

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual studio 2019 version 16,4 Preview 2](https://visualstudio.microsoft.com/downloads) ou version ultérieure, ou si vous utilisez une version antérieure de visual studio 2019, installez l' [extension de fenêtre conteneurs](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-containers-tools-extensions).

## <a name="view-information-about-your-containers"></a>Afficher des informations sur vos conteneurs

La fenêtre **conteneurs** s’ouvre automatiquement lorsque vous démarrez un projet .net en conteneur. Pour afficher vos conteneurs dans Visual Studio à tout moment, utilisez **CTRL** + **Q** pour activer la zone de recherche Visual Studio, puis tapez `Containers` et choisissez le premier élément. Vous pouvez également ouvrir la fenêtre **conteneurs** à partir du menu principal. Utilisez le chemin d’accès au menu **Afficher**les  >  **autres**  >  **conteneurs**Windows.  

![Capture d’écran de l’onglet environnement dans la fenêtre conteneurs](media/view-and-diagnose-containers/container-window.png)

Sur le côté gauche, vous voyez la liste des conteneurs sur votre ordinateur local. Les conteneurs associés à votre solution s’affichent sous **conteneurs de solutions**. À droite, vous voyez un volet avec des onglets pour l' **environnement**, les **ports**, les **journaux**et les **fichiers**.

> [!TIP]
> Vous pouvez facilement personnaliser l’emplacement où la fenêtre outil **conteneurs** est ancrée dans Visual Studio. Consultez [Personnalisation des dispositions de fenêtres dans Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Par défaut, la fenêtre **conteneurs** est ancrée avec la fenêtre **Espion** lorsque le débogueur est en cours d’exécution.

## <a name="view-environment-variables"></a>Afficher les variables d’environnement

L’onglet **environnement** affiche les variables d’environnement dans le conteneur. Pour le conteneur de votre application, vous pouvez définir ces variables de nombreuses façons, par exemple dans le fichier dockerfile, dans un fichier. env ou à l’aide de l’option-e quand vous démarrez un conteneur à l’aide d’une commande Dockr.

![Capture d’écran de l’onglet environnement dans la fenêtre conteneurs](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> Les modifications apportées aux variables d’environnement ne sont pas reflétées en temps réel. En outre, les variables d’environnement de cet onglet sont les variables d’environnement système sur le conteneur et ne reflètent pas les variables d’environnement utilisateur locales pour l’application.

## <a name="view-port-mappings"></a>Afficher les mappages de ports

Sous l’onglet **ports** , vous pouvez vérifier les mappages de port en vigueur pour votre conteneur.

![Capture d’écran de l’onglet ports dans la fenêtre conteneurs](media/view-and-diagnose-containers/containers-ports.png)

Les ports connus sont liés. ainsi, si le contenu est disponible sur un port, vous pouvez cliquer sur le lien pour ouvrir le navigateur.

## <a name="view-logs"></a>Afficher les journaux d’activité

L’onglet **journaux** affiche les résultats de la `docker logs` commande. Par défaut, l’onglet affiche les flux STDOUT et stderr sur un conteneur, mais vous pouvez configurer la sortie. Pour plus d’informations, consultez [journalisation](https://docs.docker.com/config/containers/logging/)de l’ancrage.  Par défaut, l’onglet **journaux** diffuse les journaux, mais vous pouvez le désactiver en choisissant le bouton **arrêter** sous l’onglet.

![Capture d’écran de l’onglet journaux dans la fenêtre conteneurs](media/view-and-diagnose-containers/containers-logs.png)

Pour effacer les journaux, utilisez le bouton **Effacer** sous l’onglet **journaux** .  Pour récupérer tous les journaux, utilisez le bouton **Actualiser** .

> [!NOTE]
> Visual Studio redirige automatiquement stdout et stderr vers la fenêtre **sortie** lorsque vous exécutez sans débogage avec des conteneurs Windows. ainsi, les conteneurs Windows démarrés à partir de Visual Studio à l’aide de la **touche Ctrl** + **F5** n’affichent pas les journaux dans cet onglet ; utilisez la fenêtre **sortie** à la place.

## <a name="view-the-filesystem"></a>Afficher le système de fichiers

Dans l’onglet **fichiers** , vous pouvez afficher le système de fichiers du conteneur, y compris le dossier d’application qui contient votre projet.

![Capture d’écran de l’onglet fichiers dans la fenêtre conteneurs](media/view-and-diagnose-containers/container-filesystem.png)

Pour ouvrir des fichiers dans Visual Studio, accédez au fichier et double-cliquez dessus, ou cliquez avec le bouton droit et choisissez **ouvrir**. Visual Studio ouvre les fichiers en mode lecture seule.

![Capture d’écran de l’ouverture d’un fichier dans Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

À l’aide de l’onglet **fichiers** , vous pouvez afficher les journaux des applications, tels que les journaux IIS, les fichiers de configuration et d’autres fichiers de contenu dans le système de fichiers de votre conteneur.

## <a name="start-stop-and-remove-containers"></a>Démarrer, arrêter et supprimer des conteneurs

Par défaut, la fenêtre **conteneurs** affiche tous les conteneurs sur l’ordinateur géré par dockr. Vous pouvez utiliser les boutons de la barre d’outils pour démarrer, arrêter ou supprimer (supprimer) un conteneur dont vous n’avez plus besoin.  Cette liste est mise à jour dynamiquement au fur et à mesure de la création ou de la suppression de conteneurs.

## <a name="open-a-terminal-window-in-a-running-container"></a>Ouvrir une fenêtre de terminal dans un conteneur en cours d’exécution

Vous pouvez ouvrir une fenêtre de terminal (invite de commandes ou shell interactif) dans le conteneur à l’aide du bouton **ouvrir la fenêtre de terminal** dans la fenêtre de **conteneur** .

![Capture d’écran de la fenêtre ouvrir un terminal dans la fenêtre conteneurs](media/view-and-diagnose-containers/containers-open-terminal-window.png)

Pour les conteneurs Windows, l’invite de commandes Windows s’ouvre. Pour les conteneurs Linux, il ouvre une fenêtre à l’aide de l’interpréteur de commandes bash.

![Capture d’écran de la fenêtre bash](media/view-and-diagnose-containers/container-bash-window.png)

En règle générale, la fenêtre de terminal s’ouvre en dehors de Visual Studio sous la forme d’une fenêtre distincte. Si vous souhaitez qu’un environnement de ligne de commande intégré à l’IDE de Visual Studio soit une fenêtre outil Ancrable, vous pouvez installer le [Terminal Whack Whack](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal).

## <a name="attach-the-debugger-to-a-process"></a>Attacher le débogueur à un processus

Vous pouvez attacher le débogueur à un processus en cours d’exécution dans le conteneur à l’aide du bouton **attacher au processus** de la barre d’outils de la fenêtre conteneurs. Lorsque vous utilisez ce bouton, la boîte de dialogue **attacher au processus** apparaît et affiche les processus disponibles qui s’exécutent dans le conteneur.  

![Capture d’écran de la boîte de dialogue Attacher au processus](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

Vous pouvez attacher des processus managés dans le conteneur. Pour rechercher un processus dans un autre conteneur, utilisez le bouton **Rechercher** et sélectionnez un autre conteneur dans la boîte de dialogue **Sélectionner un conteneur d’ancrage** .

## <a name="viewing-images"></a>Affichage des images

Vous pouvez également afficher des images sur l’ordinateur local à l’aide de l’onglet **images** de la fenêtre **conteneurs** . Les images extraites des référentiels externes sont regroupées dans un contrôle TreeView. Sélectionnez une image pour inspecter les détails de l’image.

Pour supprimer une image, cliquez avec le bouton droit sur l’image dans le TreeView, choisissez **supprimer**ou sélectionnez l’image, puis utilisez le bouton **supprimer** dans la barre d’outils.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les outils de conteneur disponibles dans Visual Studio, consultez [vue d’ensemble des outils de conteneur](overview.md).

## <a name="see-also"></a>Voir aussi

[Développement de conteneurs dans Visual Studio](/visualstudio/containers)

[Marketplace des extensions pour Visual Studio](https://marketplace.visualstudio.com/)
