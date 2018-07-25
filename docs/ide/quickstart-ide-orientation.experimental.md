---
title: Présentation de l’IDE Visual Studio
ms.date: 07/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aeb7156998b7c6ea91205bd2c05de690b597490a
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081535"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Démarrage rapide : premier aperçu de l'IDE Visual Studio

Dans cette présentation de 5-10 minutes de l’environnement de développement intégré (IDE) de Visual Studio, vous allez effectuer une visite guidée de quelques fenêtres, menus et autres fonctionnalités de l’interface utilisateur.

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement.

## <a name="start-page"></a>Page de démarrage

Quand vous lancez Visual Studio, la première chose qui s’affiche en général est la **Page de démarrage**. La **Page de démarrage** est conçue comme un « hub » pour vous aider à trouver plus rapidement les commandes et fichiers projet dont vous avez besoin. La section **Récent** affiche les projets et dossiers que vous avez utilisés récemment. Sous **Nouveau projet**, vous pouvez cliquer sur un lien pour afficher la boîte de dialogue **Nouveau projet**, ou sous **Ouvrir**, vous pouvez ouvrir un projet ou dossier de code existant. Vous trouverez à droite un flux des dernières informations pour les développeurs.

![Page de démarrage dans Visual Studio](media/start-page-dark.png)

Si vous fermez la **Page de démarrage** et souhaitez la revoir, vous pouvez la rouvrir à partir du menu **Fichier**.

![Menu Fichier dans Visual Studio](media/file-menu-start-page-dark.png)

## <a name="create-a-project"></a>Créer un projet

Pour continuer à explorer les fonctionnalités de Visual Studio, nous allons créer un projet.

1. Dans la **Page de démarrage**, dans la zone de recherche sous **Nouveau projet**, tapez **console** pour filtrer la liste des types de projets à ceux dont le nom contient le mot « console ».

   ![Rechercher des modèles de projet dans la page de démarrage de Visual Studio](media/start-page-search-templates-dark.png)

   Visual Studio fournit différents types de modèles de projet qui vous aident à bien démarrer le codage. Choisissez un modèle de projet C# **Application console (.NET Framework)**. (Ou, si vous êtes un développeur en Visual Basic, C++, Javascript ou autre langage, n’hésitez pas à créer un projet dans l’un de ces langages. L’interface utilisateur que nous allons explorer est identique pour tous les langages de programmation.)

1. Dans la boîte de dialogue **Nouveau projet** qui apparaît, acceptez le nom de projet par défaut et sélectionnez **OK**.

   Le projet est créé et un fichier nommé *Program.cs* s’ouvre dans la fenêtre **Éditeur**. **L’Éditeur** affiche le contenu des fichiers. C’est là que vous effectuez la majeure partie de votre travail de codage dans Visual Studio.

   ![Éditeur dans Visual Studio](media/editor-dark.png)

## <a name="solution-explorer"></a>Explorateur de solutions

L’**Explorateur de solutions**, qui se trouve généralement sur le côté droit de Visual Studio, affiche une représentation graphique de la hiérarchie des fichiers et des dossiers dans votre projet, solution ou dossier de code. Vous pouvez parcourir la hiérarchie et atteindre un fichier dans **l’Explorateur de solutions**.

![Explorateur de solutions dans Visual Studio](media/solution-explorer-console-app-dark.png)

## <a name="menus"></a>Menus

La barre de menus en haut de la fenêtre de Visual Studio regroupe les commandes en catégories. Par exemple, le menu **Projet** contient les commandes liées au projet sur lequel vous travaillez. Dans le menu **Outils**, vous pouvez personnaliser le comportement de Visual Studio en sélectionnant **Options**, ou vous pouvez ajouter des fonctionnalités à votre installation en sélectionnant **Obtenir des outils et des fonctionnalités**.

![Barre de menus dans Visual Studio](media/menu-bar-dark.png)

Ouvrons la fenêtre **Liste d’erreurs** en sélectionnant le menu **Afficher**, puis **Liste d’erreurs**.

