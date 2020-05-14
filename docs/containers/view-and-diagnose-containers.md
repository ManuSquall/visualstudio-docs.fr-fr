---
title: Journaux de conteneurs Docker, variables de l’environnement et accès au système de fichiers
description: Décrit comment améliorer votre capacité à débog et diagnostiquer vos applications basées sur des conteneurs dans Visual Studio en utilisant une fenêtre d’outils pour voir ce qui se passe à l’intérieur des conteneurs qui hébergent votre application.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 01/20/2020
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: b4670c003c06f8d16979589a4dce5abf33d5e27d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027303"
---
# <a name="how-to-view-and-diagnose-containers-and-images-in-visual-studio"></a>Comment voir et diagnostiquer les conteneurs et les images dans Visual Studio

Vous pouvez voir ce qui se passe à l’intérieur des conteneurs qui hébergent votre application en utilisant la fenêtre **Containers.** Si vous avez l’habitude d’utiliser l’invite de commande pour exécuter les commandes Docker pour afficher et diagnostiquer ce qui se passe avec vos conteneurs, cette fenêtre fournit un moyen plus pratique de surveiller vos conteneurs sans quitter l’IDE Visual Studio.

## <a name="prerequisites"></a>Conditions préalables requises

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019 version 16.4 Aperçu 2](https://visualstudio.microsoft.com/downloads) ou plus tard, ou si vous utilisez une version antérieure de Visual Studio 2019, installez l’extension [de fenêtre Containers](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-containers-tools-extensions).

## <a name="view-information-about-your-containers"></a>Afficher les informations sur vos conteneurs

La fenêtre **Containers** s’ouvre automatiquement lorsque vous démarrez un projet .NET conteneurisé. Pour voir vos conteneurs dans Visual Studio à tout moment, utilisez **Ctrl**+**Q** pour activer la boîte de recherche Visual Studio, et tapez `Containers` et choisissez le premier élément. Vous pouvez également ouvrir la fenêtre **Containers** à partir du menu principal. Utilisez le chemin du menu **Voir** > **d’autres** > **conteneurs**Windows .  

![Capture d’écran de l’onglet Environnement dans la fenêtre des conteneurs](media/view-and-diagnose-containers/container-window.png)

Sur le côté gauche, vous voyez la liste des conteneurs sur votre machine locale. Les conteneurs associés à votre solution sont indiqués sous **les conteneurs Solution**. À droite, vous voyez une vitre avec des onglets pour **l’environnement,** **ports,** **journaux,** et **les fichiers**.

> [!TIP]
> Vous pouvez facilement personnaliser l’endroit où la fenêtre de l’outil **Containers** est amarrée dans Visual Studio. Voir [personnaliser les mises en page des fenêtres dans Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Par défaut, la fenêtre **Containers** est amarrée à la fenêtre **Watch** lorsque le débbuggeur est en marche.

## <a name="view-environment-variables"></a>Afficher les variables de l’environnement

**L’onglet Environnement** indique les variables de l’environnement dans le conteneur. Pour le conteneur de votre application, vous pouvez définir ces variables de plusieurs façons, par exemple, dans le Dockerfile, dans un fichier .env, ou en utilisant l’option e lorsque vous démarrez un conteneur à l’aide d’une commande Docker.

![Capture d’écran de l’onglet Environnement dans la fenêtre des conteneurs](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> Toute modification des variables de l’environnement ne se reflète pas en temps réel. En outre, les variables de l’environnement dans cet onglet sont les variables de l’environnement du système sur le conteneur, et ne reflètent pas les variables de l’environnement utilisateur local à l’application.

## <a name="view-port-mappings"></a>Afficher les cartographies portuaires

Sur l’onglet **Ports,** vous pouvez vérifier les cartes portuaires en vigueur pour votre conteneur.

![Capture d’écran de l’onglet Ports dans la fenêtre des conteneurs](media/view-and-diagnose-containers/containers-ports.png)

Les ports bien connus sont liés, donc s’il y a du contenu disponible sur un port, vous pouvez cliquer sur le lien pour ouvrir le navigateur.

## <a name="view-logs"></a>Afficher les journaux d’activité

**L’onglet Logs** affiche `docker logs` les résultats de la commande. Par défaut, l’onglet affiche des flux stdout et stderr sur un conteneur, mais vous pouvez configurer la sortie. Pour plus de détails, voir [Dockerlogging](https://docs.docker.com/config/containers/logging/).  Par défaut, **l’onglet Logs** diffuse les journaux, mais vous pouvez désactiver cela en choisissant le bouton **Stop** sur l’onglet.

![Capture d’écran de l’onglet Logs dans la fenêtre des conteneurs](media/view-and-diagnose-containers/containers-logs.png)

Pour effacer les journaux, utilisez le bouton **Clear** sur l’onglet **Logs.**  Pour obtenir tous les journaux, utilisez le bouton **Rafraîchir.**

> [!NOTE]
> Visual Studio redirige automatiquement stdout et stderr à la fenêtre **de sortie** lorsque vous exécutez sans débogage avec des conteneurs Windows, de sorte que les conteneurs Windows a commencé à partir de Visual Studio en utilisant **Ctrl**+**F5** n’affichera pas les journaux dans cet onglet; utiliser la fenêtre **de sortie** à la place.

## <a name="view-the-filesystem"></a>Afficher le système de fichiers

Sur l’onglet **Fichiers,** vous pouvez consulter le système de fichiers du conteneur, y compris le dossier d’application qui contient votre projet.

![Capture d’écran de l’onglet Fichiers dans la fenêtre des conteneurs](media/view-and-diagnose-containers/container-filesystem.png)

Pour ouvrir des fichiers dans Visual Studio, naviguez sur le fichier et cliquez deux fois, ou cliquez à droite et choisissez **Open**. Visual Studio ouvre les fichiers en mode lecture uniquement.

![Capture d’écran d’un fichier ouvert pour visionnement dans Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

À l’aide de l’onglet **Fichiers,** vous pouvez afficher les journaux d’applications tels que les journaux IIS, les fichiers de configuration et d’autres fichiers de contenu dans le système de fichiers de votre conteneur.

## <a name="start-stop-and-remove-containers"></a>Démarrer, arrêter et enlever les conteneurs

Par défaut, la fenêtre **Containers** affiche tous les conteneurs de la machine que Docker gère. Vous pouvez utiliser les boutons de la barre d’outils pour démarrer, arrêter ou supprimer (supprimer) un conteneur que vous ne voulez plus.  Cette liste est mise à jour dynamiquement au fur et à mesure que les conteneurs sont créés ou supprimés.

## <a name="open-a-terminal-window-in-a-running-container"></a>Ouvrez une fenêtre terminale dans un conteneur en marche

Vous pouvez ouvrir une fenêtre terminale (application rapide ou coque interactive) dans le conteneur en utilisant le bouton **Fenêtre terminale ouverte** dans la fenêtre **du conteneur.**

![Capture d’écran de la fenêtre terminale ouverte dans la fenêtre des conteneurs](media/view-and-diagnose-containers/containers-open-terminal-window.png)

Pour les conteneurs Windows, l’invite de commande Windows s’ouvre. Pour les conteneurs Linux, il ouvre une fenêtre à l’aide de la coquille bash.

![Capture d’écran de la fenêtre bash](media/view-and-diagnose-containers/container-bash-window.png)

Normalement, la fenêtre terminale s’ouvre à l’extérieur visual Studio comme une fenêtre séparée. Si vous voulez un environnement de ligne de commande intégré dans l’IDE Visual Studio comme une fenêtre d’outils amarrée, vous pouvez installer [Whack Whack Terminal](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal).

## <a name="attach-the-debugger-to-a-process"></a>Attachez le débagé à un processus

Vous pouvez attacher le débbugger à un processus qui s’exécute dans le conteneur en utilisant le bouton **Joindre pour traiter** sur la barre d’outils de fenêtre Containers. Lorsque vous utilisez ce bouton, le dialogue **Attach to Process** apparaît et affiche les processus disponibles qui s’exécutent dans le conteneur.  

![Capture d’écran de Attach to Process dialog box](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

Vous pouvez vous attacher aux processus gérés dans le conteneur. Pour rechercher un processus dans un autre conteneur, utilisez le bouton **Trouver** et sélectionnez un autre conteneur sur le dialogue **Select Docker Container.**

## <a name="viewing-images"></a>Affichage d’images

Vous pouvez également afficher des images sur la machine locale en utilisant l’onglet **Images** dans la fenêtre **Des conteneurs.** Les images tirées des dépôts externes sont regroupées dans une vue d’arbres. Sélectionnez une image pour inspecter les détails de l’image.

Pour supprimer une image, cliquez à droite sur l’image dans la vue de l’arbre et choisissez **Supprimer,** ou sélectionnez l’image, et utilisez le bouton **Supprimer** sur la barre d’outils.

## <a name="next-steps"></a>Étapes suivantes

En savoir plus sur les outils de conteneurs disponibles dans Visual Studio en lisant [l’aperçu des outils conteneurs](overview.md).

## <a name="see-also"></a>Voir aussi

[Développement de conteneurs dans visual Studio](/visualstudio/containers)

[Extensions Marketplace pour Visual Studio](https://marketplace.visualstudio.com/)
