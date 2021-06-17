---
title: 'Démarrage rapide : visite guidée de l’IDE de Visual Studio'
description: Découvrez quelques-unes des fenêtres, des menus et d’autres fonctionnalités de l’interface utilisateur de l’environnement de développement intégré (IDE) de Visual Studio.
ms.custom: acquisition
titleSuffix: ''
ms.date: 03/02/2021
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f10c3fcca5d87f8371d1373314406cf4aa47ec3
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113224"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Démarrage rapide : premier aperçu de l'IDE Visual Studio

Dans cette présentation de 5-10 minutes de l’environnement de développement intégré (IDE) de Visual Studio, vous allez effectuer une visite guidée de quelques fenêtres, menus et autres fonctionnalités de l’interface utilisateur.

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range=">=vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Page de démarrage

Lorsque vous ouvrez Visual Studio, la première chose qui s’affiche en général est la **Page de démarrage**. La **page de démarrage** est conçue comme un « Hub » pour vous aider à trouver plus rapidement les commandes et fichiers projet dont vous avez besoin. La section **Récent** affiche les projets et dossiers que vous avez utilisés récemment. Sous **Nouveau projet**, vous pouvez cliquer sur un lien pour afficher la boîte de dialogue **Nouveau projet**, ou sous **Ouvrir**, vous pouvez ouvrir un projet ou dossier de code existant. Vous trouverez à droite un flux des dernières informations pour les développeurs.

![Page de démarrage dans Visual Studio](media/start-page.png)

Si vous fermez la **page de démarrage** et que vous souhaitez la voir à nouveau, vous pouvez la rouvrir à partir du menu **fichier** .

