---
title: "Visite guidée de l’IDE de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7f10ee7dc03ffe0f80b6ee3d7ff47f5fcd6a1624
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2017
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Démarrage rapide : premier aperçu de l'IDE Visual Studio

Dans cette présentation de 5-10 minutes de l’environnement de développement intégré (IDE) de Visual Studio, vous allez effectuer une visite guidée de quelques fenêtres, menus et autres fonctionnalités de l’interface utilisateur.

## <a name="start-page"></a>Page de démarrage

Lorsque vous lancez Visual Studio, la première chose qui s’affiche en général est la Page de démarrage. La page de démarrage est conçue comme un « hub » pour vous aider à trouver plus rapidement les commandes et fichiers projet dont vous avez besoin. La section **Récent** affiche les projets et dossiers que vous avez utilisés récemment. Sous **Nouveau projet**, vous pouvez cliquer sur un lien pour afficher la boîte de dialogue Nouveau projet ou sous **Ouvrir**, vous pouvez ouvrir un projet ou dossier de code existant. Vous trouverez à droite un flux des dernières informations pour les développeurs.

![Page de démarrage VS](media/quickstart-IDE-start-page.png)

Si vous fermez la Page de démarrage et souhaitez l’afficher à nouveau, vous pouvez la rouvrir à partir du menu **Fichier**.

![menu Fichier](media/quickstart-IDE-file-menu-large.png)

Pour continuer à explorer l’IDE, créons un projet.

1. Dans la **Page de démarrage**, dans la zone de recherche sous **Nouveau projet**, entrez `console` pour filtrer la liste des types de projets. Choisissez une application de console C# ou VB **(.NET Framework)**. (Ou, si vous êtes un développeur en C++, Javascript ou autre langage, n’hésitez pas à créer un projet dans l’un de ces langages. L’interface utilisateur que nous allons explorer est identique pour tous les langages.)

1. Dans la boîte de dialogue **Nouveau projet**, acceptez le nom de projet par défaut et sélectionnez **OK**.

   Le projet est créé et un fichier nommé **Program.cs** ou **Program.vb** s’ouvre dans la fenêtre **Éditeur**. L’Éditeur affiche le contenu des fichiers. C’est là que vous effectuerez la majeure partie de votre travail de codage dans Visual Studio.

## <a name="solution-explorer"></a>Explorateur de solutions

L’Explorateur de solutions affiche une représentation graphique de la hiérarchie des fichiers et des dossiers dans votre projet, solution ou dossier de code. Vous pouvez parcourir la hiérarchie et atteindre un fichier dans l’Explorateur de solutions.

![Explorateur de solutions](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menus

La barre de menus au sommet de l’IDE regroupe les commandes en catégories. Par exemple, le menu **Projet** contient les commandes liées au projet sur lequel vous travaillez. Dans le menu **Outils**, vous pouvez personnaliser l’IDE en sélectionnant **Options** ou vous pouvez ajouter des fonctionnalités à votre installation en sélectionnant **Obtenir des outils et des fonctionnalités...**.

![Barre de menus](media/quickstart-IDE-menu-bar.png)

Ouvrons la fenêtre Liste d’erreurs en sélectionnant le menu **Afficher**, puis **Liste d’erreurs**.

## <a name="error-list"></a>Liste d'erreurs

La Liste d’erreurs affiche les erreurs, avertissements et messages concernant l’état actuel de votre code. S’il existe des erreurs (par exemple, une erreur de typographie dans la syntaxe) dans votre fichier, ou n’importe où dans votre projet, elles sont répertoriées ici.

![Liste d'erreurs](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Fenêtre Sortie

La fenêtre Sortie affiche des messages de sortie à partir de Générer et de Contrôle de la source.

Générons le projet pour afficher une journalisation de sortie. Dans le menu **Générer** , cliquez sur **Générer la solution**. La fenêtre Sortie est automatiquement mise au point et affiche un message de génération réussie.

![Fenêtre Sortie](media/quickstart-IDE-output.png)

## <a name="quick-launch"></a>Lancement rapide

La zone Lancement rapide permet d’effectuer rapidement et facilement presque n’importe quelle opération dans l’IDE. Vous pouvez saisir du texte concernant ce que vous voulez faire et une liste d’options pertinente s’affiche. Imaginons, par exemple, que nous voulons augmenter les commentaires sur la sortie de la génération pour afficher des informations de journalisation supplémentaires ce que fait la génération :

1. Entrez `verbosity` dans la zone **Lancement rapide**, puis choisissez **Projets et solutions -> Générer et exécuter** sous la catégorie **Options**.

   ![Zone Lancement rapide](media/quickstart-IDE-quick-launch.png)

   La boîte de dialogue **Options** s’affiche sur la page des options **Générer et exécuter**.

1. Sous **Commentaires relatifs à la sortie de génération du projet MSBuild**, choisissez **Normal**, puis cliquez sur **OK**.

1. Maintenant, nous allons générer le projet à nouveau en cliquant avec le bouton droit sur le projet **ConsoleApp1** dans **l’Explorateur de solutions** et en choisissant **Regénérer** dans le menu contextuel.

   Cette fois, la fenêtre Sortie affiche une journalisation de commentaires plus importante à partir du processus de génération, notamment quels fichiers ont été copiés et où.

## <a name="send-feedback-menu"></a>Menu Envoyer des commentaires

Si vous rencontrez des problèmes lors de l’utilisation de Visual Studio, ou si vous avez des suggestions d’amélioration du produit, vous pouvez utiliser le menu **Envoyer des commentaires** au sommet de l’IDE, à côté de la zone Lancement rapide.

![Menu Envoyer des commentaires](media/quickstart-IDE-send-feedback.png)

## <a name="next-steps"></a>Étapes suivantes

Nous avons exploré quelques fonctionnalités de l’IDE de Visual Studio pour nous familiariser avec l’interface utilisateur. Pour en apprendre davantage :

- Parcourez la section Éléments généraux de l’interface utilisateur dans la documentation VS, qui explore plus en détail les fenêtres comme [Liste d’erreurs](../ide/reference/error-list-window.md), [fenêtre Sortie](../ide/reference/output-window.md), [fenêtre Propriétés](../ide/reference/properties-window.md) et [boîte de dialogue Options](../ide/reference/options-dialog-box-visual-studio.md)

- Effectuez une visite guidée plus approfondie de l’IDE et essayez-vous au débogage, dans [Présentation de l’IDE de Visual Studio](../ide/visual-studio-ide.md)

## <a name="see-also"></a>Voir aussi

[Démarrage rapide : Personnalisation de l’IDE](../ide/personalizing-the-visual-studio-ide.md)  
[Démarrage rapide : Codage dans l’éditeur](../ide/quickstart-editor.md)  
[Démarrage rapide : Projets et solutions](../ide/quickstart-projects-solutions.md)  