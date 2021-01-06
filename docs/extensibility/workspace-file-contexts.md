---
title: Contextes de fichiers de l’espace de travail dans Visual Studio | Microsoft Docs
description: En savoir plus sur les fournisseurs de contexte de fichier qui implémentent l’interface IFileContextProvider pour prendre en charge des Insights dans les espaces de travail de dossier ouverts.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 271b05d78123136d47cb618e8ed38cea64b7beac
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877063"
---
# <a name="workspace-file-contexts"></a>Contextes de fichiers de l’espace de travail

Toutes les informations sur les espaces de travail de [dossier ouverts](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) sont produites par des « fournisseurs de contexte de fichier » qui implémentent l' <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> interface. Ces extensions peuvent rechercher des modèles dans des dossiers ou des fichiers, lire des fichiers et makefiles MSBuild, détecter les dépendances de package, etc. afin d’accumuler les Insights dont ils ont besoin pour définir un contexte de fichier. Un contexte de fichier en lui-même n’exécute aucune action, mais fournit plutôt des données qu’une autre extension peut ensuite agir.

Chaque <xref:Microsoft.VisualStudio.Workspace.FileContext> est associé à un `Guid` qui identifie le type de données qu’il transporte. Un espace de travail l’utilise `Guid` ultérieurement pour le faire correspondre aux extensions qui consomment les données par le biais de la <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> propriété. Un fournisseur de contexte de fichier est exporté avec des métadonnées qui identifient le contexte `Guid` de fichier pour lequel il peut produire des données.

Une fois défini, un contexte de fichier peut être associé à un nombre quelconque de fichiers ou de dossiers dans l’espace de travail. Un fichier ou un dossier donné peut être associé à un nombre quelconque de contextes de fichier. Il s’agit d’une relation plusieurs-à-plusieurs.

Les scénarios les plus courants pour les contextes de fichier sont liés aux services de génération, de débogage et de langage. Pour plus d’informations, consultez les autres rubriques associées à ces scénarios.

## <a name="file-context-lifecycle"></a>Cycle de vie du contexte de fichier

Les cycles de vie d’un `FileContext` sont non déterministes. À tout moment, un composant peut demander de façon asynchrone un ensemble de types de contexte. Les fournisseurs qui prennent en charge un sous-ensemble des types de contexte de demande seront interrogés. L' `IWorkspace` instance joue le rôle d’intermédiaire entre le consommateur et les fournisseurs par le biais de la <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> méthode. Les consommateurs peuvent demander un contexte et effectuer une action à long terme basée sur le contexte, tandis que d’autres peuvent demander un contexte et maintenir une référence durable.

Des modifications peuvent se produire dans les fichiers qui provoquent l’indisponibilité d’un contexte de fichier. Le fournisseur peut déclencher un événement sur le `FileContext` pour informer les consommateurs des mises à jour. Par exemple, si un contexte de génération est fourni pour un fichier mais qu’une modification sur disque invalide ce contexte, le producteur d’origine peut appeler l’événement. Tout consommateur faisant toujours référence à qui `FileContext` peut ensuite recréer une requête pour un nouveau `FileContext` .

>[!NOTE]
>Il n’y a pas de modèle push pour les consommateurs. Les consommateurs ne sont pas avertis du nouveau fournisseur `FileContext` après leur demande.

## <a name="expensive-file-context-computations"></a>Calculs coûteux de contexte de fichier

La lecture du contenu du fichier à partir du disque peut être coûteuse, en particulier lorsqu’un fournisseur doit résoudre la relation entre les fichiers. Par exemple, un fournisseur peut être interrogé pour le contexte de fichier d’un fichier source, mais le contexte de fichier dépend des métadonnées d’un fichier projet. L’analyse du fichier projet ou son évaluation avec MSBuild est coûteuse. Au lieu de cela, l’extension peut exporter un `IFileScanner` pour créer des `FileDataValue` données pendant l’indexation de l’espace de travail. Désormais, lorsque vous êtes invité à entrer des contextes de fichier, le `IFileContextProvider` peut rapidement interroger ces données indexées. Pour plus d’informations sur l’indexation, consultez la rubrique [indexation de l’espace de travail](workspace-indexing.md) .

>[!WARNING]
>Méfiez-vous des autres façons dont le `FileContext` calcul peut être coûteux. Certaines interactions de l’interface utilisateur sont synchrones et s’appuient sur un volume élevé de `FileContext` demandes. Par exemple, l’ouverture d’un onglet Éditeur et l’ouverture d’un menu contextuel **Explorateur de solutions** . Ces actions effectuent de nombreuses demandes de type de contexte de génération.

## <a name="file-context-related-apis"></a>API associées au contexte de fichier

- <xref:Microsoft.VisualStudio.Workspace.FileContext> contient des données et des métadonnées.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> et <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> créent le contexte de fichier.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> exporte un fournisseur de contexte de fichier.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> est utilisé par les consommateurs pour obtenir des contextes de fichier.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> définit les types de contexte de génération que le dossier ouvert utilisera.

## <a name="file-context-actions"></a>Actions du contexte de fichier

Alors qu’il `FileContext` s’agit simplement de données relatives à un ou plusieurs fichiers, un <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> est un moyen d’exprimer et d’agir sur ces données. `IFileContextAction` est flexible dans son utilisation. Deux de ses cas les plus courants sont la génération et le débogage.

## <a name="reporting-progress"></a>Signalement de la progression

La <xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> méthode est passée `IProgress<IFileContextActionProgressUpdate>` , mais l’argument ne doit pas être utilisé comme ce type. `IFileContextActionProgressUpdate` est une interface vide et l’appel de `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` peut lever une exception `NotImplementedException` . Au lieu de cela, le `IFileContextAction` doit effectuer un cast de l’argument vers un autre type en fonction des besoins du scénario.

Pour plus d’informations sur les types fournis par Visual Studio, consultez la documentation du scénario respectif.

## <a name="file-context-action-related-apis"></a>API associées à l’action de contexte de fichier

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> exécute un comportement basé sur un `FileContext` .
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> crée des instances de `IFileContextAction` .
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> exporte le type `IWorkspaceProviderFactory<IFileContextActionProvider>` .

## <a name="file-watching"></a>Surveillance des fichiers

Un espace de travail écoute les notifications de modification de fichier et fournit le <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> via <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . Les fichiers qui correspondent au paramètre « ExcludedItems » ne génèrent pas d’événements de notification de fichier. Un seuil entre les événements est utilisé pour la simplification des notifications et la réduction des doublons. Lorsque vous devez réagir à une modification de fichier, vous devez vous abonner à ce service.

>[!TIP]
>Le service d' [indexation](workspace-indexing.md) d’un espace de travail s’abonne aux événements de fichier par défaut. Les ajouts et les modifications de fichiers entraînent l' `IFileScanner` appel des événements s pertinents pour les nouvelles données de ce fichier. Les suppressions de fichiers entraînent la suppression des données indexées. Vous n’avez pas besoin de vous abonner `IFileScanner` au service de l’observateur de fichiers.

## <a name="next-steps"></a>Étapes suivantes

* [Indexation](workspace-indexing.md) : l’indexation d’espace de travail collecte et conserve les informations relatives à l’espace de travail.
* [Espaces de travail](workspaces.md) : Examinez les concepts et le stockage des paramètres de l’espace de travail.
