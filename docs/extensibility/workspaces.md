---
title: Espaces de travail dans Visual Studio | Microsoft Docs
description: Découvrez comment Visual Studio utilise un espace de travail pour représenter une collection de fichiers dans le dossier ouvert, y compris les fournisseurs d’espace de travail et les services.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 1ed660a5f52aba548d087b28f7caea4d1966fe45
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876946"
---
# <a name="workspaces"></a>Workspaces

Un espace de travail est la manière dont Visual Studio représente une collection de fichiers dans le [dossier ouvert](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), et il est représenté par le <xref:Microsoft.VisualStudio.Workspace.IWorkspace> type. L’espace de travail ne comprend pas le contenu ou les fonctionnalités liées aux fichiers dans le dossier. Au lieu de cela, il fournit un ensemble général d’API pour les fonctionnalités et les extensions pour produire et consommer des données sur lesquelles d’autres utilisateurs peuvent agir. Les producteurs sont composés du [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) à l’aide de différents attributs d’exportation.

## <a name="workspace-providers-and-services"></a>Fournisseurs et services d’espace de travail

Les fournisseurs d’espace de travail et les services fournissent les données et les fonctionnalités permettant de réagir au contenu d’un espace de travail. Ils peuvent fournir des informations de fichier contextuel, des symboles dans les fichiers sources ou des fonctionnalités de génération.

