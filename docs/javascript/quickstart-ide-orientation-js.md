---
title: Premier aperçu de l’IDE Visual Studio
titleSuffix: ''
ms.date: 02/05/2019
ms.topic: quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41d5d40cc7951f09a8106426f603d42628c61846
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238866"
---
# <a name="first-look-at-the-visual-studio-ide"></a>Premier aperçu de l’IDE Visual Studio

Dans cette présentation de 5-10 minutes de l’environnement de développement intégré (IDE) de Visual Studio, vous allez effectuer une visite guidée de quelques fenêtres, menus et autres fonctionnalités de l’interface utilisateur.

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range=">=vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Fenêtre de démarrage

Quand vous lancez Visual Studio, la première chose que vous voyez est la fenêtre de démarrage. La fenêtre de démarrage est conçue pour vous aider à « accéder au code » plus rapidement. Elle contient des options pour fermer ou extraire du code, ouvrir une solution ou un projet existant, créer un projet ou simplement ouvrir un dossier qui contient des fichiers de code.

[![Fenêtre démarrer dans Visual Studio 2019](media/vs-2019/start-window.png)](media/vs-2019/start-window.png)

Si vous utilisez Visual Studio pour la première fois, votre liste des derniers projets est vide.

Si vous travaillez avec des codes base non-MSBuild, utilisez l’option **Ouvrir un dossier local** pour ouvrir votre code dans Visual Studio. Pour plus d’informations, consultez [Développer du code dans Visual Studio sans projets ni solutions](develop-javascript-code-without-solutions-projects.md). Sinon, vous pouvez créer un projet ou en cloner un à partir d’un fournisseur de code source comme GitHub ou Azure DevOps.

L’option **Continuer sans code** ouvre simplement l’environnement de développement Visual Studio sans aucun projet ou code spécifique chargé. Vous pouvez choisir cette option pour rejoindre une session [Live Share](/visualstudio/liveshare/) ou effectuer l’attachement à un processus pour le débogage. Vous pouvez également appuyer sur **Échap** pour fermer la fenêtre de démarrage et ouvrir l’IDE.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Page de démarrage

La première chose que vous verrez après avoir lancé Visual Studio est probablement la **page de démarrage**. La **page de démarrage** est conçue comme un « Hub » pour vous aider à trouver plus rapidement les commandes et fichiers projet dont vous avez besoin. La section **Récent** affiche les projets et dossiers que vous avez utilisés récemment. Sous **Nouveau projet**, vous pouvez cliquer sur un lien pour afficher la boîte de dialogue **Nouveau projet**, ou sous **Ouvrir**, vous pouvez ouvrir un projet ou dossier de code existant. Vous trouverez à droite un flux des dernières informations pour les développeurs.

![Page de démarrage dans Visual Studio](media/start-page.png)

Si vous fermez la **page de démarrage** et que vous souhaitez la voir à nouveau, vous pouvez la rouvrir à partir du menu **fichier** .

