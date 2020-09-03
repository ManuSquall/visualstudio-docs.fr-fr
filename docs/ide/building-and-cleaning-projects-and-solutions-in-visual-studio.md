---
title: Génération et nettoyage des projets et des solutions
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
f1_keywords:
- VS.BuildProjectPicker
- vs.batchbuild
helpviewer_keywords:
- Clean Solution command
- builds [Visual Studio], managing
- solution build configurations, starting
- Build Solution command
- project build configurations, starting
- build configurations, starting
- project build configurations, dependencies
- Rebuild Solution command
- solution build configurations, build order
- builds [Visual Studio], preparing
ms.assetid: 710891fd-379e-42c2-a84b-44a7af694ca0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1cf71abb19f6d4a3a459b4e5559e536f18f41c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114559"
---
# <a name="build-and-clean-projects-and-solutions-in-visual-studio"></a>Générer et nettoyer des projets et des solutions dans Visual Studio

En appliquant les procédures décrites dans cette rubrique, vous pouvez générer, régénérer ou nettoyer tout ou partie des projets ou éléments de projet dans une solution. Pour obtenir un didacticiel pas à pas, consultez [Procédure pas à pas : génération d’une application](../ide/walkthrough-building-an-application.md).

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Générer et nettoyer des projets et des solutions dans Visual Studio pour Mac](/visualstudio/mac/building-and-cleaning-projects-and-solutions).

> [!NOTE]
> En fonction de vos paramètres actifs, l’interface utilisateur dans votre édition de Visual Studio peut-être différente de celle décrite dans cette rubrique. Pour modifier vos paramètres, par exemple pour définir les paramètres **Général** ou **Visual C++**, choisissez **Outils** > **Importation et exportation de paramètres**, puis choisissez **Réinitialiser tous les paramètres**.

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Pour générer, régénérer ou nettoyer une solution entière

1. Dans l’**Explorateur de solutions**, choisissez ou ouvrez la solution.

2. Dans la barre de menus, choisissez **Générer**, puis choisissez l’une des commandes suivantes :

    - Choisissez **Générer** ou **Générer la Solution** pour compiler uniquement les fichiers de projet et les composants qui ont été modifiés depuis la dernière génération.

        > [!NOTE]
        > La commande **Générer** devient **Générer la Solution** quand une solution contient plusieurs projets.

    - Choisissez **Régénérer la Solution** pour « nettoyer » la solution, puis générer tous les fichiers projet et les composants.

    - Choisissez **Nettoyer la solution** pour supprimer tous les fichiers intermédiaires et de sortie. De nouvelles instances des fichiers intermédiaires et de sortie peuvent alors être générées avec uniquement les fichiers projet et les composant restants.

## <a name="to-build-or-rebuild-a-single-project"></a>Pour générer ou régénérer un projet unique

1. Dans l’**Explorateur de solutions**, choisissez ou ouvrez le projet.

2. Dans la barre de menus, choisissez **Générer**, puis **Générer** *ProjectName* ou **Régénérer** *ProjectName*.

    - Choisissez **Générer** *ProjectName* pour générer uniquement les composants qui ont été modifiés depuis la dernière génération du projet.

    - Choisissez **Régénérer** *ProjectName* pour « nettoyer » le projet, puis générer les fichiers projet et tous les composants du projet.

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Pour générer uniquement le projet de démarrage et ses dépendances

1. Dans la barre de menus, choisissez **Outils**  >  **options**.

2. Dans la boîte de dialogue **Options**, développez le nœud **Projets et solutions**, puis choisissez la page **Générer et exécuter**.

     La boîte de dialogue **générer et exécuter**des  >  **projets et des solutions**  >  **Options** s’ouvre.

3. Cochez la case **Générer des projets de démarrage et des dépendances à l’exécution**.

     Quand cette case est cochée, seuls le projet de démarrage actuel et ses dépendances sont générés quand vous effectuez l’une des opérations suivantes :

    - Dans la barre de menus, choisissez **Déboguer**  >  **Démarrer** (**F5**).

    - Dans la barre de menus, choisissez **générer**  >  **générer la solution** (**CTRL** + **MAJ** + **B**).

    Quand cette case est décochée, tous les projets, leurs dépendances et les fichiers solution sont générés quand vous exécutez l’une des commandes précédentes. Par défaut, cette case à cocher est désactivée.

## <a name="to-build-only-the-selected-visual-c-project"></a>Pour générer uniquement le projet Visual C++ sélectionné

Choisissez un [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projet, puis, dans la barre de menus, choisissez **générer**le  >  **projet uniquement**et l’une des commandes suivantes :

- **Générer uniquement** *nom_projet*

- **Régénérer uniquement** *nom_projet*

- **Nettoyer uniquement** *nom_projet*

- **Lier uniquement** *nom_projet*

Ces commandes s’appliquent uniquement au projet [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] que vous avez choisi, sans générer, régénérer, nettoyer ou lier aucune dépendance de projet ou fichier de solution. En fonction de votre version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], le sous-menu **Projet uniquement** peut contenir plus de commandes.

## <a name="to-compile-multiple-c-project-items"></a>Pour compiler plusieurs éléments de projet C++

Dans l’**Explorateur de solutions**, choisissez plusieurs fichiers qui ont plusieurs actions de compilation, ouvrez le menu contextuel pour l’un de ces fichiers, puis choisissez **Compiler**.

Si les fichiers ont des dépendances, ils seront compilés par ordre de dépendance. La compilation échoue si les fichiers nécessitent un en-tête précompilé qui n’est pas disponible lors de la compilation. L’opération de compilation utilise la configuration de solution active.

## <a name="to-stop-a-build"></a>Pour arrêter une génération

Effectuez l'une des étapes suivantes :

- Dans la barre de menus, sélectionnez **générer**  >  **Annuler**.

- Appuyez sur **CTRL** + **Pause**.

## <a name="see-also"></a>Voir aussi

- [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Obtention des journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Compilation et génération](../ide/compiling-and-building-in-visual-studio.md)
- [Présentation des configurations de build](../ide/understanding-build-configurations.md)
- [Guide pratique pour définir des configurations de débogage et des configurations Release](../debugger/how-to-set-debug-and-release-configurations.md)
- [Informations de référence sur la génération C/C++](/cpp/build/reference/c-cpp-building-reference)
- [Devenv command line switches](../ide/reference/devenv-command-line-switches.md)
- [Solutions et projets](../ide/solutions-and-projects-in-visual-studio.md)
- [Générer et nettoyer des projets et des solutions (Visual Studio pour Mac)](/visualstudio/mac/building-and-cleaning-projects-and-solutions)