![Menu Fichier dans Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Fenêtre de démarrage

Quand vous ouvrez Visual Studio, la première chose que vous voyez est la fenêtre de démarrage. La fenêtre de démarrage est conçue pour vous aider à « accéder au code » plus rapidement. Elle contient des options pour fermer ou extraire du code, ouvrir une solution ou un projet existant, créer un projet ou simplement ouvrir un dossier qui contient des fichiers de code.

[![Démarrer la fenêtre dans Visual Studio 2019](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

Si vous utilisez Visual Studio pour la première fois, votre liste des derniers projets est vide.

Si vous travaillez avec des codes base non-MSBuild, utilisez l’option **Ouvrir un dossier local** pour ouvrir votre code dans Visual Studio. Pour plus d’informations, consultez [Développer du code dans Visual Studio sans projets ni solutions](develop-code-in-visual-studio-without-projects-or-solutions.md). Sinon, vous pouvez créer un projet ou en cloner un à partir d’un fournisseur de code source comme GitHub ou Azure DevOps.

L’option **Continuer sans code** ouvre simplement l’environnement de développement Visual Studio sans aucun projet ou code spécifique chargé. Vous pouvez choisir cette option pour rejoindre une session [Live Share](/visualstudio/liveshare/) ou effectuer l’attachement à un processus pour le débogage. Vous pouvez également appuyer sur **Échap** pour fermer la fenêtre de démarrage et ouvrir l’IDE.

::: moniker-end

## <a name="create-a-project"></a>Création d’un projet

Pour continuer à explorer les fonctionnalités de Visual Studio, nous allons créer un projet.

::: moniker range="vs-2017"

1. Dans la **Page de démarrage**, dans la zone de recherche sous **Nouveau projet**, tapez **console** pour filtrer la liste des types de projets à ceux dont le nom contient le mot « console ».

   ![Rechercher des modèles de projet dans la page de démarrage de Visual Studio](media/start-page-search-templates.png)

   Visual Studio fournit différents types de modèles de projet qui vous aident à bien démarrer le codage. Choisissez un modèle de projet **Application console (.NET Core)** C#. (Ou, si vous êtes un développeur en Visual Basic, C++, Javascript ou autre langage, n’hésitez pas à créer un projet dans l’un de ces langages. L’interface utilisateur que nous allons explorer est identique pour tous les langages de programmation.)

1. Dans la boîte de dialogue **Nouveau projet** qui apparaît, acceptez le nom de projet par défaut et sélectionnez **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

    :::image type="content" source="../get-started/media/vs-2019/start-window-create-new-project.png" alt-text="Capture d’écran de la fenêtre créer un nouveau projet dans Visual Studio 2019.":::

   La fenêtre **Créer un projet** s’affiche et présente plusieurs *modèles* de projet. Un modèle contient les fichiers et les paramètres de base requis pour un type de projet donné.

   Ici, vous pouvez rechercher, filtrer et sélectionner un modèle de projet. Elle montre également la liste des modèles de projet récemment utilisés.

1. Dans la zone de recherche située en haut, tapez **console** pour filtrer la liste des types de projets à ceux dont le nom contient le mot « console ». Affinez les résultats de la recherche en choisissant **C#** (ou une autre langue de votre choix) dans la liste déroulante **tous les langages** .

    :::image type="content" source="media/vs-2019/create-new-project.png" alt-text="Capture d’écran de la fenêtre créer un nouveau projet dans Visual Studio 2019, où vous sélectionnez le modèle souhaité.":::

1. Si vous avez sélectionné C#, Visual Basic ou F # comme langage, sélectionnez le modèle **application console** , puis choisissez **suivant**. (Si vous avez sélectionné un autre langage, choisissez n’importe quel modèle. L’interface utilisateur que nous allons explorer est identique pour tous les langages de programmation.)

1. Dans la fenêtre **configurer votre nouveau projet** , acceptez le nom et l’emplacement du projet par défaut, puis choisissez **suivant**.

    :::image type="content" source="media/vs-2019/configure-new-project-console.png" alt-text="Capture d’écran de la fenêtre « Configurer un nouveau projet » dans Visual Studio 2019, où vous entrez le nom du projet.":::

1. Dans la fenêtre **informations supplémentaires** , vérifiez que **.net Core 3,1** s’affiche dans le menu déroulant **Framework cible** , puis cliquez sur **créer**.

    :::image type="content" source="../get-started/media/vs-2019/create-project-additional-info.png" alt-text="Capture d’écran de la fenêtre « informations supplémentaires » dans Visual Studio 2019, où vous sélectionnez la version de .NET Core Framework que vous souhaitez.":::

::: moniker-end

   Le projet est créé et un fichier nommé *Program.cs* s’ouvre dans la fenêtre **Éditeur**. L’**Éditeur** affiche le contenu des fichiers. C’est là que vous effectuez la majeure partie de votre travail de codage dans Visual Studio.

   ![Éditeur dans Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Explorateur de solutions

L’**Explorateur de solutions**, qui se trouve généralement sur le côté droit de Visual Studio, affiche une représentation graphique de la hiérarchie des fichiers et des dossiers dans votre projet, solution ou dossier de code. Vous pouvez parcourir la hiérarchie et accéder à un fichier dans **Explorateur de solutions**.

![Explorateur de solutions dans Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menus

La barre de menus en haut de la fenêtre de Visual Studio regroupe les commandes en catégories. Par exemple, le menu **Projet** contient les commandes liées au projet sur lequel vous travaillez. Dans le menu **Outils**, vous pouvez personnaliser le comportement de Visual Studio en sélectionnant **Options**, ou vous pouvez ajouter des fonctionnalités à votre installation en sélectionnant **Obtenir des outils et des fonctionnalités**.

::: moniker range="vs-2017"

![Barre de menus dans Visual Studio 2017](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Barre de menus dans Visual Studio 2019](media/vs-2019/menu-bar.png)

::: moniker-end

## <a name="error-list"></a>Liste d'erreurs

Ouvrez la fenêtre **Liste d’erreurs** en sélectionnant le menu **Affichage**, puis **Liste d’erreurs**.

Le **liste d’erreurs** affiche les erreurs, les avertissements et les messages relatifs à l’état actuel de votre code. S’il existe des erreurs (par exemple, une accolade ou un point-virgule manquant) dans votre fichier, ou n’importe où dans votre projet, elles sont répertoriées ici.

![Liste d’erreurs dans Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Fenêtre Sortie

La fenêtre **Sortie** affiche les messages de sortie après la génération de votre projet et les messages retournés par votre fournisseur de contrôle de code source.

Générons le projet pour afficher une sortie de génération. Dans le menu **générer** , choisissez **générer la solution**. La fenêtre **sortie** obtient automatiquement le focus et affiche un message de génération réussi.

![Fenêtre Sortie dans Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Zone de recherche

La zone de recherche permet d’accéder rapidement et facilement à quasiment n’importe quel élément dans Visual Studio. Vous pouvez saisir du texte concernant ce que vous voulez faire et une liste d’options pertinente s’affiche. Imaginez par exemple que vous souhaitez augmenter les commentaires de la sortie de la génération pour afficher des détails supplémentaires sur ce que fait la génération. Voici comment procéder :

::: moniker range="vs-2017"

1. Localisez la zone de recherche **Lancement rapide** dans le coin supérieur droit de l’IDE. (Vous pouvez également appuyer sur **CTRL** + **Q** pour y accéder.)

2. Tapez **commentaires** dans la zone de recherche. Parmi les résultats affichés, choisissez **Projets et solutions --> Générer et exécuter** sous la catégorie **Options**.

   ![Zone de recherche Lancement rapide dans Visual Studio 2017](media/quickstart-IDE-quick-launch.png)

   La boîte de dialogue **Options** s’affiche sur la page des options **Générer et exécuter**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Appuyez sur **CTRL** + **Q** pour activer la zone de recherche dans la partie supérieure de l’IDE.

2. Tapez **commentaires** dans la zone de recherche. Parmi les résultats affichés, choisissez **Modifier les commentaires MSBuild**.

   ![Zone de recherche dans Visual Studio 2019](media/vs-2019/quick-launch-verbosity.png)

   La boîte de dialogue **Options** s’affiche sur la page des options **Générer et exécuter**.

::: moniker-end

3. Sous **Commentaires relatifs à la sortie de génération du projet MSBuild**, choisissez **Normal**, puis cliquez sur **OK**.

4. Regénérez le projet en cliquant avec le bouton droit sur le projet **ConsoleApp1** dans l’**Explorateur de solutions** et en choisissant **Regénérer** dans le menu contextuel.

   Cette fois, la fenêtre **sortie** affiche une journalisation plus détaillée du processus de génération, y compris les fichiers qui ont été copiés où.

   ![Sortie de génération avec commentaires dans Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Menu Envoyer des commentaires

Si vous rencontrez des problèmes pendant l’utilisation de Visual Studio, ou si vous avez des suggestions d’amélioration du produit, vous pouvez utiliser le menu **Envoyer des commentaires** vers le haut de la fenêtre Visual Studio.

::: moniker range="vs-2017"

![Menu Envoyer des commentaires dans Visual Studio 2017](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Menu Envoyer des commentaires dans Visual Studio 2019](media/vs-2019/send-feedback-menu.png)

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

Nous avons exploré quelques fonctionnalités de Visual Studio pour nous familiariser avec l’interface utilisateur. Pour en apprendre davantage :

> [!div class="nextstepaction"]
> [Découvrez l’éditeur de code](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [Découvrir les projets et les solutions](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’IDE Visual Studio](../get-started/visual-studio-ide.md)
- [Fonctionnalités supplémentaires de Visual Studio](../ide/advanced-feature-overview.md)
- [Changer le thème et les couleurs de police](../ide/quickstart-personalize-the-ide.md)