![Menu Fichier dans Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

## <a name="create-a-project"></a>Création d’un projet

Pour continuer à explorer les fonctionnalités de Visual Studio, nous allons créer un projet.

::: moniker range=">=vs-2019"

1. Dans la fenêtre de démarrage, sélectionnez **Créer un projet** puis, dans la zone de recherche, tapez **javascript** pour filtrer la liste des types de projets et afficher seulement ceux dont le nom ou le type de langage contient le mot « javascript ».

   Visual Studio fournit différents types de modèles de projet qui vous aident à bien démarrer le codage. (Si vous êtes développeur TypeScript, n’hésitez pas à créer un projet dans ce langage. L’interface utilisateur que nous allons explorer est identique pour tous les langages de programmation.)

   ![Rechercher des modèles de projet dans la fenêtre de démarrage de Visual Studio](media/vs-2019/create-new-project.png)

1. Choisissez un modèle de projet **Application web Node.js vide**, puis cliquez sur **Suivant**.

1. Dans la boîte de dialogue **Configurer votre nouveau projet** qui apparaît, acceptez le nom de projet par défaut et choisissez **Créer**.

::: moniker-end

::: moniker range="vs-2017"

1. Dans la **Page de démarrage**, dans la zone de recherche sous **Nouveau projet**, tapez **javascript** pour filtrer la liste des types de projets et afficher seulement ceux dont le nom ou le type de langage contient le mot « javascript ».

   ![Rechercher des modèles de projet dans la page de démarrage de Visual Studio](media/start-page-search-templates.png)

   Visual Studio fournit différents types de modèles de projet qui vous aident à bien démarrer le codage. Choisissez un modèle de projet **Application web Node.js vide**. (Si vous êtes développeur TypeScript, n’hésitez pas à créer un projet dans ce langage. L’interface utilisateur que nous allons explorer est identique pour tous les langages de programmation.)

1. Dans la boîte de dialogue **Nouveau projet** qui apparaît, acceptez le nom de projet par défaut et sélectionnez **OK**.
::: moniker-end

   Le projet est créé et un fichier nommé *server.js* s’ouvre dans la fenêtre de l' **éditeur** . L' **éditeur** affiche le contenu des fichiers et vous permet d’effectuer la majeure partie de votre travail de codage dans Visual Studio.

   ![Éditeur dans Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Explorateur de solutions

L’**Explorateur de solutions**, qui se trouve généralement sur le côté droit de Visual Studio, affiche une représentation graphique de la hiérarchie des fichiers et des dossiers dans votre projet, solution ou dossier de code. Vous pouvez parcourir la hiérarchie et accéder à un fichier dans **Explorateur de solutions**.

![Explorateur de solutions dans Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menus

La barre de menus en haut de la fenêtre de Visual Studio regroupe les commandes en catégories. Par exemple, le menu **Projet** contient les commandes liées au projet sur lequel vous travaillez. Dans le menu **Outils**, vous pouvez personnaliser le comportement de Visual Studio en sélectionnant **Options**, ou vous pouvez ajouter des fonctionnalités à votre installation en sélectionnant **Obtenir des outils et des fonctionnalités**.

![Barre de menus dans Visual Studio](media/quickstart-IDE-menu-bar.png)

Nous allons ouvrir la fenêtre de **liste d’erreurs** en sélectionnant le menu **affichage** , puis **liste d’erreurs**.

## <a name="error-list"></a>Liste d'erreurs

Le **liste d’erreurs** affiche les erreurs, les avertissements et les messages relatifs à l’état actuel de votre code. S’il existe des erreurs (par exemple, une accolade ou un point-virgule manquant) dans votre fichier, ou n’importe où dans votre projet, elles sont répertoriées ici.

![Liste d’erreurs dans Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Fenêtre Sortie

La fenêtre **Sortie** affiche les messages de sortie après la génération de votre projet et les messages retournés par votre fournisseur de contrôle de code source.

Générons le projet pour afficher une sortie de génération. Dans le menu **générer** , choisissez **générer la solution**. La fenêtre **sortie** obtient automatiquement le focus et affiche un message de génération réussi.

![Fenêtre Sortie dans Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Zone de recherche

La zone de recherche permet d’effectuer rapidement et facilement presque n’importe quelle opération dans Visual Studio. Vous pouvez saisir du texte concernant ce que vous voulez faire et une liste d’options pertinente s’affiche. Imaginez par exemple que vous souhaitez augmenter les commentaires de la sortie de la génération pour afficher des détails supplémentaires sur ce que fait la génération. Voici comment procéder :

1. Tapez **commentaires** dans la zone de recherche. Parmi les résultats affichés, choisissez **Projets et solutions --> Générer et exécuter** sous la catégorie **Options**.

   ![Zone de recherche dans Visual Studio](media/quickstart-IDE-quick-launch.png)

   La boîte de dialogue **Options** s’affiche sur la page des options **Générer et exécuter**.

1. Sous **Commentaires relatifs à la sortie de génération du projet MSBuild**, choisissez **Normal**, puis cliquez sur **OK**.

1. Regénérez le projet en cliquant avec le bouton droit sur le projet **NodejsWebApp1** dans l’**Explorateur de solutions** et en choisissant **Regénérer** dans le menu contextuel.

   Cette fois, la fenêtre **sortie** affiche une journalisation plus détaillée du processus de génération, y compris les fichiers qui ont été copiés où.

   ![Sortie de génération avec commentaires dans Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Menu Envoyer des commentaires

Si vous rencontrez des problèmes pendant l’utilisation de Visual Studio, ou si vous avez des suggestions d’amélioration du produit, vous pouvez utiliser le menu **Envoyer des commentaires** en haut de la fenêtre Visual Studio.

![Menu Envoyer des commentaires dans Visual Studio](../ide/media/quickstart-ide-send-feedback.png)

## <a name="next-steps"></a>Étapes suivantes

Nous avons exploré quelques fonctionnalités de Visual Studio pour nous familiariser avec l’interface utilisateur. Pour en apprendre davantage :

> [!div class="nextstepaction"]
> [Découvrez l’éditeur de code](write-and-edit-code.md)

> [!div class="nextstepaction"]
> [Découvrir les projets et les solutions](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’IDE Visual Studio](../get-started/visual-studio-ide.md)
- [Fonctionnalités supplémentaires de Visual Studio 2017](../ide/advanced-feature-overview.md)
- [Changer le thème et les couleurs de police](../ide/quickstart-personalize-the-ide.md)
