---
title: Projets et solutions, boîte de dialogue Options
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
- VS.ToolsOptionsPages.Projects.Locations
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dbd3fe20377cd2aa4954e904fec50702cc9b7120
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843989"
---
# <a name="projects-and-solutions-page-options-dialog-box"></a>Page Projets et solutions, boîte de dialogue Options

Définit le comportement des projets et des solutions Visual Studio. Pour accéder à ces options, sélectionnez **Outils** > **Options**, développez **Projets et solutions** et sélectionnez **Général**.

Définissez les chemins par défaut des dossiers de projet et de modèle dans l’onglet **Emplacements** de la même boîte de dialogue.

> [!NOTE]
> Les options disponibles dans l’interface utilisateur peuvent différer de ce qui est décrit ici, en fonction de vos paramètres actifs ou de votre édition. Cet article concerne les **Paramètres de développement généraux**. Pour afficher ou modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-page"></a>Page Général

Les options suivantes sont disponibles dans la page **Général**.

### <a name="always-show-error-list-if-build-finishes-with-errors"></a>Toujours afficher la liste d'erreurs à la fin de la génération avec erreurs

Ouvre la fenêtre **Liste d’erreurs** à l’achèvement de build, uniquement en cas d’échec de la génération du projet. Les erreurs qui se produisent pendant le processus de génération sont affichées. Lorsque cette option est désactivée, les erreurs persistent, mais la fenêtre ne s'ouvre pas quand la génération est terminée. Cette option est activée par défaut.

### <a name="track-active-item-in-solution-explorer"></a>Suivre un élément actif dans l’Explorateur de solutions

Quand l’option est sélectionnée, l’**Explorateur de solutions** s’ouvre automatiquement et l’élément actif est sélectionné. L'élément sélectionné change au fur et à mesure que vous utilisez différents fichiers dans un projet ou une solution, ou différents composants dans un concepteur. Quand cette option est désactivée, la sélection de l’**Explorateur de solutions** ne change pas automatiquement. Cette option est activée par défaut.

### <a name="show-advanced-build-configurations"></a>Afficher les configurations de build avancées

Quand cette option est sélectionnée, les options de configuration de build apparaissent dans les boîtes de dialogue **Pages de propriétés du projet** et **Pages de propriétés de la solution**. Si l’option est désactivée, les options de configuration de build n’apparaissent pas dans les boîtes de dialogue **Pages de propriétés du projet** et **Pages de propriétés de la solution** pour les projets Visual Basic et C# qui contiennent une seule configuration ou les deux configurations debug et release. Si un projet possède une configuration définie par l'utilisateur, les options de configuration de build sont affichées.

Si l’option n’est pas sélectionnée, les commandes du menu **Générer**, telles que **Générer la solution**, **Régénérer la solution** et **Nettoyer la solution**, sont exécutées sur la configuration Release et les commandes du menu **Déboguer**, telles que **Démarrer le débogage** et **Exécuter sans débogage**, sont exécutées sur la configuration Debug.

### <a name="always-show-solution"></a>Toujours afficher la solution

Lorsque cette option est sélectionnée, la solution et toutes les commandes qui agissent sur les solutions sont toujours affichées dans l'IDE. Lorsqu'elle est désactivée, tous les projets sont créés comme projets autonomes. En outre, vous ne voyez pas la solution dans l'Explorateur de solutions ou les commandes qui agissent sur les solutions dans l'IDE si la solution contient un seul projet.

### <a name="save-new-projects-when-created"></a>Enregistrer les nouveaux projets lors de leur création

Quand cette option est sélectionnée, vous pouvez spécifier un emplacement pour votre projet dans la boîte de dialogue **Nouveau projet**. Lorsqu'elle est désactivée, tous les nouveaux projets sont créés en tant que projets temporaires. Lorsque vous travaillez avec des projets temporaires, vous pouvez créer un projet et l'expérimenter sans avoir à spécifier un emplacement sur le disque.

### <a name="warn-user-when-the-project-location-is-not-trusted"></a>Prévenir l'utilisateur lorsque l'emplacement du projet n'est pas fiable

Si vous tentez de créer un projet ou d’ouvrir un projet existant dans un emplacement qui n’est pas totalement fiable (par exemple, un chemin UNC ou un chemin HTTP), un message s’affiche. Utilisez cette option pour spécifier si le message s'affiche chaque fois que vous essayez de créer ou d'ouvrir un projet dans un emplacement qui n'est pas entièrement fiable.

### <a name="show-output-window-when-build-starts"></a>Afficher la fenêtre Sortie au démarrage de la génération

Affiche automatiquement la [fenêtre Sortie](../../ide/reference/output-window.md) dans l’IDE au démarrage des générations de la solution.

### <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Inviter à utiliser des noms symboliques au moment de renommer les fichiers

Quand cette option est sélectionnée, Visual Studio affiche un message demandant s’il doit également renommer toutes les références du projet à l’élément de code.

### <a name="prompt-before-moving-files-to-a-new-location"></a>Demander avant de déplacer les fichiers vers un nouvel emplacement

Quand cette option est sélectionnée, Visual Studio affiche un message de confirmation avant que les emplacements des fichiers ne soient changés dans l’**Explorateur de solutions**.

### <a name="reopen-documents-on-solution-load"></a>Rouvrir les documents au chargement de la solution

**Nouveautés de Visual Studio 2017 version 15.8 préversion 2 et ultérieures**

Quand cette option est sélectionnée, les documents qui ont été laissés ouverts lors de la précédente fermeture de cette solution s’ouvrent automatiquement lors de l’ouverture de la solution.

La réouverture de certains types de fichiers ou concepteurs peut ralentir le chargement de la solution. Désactivez cette option pour [améliorer les performances de chargement de la solution](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) si vous ne souhaitez pas restaurer le contexte précédent de la solution.

## <a name="locations-page"></a>Page Emplacements

Les options suivantes sont disponibles dans la page **Emplacements**.

### <a name="projects-location"></a>Emplacement des projets

Spécifie l’emplacement par défaut où Visual Studio crée des projets et des dossiers de solution. Plusieurs boîtes de dialogue utilisent aussi l'emplacement défini dans cette option comme point de démarrage des dossiers. Par exemple, la boîte de dialogue **Ouvrir un projet** utilise cet emplacement pour le raccourci **Mes projets**.

### <a name="user-project-templates-location"></a>Emplacement des modèles des projets utilisateur

Spécifie l’emplacement par défaut que la boîte de dialogue **Nouveau projet** utilise pour créer la liste de **Mes modèles**. Pour plus d’informations, consultez [Guide pratique pour localiser et organiser les modèles](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

### <a name="user-item-templates-location"></a>Emplacement des modèles des éléments utilisateur

Spécifie l’emplacement par défaut que la boîte de dialogue **Ajouter un nouvel élément** utilise pour créer la liste de **Mes modèles**. Pour plus d’informations, consultez [Guide pratique pour localiser et organiser les modèles](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Voir aussi

- [Options (boîte de dialogue), Projets et solutions, Générer et exécuter](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Boîte de dialogue Options, Projets et solutions, Projets web](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
