---
title: Espaces de travail dans Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3489592a-dc0c-4cd3-9b08-cd367626980a
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 0230201677fd2422817ca1fbeab6679a424e5c05
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="workspaces"></a>Espaces de travail

Un espace de travail est la façon dont Visual Studio représente une collection de fichiers dans [ouvrir le dossier](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), et il est représenté par la <xref:Microsoft.VisualStudio.Workspace.IWorkspace> type. Par lui-même, l’espace de travail ne comprend pas le contenu ou les fonctionnalités liées à des fichiers dans le dossier. Au lieu de cela, il fournit un ensemble général d’API pour les fonctionnalités et extensions de produire et consommer des données d’autres personnes peuvent agir. Les producteurs sont composés via la [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) à l’aide de divers exporter les attributs.

## <a name="workspace-providers-and-services"></a>Services et les fournisseurs de l’espace de travail

Services et les fournisseurs de l’espace de travail fournissent les données et les fonctionnalités de réagir au contenu d’un espace de travail. Elles peuvent fournir des informations contextuelles de fichier, symboles dans les fichiers source, ou générer des fonctionnalités.

Les deux concepts utilisent un [modèle de fabrique](https://en.wikipedia.org/wiki/Factory_method_pattern) et importés par le biais MEF par l’espace de travail. Tous les attributs d’exportation implémentent `IProviderMetadataBase` ou `IWorkspaceServiceFactoryMetadata`, mais il existe des types concrets extensions doivent utiliser pour les types exportés.

Une différence entre les fournisseurs et les services est leur relation à l’espace de travail. Un espace de travail peut avoir de nombreux fournisseurs d’un type particulier, mais qu’un seul service d’un type particulier est créé par l’espace de travail. Par exemple, un espace de travail a de nombreux fournisseurs de scanneur de fichier, mais l’espace de travail a un seul service d’indexation par espace de travail.

Une autre différence essentielle est la consommation des données provenant de fournisseurs et les services. L’espace de travail est le point d’entrée pour obtenir des données provenant de fournisseurs pour plusieurs raisons. Tout d’abord, les fournisseurs ont généralement certaines étroit jeu de données qu’ils créent. Les données peuvent être des symboles pour un fichier source c# ou générer des contextes de fichier pour un _CMakeLists.txt_ fichier. L’espace de travail correspondra à la demande d’un consommateur pour les fournisseurs dont les métadonnées s’aligner avec la demande. En second lieu, certains scénarios autoriser pour de nombreux fournisseurs de contribuer à une demande, tandis que d’autres scénarios utilisent le fournisseur avec la priorité la plus élevée.

En revanche, les extensions peuvent obtenir des instances d’et interagir directement avec les services de l’espace de travail. Méthodes d’extension sur `IWorkspace` sont disponibles pour les services fournis par Visual Studio, tels que <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Votre extension peut offrir un service de l’espace de travail de composants au sein de votre extension ou d’autres extensions à utiliser. Les consommateurs doivent utiliser <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> ou une méthode d’extension que vous fournissez sur le `IWorkspace` type.

>[!WARNING]
> Les services qui sont en conflit avec Visual Studio ne sont pas les auteurs. Il peut entraîner des problèmes inattendus.

## <a name="disposal-on-workspace-closure"></a>Élimination de la fermeture de l’espace de travail

Fermeture d’un espace de travail, extendeurs deviez dispose, mais l’appel asynchrone code. Le <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> interface est disponible pour simplifier l’écriture de ce code facile.

## <a name="related-types"></a>Types associés

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> est l’entité centrale pour un espace de travail ouvert comme un dossier ouvert.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> Crée un fournisseur par espace de travail instancié.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> Crée un service par espace de travail instancié.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> doit être implémentée sur les fournisseurs et les services qui doivent s’exécuter de code asynchrone au cours de suppression.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> Fournit des méthodes d’assistance pour l’accès aux services connus ou services arbitraires.

## <a name="workspace-settings"></a>Paramètres de l’espace de travail

Espaces de travail ont un <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> service avec un contrôle simple mais puissant sur un espace de travail. Pour obtenir une vue d’ensemble de paramètres, consultez [personnaliser la génération et débogage des tâches](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Paramètres pour la plupart des `SettingsType` sont de types _.json_ des fichiers, tel que _VSWorkspaceSettings.json_ et _tasks.vs.json_.

La puissance des paramètres de l’espace de travail repose sur « étendues », qui sont simplement les chemins d’accès dans l’espace de travail. Lorsqu’un consommateur appelle <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A>, toutes les étendues qui incluent le chemin d’accès demandé et le type de paramètre sont agrégées. Priorité d’agrégation étendue est la suivante :

1. « Paramètres locales », ce qui correspond généralement à la racine de l’espace de travail `.vs` active.
1. Le chemin d’accès demandé lui-même.
1. Le répertoire parent du chemin d’accès demandé.
1. Tous les parents autres répertoires jusque et y compris la racine de l’espace de travail.
1. « Paramètres globaux », ce qui se trouve dans un répertoire de l’utilisateur.

Le résultat est une instance de <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings>. Cet objet contient les paramètres pour un type particulier et peut être interrogé pour définir les noms de clés stockées en tant que `string`. Le <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> méthodes et <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> les méthodes d’extension attendent que l’appelant de connaître le type de la valeur du paramètre demandé. Comme la plupart des fichiers de paramètres sont conservés en tant que _.json_ fichiers, utilisent plusieurs appels `string`, `bool`, `int`et les tableaux de ces types. Types d’objet sont également prises en charge. Dans ce cas, vous pouvez utiliser `IWorkspaceSettings` en tant que l’argument de type. Par exemple :

```json
{
  "intValue": 1,
  "stringValue": "s",
  "boolValue": true,
  "stringArray": [
    "s1",
    "s2"
  ],
  "nestedIWorkspaceSettings": {
    "nestedString": "ns"
  }
}
```

En supposant que ces paramètres ont été dans l’utilisateur _VSWorkspaceSettings.json_, les données sont accessibles en tant que :

```csharp
using System.Collections.Generic;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static void ReadSettings(IWorkspace workspace)
{
    IWorkspaceSettingsManager settingsManager = workspace.GetSettingsManager();
    IWorkspaceSettings settings = settingsManager.GetAggregatedSettings(SettingsTypes.Generic);

    // result == WorkspaceSettingsResult.Success
    WorkspaceSettingsResult result = settings.GetProperty("intValue", out int intValue);
    result = settings.GetProperty("stringValue", out string stringValue);
    result = settings.GetProperty("boolValue", out bool boolValue);
    result = settings.GetProperty("stringArray", out string[] stringArray);
    result = settings.GetProperty("nestedIWorkspaceSettings", out IWorkspaceSettings nestedIWorkspaceSettings);
    result = nestedIWorkspaceSettings.GetProperty("nestedString", out string nestedString);

    // Extension method alternative using default values.
    int intValueOrDefault = settings.Property("intValue", /* default */ 42);

    // Missing key. result == WorkspaceSettingsResult.Undefined
    result = settings.GetProperty("missing", out string missing);

    // Wrong type for a key. result == WorkspaceSettingsResult.Error
    result = settings.GetProperty("intValue", out IWorkspaceSettings notSettings);

    // Special ability to union "stringArray" across all scopes.
    IEnumerable<string> allStringArray = settings.UnionPropertyArray<string>("stringArray");
}
```

>[!NOTE]
>Ces paramètres API ne sont pas liées aux API disponibles dans le `Microsoft.VisualStudio.Settings` espace de noms. Paramètres de l’espace de travail sont indépendantes de l’hôte et utilisent les fournisseurs de paramètres dynamiques ou les fichiers de paramètres spécifiques à l’espace de travail.

### <a name="providing-dynamic-settings"></a>En fournissant des paramètres dynamiques

Extensions peuvent fournir <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider>s. Ces fournisseurs en mémoire permettent aux ajouter des paramètres ou de remplacer d’autres extensions.

Exportation d’un `IWorkspaceSettingsProvider` est différente de celle des autres fournisseurs d’espace de travail. La fabrique n’est pas `IWorkspaceProviderFactory` et il n’existe aucun type d’attribut spécial. Au lieu de cela, implémentez <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> et utiliser `[Export(typeof(IWorkspaceSettingsProviderFactory))]`.

```csharp
// Common workspace provider factory pattern
[ExportFeatureProvider(some, args, to, export)]
internal class MyProviderFactory : IWorkspaceProviderFactory<IFeatureProvider>
{
     IFeatureProvider CreateProvider(IWorkspace workspace) => new Provider(workspace);
}

// IWorkspaceSettingsProvider pattern
[Export(typeof(IWorkspaceSettingsProviderFactory))]
internal class MySettingsProviderFactory : IWorkspaceSettingsProviderFactory
{
    // 100 is typically the value used by built-in settings providers. Lower value is higher priority.
    int Priority => 100;

    IWorkspaceSettingsProvider CreateSettingsProvider(IWorkspace workspace) => new MySettingsProvider(workspace);
}
```

>[!TIP]
>Lors de l’implémentation des méthodes qui retournent `IWorkspaceSettingsSource` (comme `IWorkspaceSettingsProvider.GetSingleSettings`), retourner une instance de `IWorkspaceSettings` plutôt que `IWorkspaceSettingsSource`. `IWorkspaceSettings` Fournit des informations qui peuvent être utiles pendant les agrégations de certains paramètres.

### <a name="settings-related-apis"></a>Paramètres liés API

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> lit et regroupe les paramètres de l’espace de travail.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> Obtient le `IWorkspaceSettingsManager` pour un espace de travail.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Obtient les paramètres pour une étendue donnée agrégés sur toutes les étendues qui se chevauchent.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> contient des paramètres pour une portée spécifique.

## <a name="workspace-suggested-practices"></a>Espace de travail suggéré pratiques

- Retourner des objets à partir de `IWorkspaceProviderFactory.CreateProvider` ou des API similaires, n’oubliez pas leur `Workspace` contexte lors de la création. Interfaces de fournisseurs sont écrites attendue de que cet objet est conservé lors de la création.
- Enregistrez les caches de l’espace de travail spécifiques ou des paramètres dans le chemin d’accès « Paramètres Local » de l’espace de travail. Créer un chemin d’accès pour votre fichier à l’aide `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` dans Visual Studio 2017 15,6 ou version ultérieure. Pour les versions antérieures à la version 15,6, utilisez l’extrait de code suivant :

```csharp
using System.IO;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static string MakeRootedUnderWorkingFolder(IWorkspace workspace, string relativePath)
{
    string workingFolder = workspace.GetSettingsManager().GetAggregatedSettings(SettingsTypes.WorkspaceControlSettings).Property<string>("WorkingFolder");
    return Path.Combine(workingFolder, relativePath);
}
```

## <a name="solution-events-and-package-auto-load"></a>Événements de la solution et auto-chargement du package

Charger des packages peuvent implémenter `IVsSolutionEvents7` et appeler `IVsSolution.AdviseSolutionEvents`. Il inclut la gestion des événements sur l’ouverture et fermeture d’un dossier dans Visual Studio.

Un contexte de l’interface utilisateur peut être utilisé pour charger automatiquement votre package. La valeur est `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>Le package SourceExplorerPackage n’a pas été chargé correctement

Extensibilité de l’espace de travail très basé sur MEF, et les erreurs de composition entraînera le package à ouvrir le dossier pour l’échec du chargement d’hébergement. Par exemple, si une extension exporte un type avec `ExportFileContextProviderAttribute`, mais le type implémente uniquement `IWorkspaceProviderFactory<IFileContextActionProvider>`, une erreur se produit lorsque vous tentez d’ouvrir un dossier dans Visual Studio. Vous trouverez les détails de l’erreur dans _%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_. Résolvez les erreurs de types implémentés par votre extension.

## <a name="next-steps"></a>Étapes suivantes

* [Contextes de fichiers](workspace-file-contexts.md) -fournisseurs de contexte de fichier mettre l’intelligence de code pour les espaces de travail ouvrir le dossier. 
* [L’indexation](workspace-indexing.md) -indexation de l’espace de travail de collecte et conserve les informations sur l’espace de travail.