## <a name="error-list"></a>Liste d'erreurs

La **Liste d’erreurs** affiche les erreurs, avertissements et messages concernant l’état actuel de votre code. S’il existe des erreurs (par exemple, une accolade ou un point-virgule manquant) dans votre fichier, ou n’importe où dans votre projet, elles sont répertoriées ici.

![Liste d’erreurs dans Visual Studio](media/error-list-dark.png)

## <a name="output-window"></a>Fenêtre Sortie

La fenêtre **Sortie** affiche les messages de sortie après la génération de votre projet et les messages retournés par votre fournisseur de contrôle de code source.

Générons le projet pour afficher une sortie de génération. Dans le menu **Générer** , cliquez sur **Générer la solution**. La fenêtre **Sortie** obtient automatiquement le focus et affiche un message de génération réussie.

![Fenêtre Sortie dans Visual Studio](media/output-window-dark.png)

## <a name="quick-launch"></a>Lancement rapide

La zone **Lancement rapide** permet d’effectuer rapidement et facilement presque n’importe quelle opération dans Visual Studio. Vous pouvez saisir du texte concernant ce que vous voulez faire et une liste d’options pertinente s’affiche. Imaginez par exemple que vous souhaitez augmenter les commentaires de la sortie de la génération pour afficher des détails supplémentaires sur ce que fait la génération. Voici comment procéder :

1. Tapez **commentaires** dans la zone **Lancement rapide**. Parmi les résultats affichés, choisissez **Projets et solutions --> Générer et exécuter** sous la catégorie **Options**.

   ![Zone de lancement rapide dans Visual Studio](media/quick-launch-verbosity-dark.png)

   La boîte de dialogue **Options** s’affiche sur la page des options **Générer et exécuter**.

1. Sous **Commentaires relatifs à la sortie de génération du projet MSBuild**, choisissez **Normal**, puis cliquez sur **OK**.

1. Regénérez le projet en cliquant avec le bouton droit sur le projet **ConsoleApp1** dans l’**Explorateur de solutions** et en choisissant **Regénérer** dans le menu contextuel.

   Cette fois, la fenêtre **Sortie** affiche une journalisation de commentaires plus importante à partir du processus de génération, notamment quels fichiers ont été copiés et où.

   ![Sortie de génération avec commentaires dans Visual Studio](media/build-output-verbose-dark.png)

## <a name="send-feedback-menu"></a>Menu Envoyer des commentaires

Si vous rencontrez des problèmes pendant l’utilisation de Visual Studio, ou si vous avez des suggestions d’amélioration du produit, vous pouvez utiliser le menu **Envoyer des commentaires** en haut de la fenêtre de Visual Studio, à côté de la zone **Lancement rapide**.

![Menu Envoyer des commentaires dans Visual Studio](media/send-feedback-dark.png)

## <a name="next-steps"></a>Étapes suivantes

Nous avons exploré quelques fonctionnalités de Visual Studio pour nous familiariser avec l’interface utilisateur. Pour en apprendre davantage :

- Effectuez une visite guidée plus approfondie de Visual Studio et essayez-vous au débogage dans [Présentation de l’IDE de Visual Studio](../ide/visual-studio-ide.md)

- Parcourez la section **Éléments généraux de l’interface utilisateur** dans la documentation VS, qui explore plus en détail les fenêtres comme [Liste d’erreurs](../ide/reference/error-list-window.md), la [fenêtre Sortie](../ide/reference/output-window.md), la [fenêtre Propriétés](../ide/reference/properties-window.md) et la [boîte de dialogue Options](../ide/reference/options-dialog-box-visual-studio.md)

## <a name="see-also"></a>Voir aussi

- [Démarrage rapide : personnaliser l’IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Démarrage rapide : Écrire du code dans l’éditeur](../ide/quickstart-editor.md)
- [Démarrage rapide : projets et solutions](../ide/quickstart-projects-solutions.md)