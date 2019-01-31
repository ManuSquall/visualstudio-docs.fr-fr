---
title: Charge un sous-ensemble de projets
ms.date: 12/04/2018
ms.topic: conceptual
ms.prod: visual-studio-dev16
helpviewer_keywords:
- filtered solution
- solution filtering
author: gewarren
ms.author: stsu
manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: 1ce2c3fbb8386cb58e096e526dc27b03d16e428e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972558"
---
# <a name="filtered-solutions-in-visual-studio"></a>Solutions filtrées dans Visual Studio

**Nouveautés de Visual Studio 2019 Preview 1**

La collaboration entre grandes équipes de développement passe souvent par une vaste solution unique comprenant de nombreux projets. Toutefois, les développeurs individuels travaillent généralement sur un petit sous-ensemble de ces projets. Pour améliorer les performances associées à l’ouverture de grandes solutions, Visual Studio 2019 Preview 1 introduit le *filtrage de solution*. Le filtrage de solution permet d’ouvrir une solution avec uniquement certains projets chargés. Le chargement d’un sous-ensemble de projets d’une solution permet non seulement de réduire la durée des processus de chargement, de build et de test de la solution, mais aussi de mieux cibler la revue du code.

Les fonctionnalités suivantes sont disponibles :

- Vous pouvez accéder plus rapidement au code en ouvrant une solution sans charger ses projets. Une fois la solution ouverte, vous pouvez choisir les projets à charger.

- Quand vous rouvrez une solution, Visual Studio mémorise les projets chargés dans votre session précédente et charge uniquement ces projets.

- Vous pouvez créer un fichier de filtre de solution pour enregistrer une ou plusieurs configurations de chargement de projet ou partager la configuration avec des collègues.

## <a name="open-a-filtered-solution"></a>Ouvrir une solution filtrée

Pour ouvrir une solution en chargeant uniquement certains de ses projets, effectuez les étapes suivantes :

1. Dans la barre de menus, choisissez **Fichier** > **Ouvrir** > **Projet/Solution**.

2. Dans la boîte de dialogue **Nouveau projet**, sélectionnez la solution, puis **Ne pas charger les projets**.

   ![Boîte de dialogue Ouvrir le projet de Visual Studio avec la case Ne pas charger les projets cochée](media/filtered-solutions/do-not-load-projects.png)

3. Choisissez **Ouvrir**.

   La solution s’ouvre avec tous ses projets déchargés.

4. Dans l’**Explorateur de solutions**, sélectionnez les projets à charger (appuyez sur **Ctrl** tout en cliquant sur les projets pour en sélectionner plusieurs), puis cliquez avec le bouton droit et choisissez **Recharger le projet** .

   ![Recharger plusieurs projets dans l’Explorateur de solutions Visual Studio](media/filtered-solutions/reload-project.png)

   Visual Studio mémorise les projets qui sont chargés la prochaine fois que vous ouvrez la solution localement.

## <a name="toggle-unloaded-project-visibility"></a>Activer/désactiver la visibilité des projets déchargés

Vous pouvez choisir d’afficher tous les projets dans la solution ou seulement ceux qui sont chargés en utilisant l’une des options suivantes dans l’**Explorateur de solutions** :

- Cliquez avec le bouton droit sur votre solution, puis sélectionnez **Afficher les projets déchargés** ou **Masquer les projets déchargés**.

- Sélectionnez le bouton **Afficher tous les fichiers** pour activer/désactiver la visibilité des projets déchargés.

   ![Bouton Afficher tous les fichiers dans l’Explorateur de solutions Visual Studio](media/filtered-solutions/show-all-files.PNG)

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
- [Optimiser les performances de Visual Studio](optimize-visual-studio-performance.md)