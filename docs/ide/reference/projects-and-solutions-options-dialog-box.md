---
title: Projets et solutions, boîte de dialogue Options
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ed60e07c625665f92838cfbc671b03c605fda0d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567643"
---
# <a name="options-dialog-box-projects-and-solutions--general"></a>Boîte de dialogue Options : projets et solutions \> général

Utilisez cette page pour définir le comportement de Visual Studio relativement aux projets et aux solutions. Pour accéder à ces options, sélectionnez **Outils** > **Options**, développez **Projets et solutions** et sélectionnez **Général**.

Les options suivantes sont disponibles dans la page **Général**.

## <a name="always-show-error-list-if-build-finishes-with-errors"></a>Toujours afficher la liste d'erreurs à la fin de la génération avec erreurs

Ouvre la fenêtre **Liste d’erreurs** à l’achèvement de build, uniquement en cas d’échec de la génération du projet. Les erreurs qui se produisent pendant le processus de génération sont affichées. Lorsque cette option est désactivée, les erreurs persistent, mais la fenêtre ne s'ouvre pas quand la génération est terminée. Cette option est activée par défaut.

## <a name="track-active-item-in-solution-explorer"></a>Suivre un élément actif dans l’Explorateur de solutions

Quand l’option est sélectionnée, l’**Explorateur de solutions** s’ouvre automatiquement et l’élément actif est sélectionné. L'élément sélectionné change au fur et à mesure que vous utilisez différents fichiers dans un projet ou une solution, ou différents composants dans un concepteur. Quand cette option est désactivée, la sélection de l’**Explorateur de solutions** ne change pas automatiquement. Cette option est activée par défaut.

## <a name="show-advanced-build-configurations"></a>Afficher les configurations de build avancées

Quand cette option est sélectionnée, les options de configuration de build apparaissent dans les boîtes de dialogue **Pages de propriétés du projet** et **Pages de propriétés de la solution**. Si l’option est désactivée, les options de configuration de build n’apparaissent pas dans les boîtes de dialogue **Pages de propriétés du projet** et **Pages de propriétés de la solution** pour les projets Visual Basic et C# qui contiennent une seule configuration ou les deux configurations debug et release. Si un projet possède une configuration définie par l'utilisateur, les options de configuration de build sont affichées.

Si l’option n’est pas sélectionnée, les commandes du menu **Générer**, telles que **Générer la solution**, **Régénérer la solution** et **Nettoyer la solution**, sont exécutées sur la configuration Release et les commandes du menu **Déboguer**, telles que **Démarrer le débogage** et **Exécuter sans débogage**, sont exécutées sur la configuration Debug.

## <a name="always-show-solution"></a>Toujours afficher la solution

Lorsque cette option est sélectionnée, la solution et toutes les commandes qui agissent sur les solutions sont toujours affichées dans l'IDE. Lorsqu'elle est désactivée, tous les projets sont créés comme projets autonomes. En outre, vous ne voyez pas la solution dans l'Explorateur de solutions ou les commandes qui agissent sur les solutions dans l'IDE si la solution contient un seul projet.

::: moniker range="vs-2017"

## <a name="save-new-projects-when-created"></a>Enregistrer les nouveaux projets lors de leur création

Quand cette option est sélectionnée, vous pouvez spécifier un emplacement pour votre projet dans la boîte de dialogue **Nouveau projet**. Lorsqu'elle est désactivée, tous les nouveaux projets sont créés en tant que projets temporaires. Lorsque vous travaillez avec des projets temporaires, vous pouvez créer un projet et l'expérimenter sans avoir à spécifier un emplacement sur le disque.

::: moniker-end

## <a name="warn-user-when-the-project-location-is-not-trusted"></a>Prévenir l'utilisateur lorsque l'emplacement du projet n'est pas fiable

Si vous tentez de créer un projet ou d’ouvrir un projet existant dans un emplacement qui n’est pas totalement fiable (par exemple, un chemin UNC ou un chemin HTTP), un message s’affiche. Utilisez cette option pour spécifier si le message s'affiche chaque fois que vous essayez de créer ou d'ouvrir un projet dans un emplacement qui n'est pas entièrement fiable.