Les deux concepts utilisent un [modèle de fabrique](https://en.wikipedia.org/wiki/Factory_method_pattern) et sont importés via MEF par l’espace de travail. Tous les attributs d’exportation implémentent `IProviderMetadataBase` ou `IWorkspaceServiceFactoryMetadata` , mais il existe des types concrets que les extensions doivent utiliser pour les types exportés.

L’une des différences entre les fournisseurs et les services est leur relation avec l’espace de travail. Un espace de travail peut avoir de nombreux fournisseurs d’un type particulier, mais un seul service d’un type particulier est créé par espace de travail. Par exemple, un espace de travail contient de nombreux fournisseurs d’analyseurs de fichiers, mais l’espace de travail n’a qu’un seul service d’indexation par espace de travail.

Une autre différence clé réside dans la consommation des données des fournisseurs et des services. L’espace de travail est le point d’entrée pour obtenir des données des fournisseurs pour plusieurs raisons. Tout d’abord, les fournisseurs possèdent généralement un ensemble étroit de données qu’ils créent. Les données peuvent être des symboles pour un fichier source C# ou des contextes de fichier de build pour un fichier _CMakeLists.txt_ . L’espace de travail correspondra à la demande d’un consommateur aux fournisseurs dont les métadonnées s’alignent sur la demande. Deuxièmement, certains scénarios permettent à de nombreux fournisseurs de contribuer à une requête, tandis que d’autres scénarios utilisent le fournisseur avec la priorité la plus élevée.

En revanche, les extensions peuvent recevoir des instances de et interagir directement avec les services d’espace de travail. Les méthodes d’extension sur `IWorkspace` sont disponibles pour les services fournis par Visual Studio, tels que <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . Votre extension peut offrir un service d’espace de travail pour les composants de votre extension ou pour d’autres extensions à consommer. Les consommateurs doivent utiliser <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> ou une méthode d’extension que vous fournissez sur le `IWorkspace` type.

>[!WARNING]
> N’autorisez pas les services qui sont en conflit avec Visual Studio. Cela peut entraîner des problèmes inattendus.

## <a name="disposal-on-workspace-closure"></a>Suppression sur la fermeture de l’espace de travail

Lors de la fermeture d’un espace de travail, les extendeurs devront peut-être les supprimer mais appeler du code asynchrone. L' <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> interface est disponible pour faciliter l’écriture de ce code.

## <a name="related-types"></a>Types associés

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> est l’entité centrale d’un espace de travail ouvert, comme un dossier ouvert.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> crée un fournisseur par espace de travail instancié.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> crée un service par espace de travail instancié.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> doit être implémenté sur les fournisseurs et les services qui doivent exécuter du code asynchrone pendant la suppression.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> fournit des méthodes d’assistance pour accéder à des services connus ou à des services arbitraires.

## <a name="workspace-settings"></a>Paramètres de l’espace de travail

Les espaces de travail ont un <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> service avec un contrôle simple mais puissant sur un espace de travail. Pour une vue d’ensemble des paramètres, consultez [personnaliser les tâches de génération et de débogage](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Les paramètres de la plupart des `SettingsType` types sont des fichiers _. JSON_ , par exemple _VSWorkspaceSettings.jssur_ et _tasks.vs.jssur_.

La puissance des paramètres de l’espace de travail se concentre autour des « étendues », qui sont simplement des chemins d’accès dans l’espace de travail. Quand un consommateur appelle <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> , toutes les portées qui incluent le chemin d’accès et le type de paramètre demandés sont agrégées. La priorité d’agrégation d’étendue est la suivante :

1. « Paramètres locaux », qui est généralement le répertoire de la racine de l’espace de travail `.vs` .
1. Le chemin d’accès demandé lui-même.
1. Répertoire parent du chemin d’accès demandé.
1. Tous les autres répertoires parents jusqu’à la racine de l’espace de travail, y compris.
1. « Paramètres globaux », qui se trouve dans un répertoire utilisateur.

Le résultat est une instance de <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> . Cet objet contient les paramètres d’un type particulier et peut être interrogé pour définir des noms de clés stockés sous la forme `string` . Les méthodes <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> et les <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> méthodes d’extension s’attendent à ce que l’appelant sache le type de la valeur de paramètre demandée. Étant donné que la plupart des fichiers de paramètres sont persistants en tant que fichiers _. JSON_ , de nombreux appels utilisent `string` les tableaux,, `bool` `int` et de ces types. Les types d’objets sont également pris en charge. Dans ce cas, vous pouvez utiliser `IWorkspaceSettings` lui-même comme argument de type. Exemple :

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

En supposant que ces paramètres se trouvaient dans le _VSWorkspaceSettings.js_ d’un utilisateur, les données sont accessibles en tant que :

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
>Ces API de paramètres ne sont pas liées aux API disponibles dans l' `Microsoft.VisualStudio.Settings` espace de noms. Les paramètres de l’espace de travail sont agnostiques à l’hôte et utilisent des fichiers de paramètres spécifiques à l’espace de travail ou des fournisseurs de paramètres dynamiques.

### <a name="providing-dynamic-settings"></a>Fournir des paramètres dynamiques

Les extensions peuvent fournir des <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider> . Ces fournisseurs en mémoire autorisent les extensions à ajouter des paramètres ou à en remplacer d’autres.

L’exportation d’un `IWorkspaceSettingsProvider` est différente des autres fournisseurs d’espace de travail. La fabrique n’est pas `IWorkspaceProviderFactory` et il n’existe aucun type d’attribut spécial. Implémentez <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> et utilisez plutôt `[Export(typeof(IWorkspaceSettingsProviderFactory))]` .

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
>Lors de l’implémentation de méthodes qui retournent `IWorkspaceSettingsSource` (comme `IWorkspaceSettingsProvider.GetSingleSettings` ), retourner une instance de `IWorkspaceSettings` plutôt que `IWorkspaceSettingsSource` . `IWorkspaceSettings` fournit des informations supplémentaires qui peuvent être utiles pendant certaines agrégations de paramètres.

### <a name="settings-related-apis"></a>API associées aux paramètres

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> lit et agrège les paramètres de l’espace de travail.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> Obtient le `IWorkspaceSettingsManager` pour un espace de travail.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Obtient les paramètres d’une portée donnée agrégés sur toutes les étendues qui se chevauchent.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> contient les paramètres d’une étendue particulière.

## <a name="workspace-suggested-practices"></a>Pratiques suggérées de l’espace de travail

- Retourne des objets de `IWorkspaceProviderFactory.CreateProvider` ou des API similaires qui mémorisent leur `Workspace` contexte lors de leur création. Les interfaces des fournisseurs sont écrites pour s’attendre à ce que cet objet soit conservé lors de la création.
- Enregistrez les paramètres ou les caches spécifiques à l’espace de travail dans le chemin d’accès « paramètres locaux » de l’espace de travail. Créez un chemin d’accès pour votre fichier à l’aide `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` de dans Visual Studio 2017 version 15,6 ou ultérieure. Pour les versions antérieures à la version 15,6, utilisez l’extrait de code suivant :

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

## <a name="solution-events-and-package-auto-load"></a>Événements de solution et chargement automatique de packages

Les packages chargés peuvent implémenter `IVsSolutionEvents7` et appeler `IVsSolution.AdviseSolutionEvents` . Il comprend des événements lors de l’ouverture et de la fermeture d’un dossier dans Visual Studio.

Un contexte d’interface utilisateur peut être utilisé pour charger automatiquement votre package. La valeur est `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>Le package SourceExplorerPackage n’a pas été chargé correctement

L’extensibilité de l’espace de travail est fortement basée sur MEF, et les erreurs de composition entraînent l’échec du chargement du package qui héberge le dossier Open. Par exemple, si une extension exporte un type avec `ExportFileContextProviderAttribute` , mais que le type implémente uniquement `IWorkspaceProviderFactory<IFileContextActionProvider>` , une erreur se produit quand vous tentez d’ouvrir un dossier dans Visual Studio.

::: moniker range="vs-2017"

Les détails de l’erreur se trouvent dans _%localappdata%\microsoft\visualstudio\ 15.0_Id \componentmodelcache\microsoft.VisualStudio.default.err_. Résolvez les erreurs pour les types implémentés par votre extension.

::: moniker-end

::: moniker range=">=vs-2019"

Les détails de l’erreur se trouvent dans _%localappdata%\microsoft\visualstudio\ 16.0_Id \componentmodelcache\microsoft.VisualStudio.default.err_. Résolvez les erreurs pour les types implémentés par votre extension.

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

* [Contextes de fichier](workspace-file-contexts.md) -les fournisseurs de contexte de fichier apportent du code intelligence pour les espaces de travail de dossier ouverts.
* [Indexation](workspace-indexing.md) : l’indexation d’espace de travail collecte et conserve les informations relatives à l’espace de travail.
