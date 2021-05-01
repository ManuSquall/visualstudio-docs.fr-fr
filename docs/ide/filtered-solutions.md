---
title: Charge un sous-ensemble de projets
description: En savoir plus sur le filtrage de solution et sur la façon dont il vous permet de charger rapidement un sous-ensemble de projets dans une solution.
ms.custom: SEO-VS-2020
ms.date: 04/22/2019
ms.topic: conceptual
helpviewer_keywords:
- filtered solution
- solution filtering
author: TerryGLee
ms.author: stsu
manager: jmartens
monikerRange: '>= vs-2019'
ms.openlocfilehash: ea30edbaac7248af8e1a58b76aebd66cf44befba
ms.sourcegitcommit: a667ce8394a800906d633737f4fcbc77f0fcba7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2021
ms.locfileid: "108298728"
---
# <a name="filtered-solutions-in-visual-studio"></a>Solutions filtrées dans Visual Studio

La collaboration entre grandes équipes de développement passe souvent par une vaste solution unique comprenant de nombreux projets. Toutefois, les développeurs individuels travaillent généralement sur un petit sous-ensemble de ces projets. Pour améliorer les performances associées à l’ouverture de grandes solutions, Visual Studio 2019 a introduit le *filtrage de solution*. Le filtrage de solution permet d’ouvrir une solution avec uniquement certains projets chargés. Le chargement d’un sous-ensemble de projets d’une solution permet non seulement de réduire la durée des processus de chargement, de build et de test de la solution, mais aussi de mieux cibler la revue du code.

Les fonctionnalités suivantes sont disponibles :

- Vous pouvez accéder plus rapidement au code en ouvrant une solution sans charger ses projets. Une fois la solution ouverte, vous pouvez choisir les projets à charger.

- Quand vous rouvrez une solution, Visual Studio mémorise les projets chargés dans votre session précédente et charge uniquement ces projets.

- Vous pouvez créer un fichier de filtre de solution pour enregistrer une ou plusieurs configurations de chargement de projet ou partager la configuration avec des collègues.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows.

## <a name="open-a-filtered-solution"></a>Ouvrir une solution filtrée

Vous pouvez ouvrir une solution sans charger ses projets directement à partir de la boîte de dialogue **Ouvrir un projet** ou par le biais de la [ligne de commande](#command-line).

### <a name="open-project-dialog"></a>Boîte de dialogue Ouvrir un projet

Pour ouvrir une solution sans charger ses projets à l’aide de la boîte de dialogue **Ouvrir un projet** :

1.   >    >  Dans la barre de menus, choisissez Fichier Ouvrir le **projet/la solution** .

2. Dans la boîte de dialogue **Ouvrir un projet**, sélectionnez la solution, puis **Ne pas charger les projets**.

   ![Boîte de dialogue Ouvrir le projet de Visual Studio avec la case Ne pas charger les projets cochée](media/filtered-solutions/do-not-load-projects.png)

3. Choisissez **Ouvrir**.

   La solution s’ouvre avec tous ses projets déchargés.

4. Dans l’**Explorateur de solutions**, sélectionnez les projets à charger (appuyez sur **Ctrl** tout en cliquant sur les projets pour en sélectionner plusieurs), puis cliquez avec le bouton droit et choisissez **Recharger le projet**.

   ![Recharger plusieurs projets dans l’Explorateur de solutions Visual Studio](media/filtered-solutions/reload-project.png)

   Visual Studio mémorise les projets qui sont chargés la prochaine fois que vous ouvrez la solution localement.

### <a name="command-line"></a>Ligne de commande

(Nouveau dans Visual Studio 2019 version 16.1.)

Pour ouvrir une solution sans charger l’un de ses projets à partir de la ligne de commande, utilisez le [`/donotloadprojects`](../ide/reference/donotloadprojects-devenv-exe.md) commutateur comme indiqué dans l’exemple suivant :

```cmd
devenv /donotloadprojects MySln.sln
```

## <a name="toggle-unloaded-project-visibility"></a>Activer/désactiver la visibilité des projets déchargés

Vous pouvez choisir d’afficher tous les projets dans la solution ou seulement ceux qui sont chargés en utilisant l’une des options suivantes dans l’**Explorateur de solutions** :

- Cliquez avec le bouton droit sur votre solution, puis sélectionnez **Afficher les projets déchargés** ou **Masquer les projets déchargés**.

- Sélectionnez le nœud de la solution pour activer le bouton **Afficher tous les fichiers**, puis cliquez sur le bouton pour activer/désactiver la visibilité des projets déchargés.

   ![Bouton Afficher tous les fichiers dans l’Explorateur de solutions Visual Studio](media/filtered-solutions/show-all-files.PNG)

## <a name="load-project-dependencies"></a>Charger les dépendances de projet

Dans une solution où seuls les projets sélectionnés sont chargés, toutes les dépendances de projet d’un projet peuvent ne pas être chargées. Utilisez l’option de menu **Charger les dépendances de projet** pour vous assurer que tous les projets dont dépend un projet sont également chargés. Cliquez avec le bouton droit sur un ou plusieurs projets chargés dans **l’Explorateur de solutions** et choisissez **Charger les dépendances de projet**.

![Charger les dépendances de projet dans Visual Studio 2019](media/filtered-solutions/load-project-dependencies.png)

## <a name="solution-filter-files"></a>Fichiers de filtre de solution

Si vous souhaitez partager la configuration de chargement de votre projet ou la valider dans le contrôle de code source, vous pouvez créer un fichier de filtre de solution (avec l’extension *.slnf*). Quand vous ouvrez un fichier de filtre de solution, la solution s’ouvre dans Visual Studio avec les projets spécifiés chargés et tous les projets déchargés masqués. Vous pouvez [activer/désactiver](#toggle-unloaded-project-visibility) la visibilité des projets déchargés.

Vous pouvez distinguer les fichiers de filtre de solution des fichiers de solution standard grâce à la présence d’un glyphe supplémentaire en forme d’entonnoir en regard de la solution dans l’**Explorateur de solutions**. Le nom du filtre et le nombre de projets chargés sont également indiqués en regard du nom de la solution.

![Fichier de filtre de solution ouvert dans l’Explorateur de solutions Visual Studio](media/filtered-solutions/solution-filter.PNG)

> [!NOTE]
> Si vous ajoutez de nouveaux projets à la solution d’origine après avoir créé le fichier de filtre de solution, ils apparaissent sous la forme de projets déchargés dans l’**Explorateur de solutions**.

### <a name="create-a-solution-filter-file"></a>Créer un fichier de filtre de solution

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur la solution, puis sélectionnez **Enregistrer en tant que filtre de solution**.

   ![Menu Enregistrer en tant que filtre de solution dans l’Explorateur de solutions Visual Studio](media/filtered-solutions/save-as-solution-filter.png)

2. Choisissez un nom et un emplacement pour le fichier de filtre de solution.

Après avoir créé un fichier de filtre de solution, celui-ci est ajouté à votre liste **Projets et solutions récents** pour faciliter l’accès :

![Ouvrir les éléments récents dans Visual Studio](media/filtered-solutions/open-recent.png)

## <a name="see-also"></a>Voir aussi

- [Personnaliser l’imbrication de fichiers dans l’Explorateur de solutions](file-nesting-solution-explorer.md)
- [Optimiser le niveau de performance de Visual Studio](optimize-visual-studio-performance.md)