## <a name="show-output-window-when-build-starts"></a>Afficher la fenêtre Sortie au démarrage de la génération

Affiche automatiquement la [fenêtre Sortie](../../ide/reference/output-window.md) dans l’IDE au démarrage des générations de la solution.

## <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Inviter à utiliser des noms symboliques au moment de renommer les fichiers

Quand cette option est sélectionnée, Visual Studio affiche un message demandant s’il doit également renommer toutes les références du projet à l’élément de code.

## <a name="prompt-before-moving-files-to-a-new-location"></a>Demander avant de déplacer les fichiers vers un nouvel emplacement

Quand cette option est sélectionnée, Visual Studio affiche un message de confirmation avant que les emplacements des fichiers ne soient changés dans l’**Explorateur de solutions**.

## <a name="reopen-documents-on-solution-load"></a>Rouvrir les documents au chargement de la solution

Quand cette option est sélectionnée, les documents qui ont été laissés ouverts lors de la précédente fermeture de cette solution s’ouvrent automatiquement lors de l’ouverture de la solution.

La réouverture de certains types de fichiers ou concepteurs peut ralentir le chargement de la solution. Désactivez cette option pour [améliorer les performances de chargement de la solution](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) si vous ne souhaitez pas restaurer le contexte précédent de la solution.

::: moniker range=">=vs-2019"

## <a name="restore-solution-explorer-project-hierarchy-state-on-solution-load"></a>Restaurer l’état de la hiérarchie de projets de l’Explorateur de solutions au moment du chargement de la solution

Quand cette option est sélectionnée, elle restaure l’état des nœuds dans l’Explorateur de solutions selon qu’ils étaient développés ou réduits lors de la dernière ouverture de la solution. Désélectionnez cette option pour diminuer le temps de chargement de la solution pour des grandes solutions.

> [!TIP]
> Si vous désactivez cette option, un moyen simple d’accéder au document actif dans l’Explorateur de solutions consiste à sélectionner **Synchroniser avec le document actif** dans la barre d’outils de l’**Explorateur de solutions**.
>
> ![Synchroniser avec le document actif dans Explorateur de solutions](media/sync-active-document.png)

## <a name="open-sdk-style-project-files-with-double-click-or-the-enter-key"></a>Ouvrir les fichiers projet de style SDK par un double-clic ou à l’aide de la touche Entrée

Quand cette option est sélectionnée et que vous double-cliquez sur un nœud de projet de style SDK dans l’Explorateur de solutions, ou que vous le sélectionnez et que vous appuyez sur **Entrée**, le fichier projet (par exemple le fichier \*.csproj) s’ouvre au format XML dans l’éditeur. Quand cette option est désélectionnée, le fait de double-cliquer sur un nœud de projet de style SDK dans l’Explorateur de solutions, ou de le sélectionner et d’appuyer sur **Entrée**, a pour seul effet de développer ou de réduire ce nœud.

Si cette option n’est pas sélectionnée et que vous voulez modifier un fichier projet de style SDK, cliquez avec le bouton droit sur le nœud du projet dans l’Explorateur de solutions, puis sélectionnez **Modifier le fichier projet**. Pour les autres types de projets, vous devez d’abord décharger le projet avant de le modifier dans Visual Studio.

> [!TIP]
> Un *projet de style SDK*, ou [projet SDK](../../msbuild/how-to-use-project-sdk.md), a un format de fichier projet plus récent et plus simple, qui a été introduit avec MSBuild 15.0. Un projet de style SDK contient un attribut `Sdk` sur l’élément `Project`, par exemple `<Project Sdk="Microsoft.NET.Sdk">`. Visual Studio crée un projet de style SDK par exemple quand vous créez un projet .NET Core à partir d’un des modèles Visual Studio.

::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Boîte de dialogue Options : projets et solutions \> emplacements](projects-solutions-locations-options.md)
- [Options (boîte de dialogue), Projets et solutions, Générer et exécuter](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Boîte de dialogue Options, Projets et solutions, Projets web](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
