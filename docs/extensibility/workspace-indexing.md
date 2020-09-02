---
title: Indexation de l’espace de travail dans Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 9bf7df777d27003fa5763debc772a8804ec28ef5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952700"
---
# <a name="workspace-indexing"></a>Indexation de l’espace de travail

Dans une solution, les systèmes de projet sont chargés de fournir des fonctionnalités pour la génération, le débogage, la recherche de symboles **goto** , et bien plus encore. Les systèmes de projet peuvent effectuer ce travail, car ils comprennent la relation et les fonctionnalités des fichiers dans un projet. Un espace de travail de [dossier ouvert](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) a besoin du même Aperçu pour fournir également des fonctionnalités d’IDE riches. La collecte et le stockage permanent de ces données sont un processus appelé indexation de l’espace de travail. Ces données indexées peuvent être interrogées à l’aide d’un ensemble d’API asynchrones. Les extendeurs peuvent participer au processus d’indexation en fournissant des <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner> s qui savent gérer certains types de fichiers.

## <a name="types-of-indexed-data"></a>Types de données indexées

Il existe trois types de données indexées. Notez que le type attendu des analyseurs de fichier diffère du type désérialisé de l’index.

|Données|Type d’analyse de fichier|Type de résultat de la requête d’index|Types associés|
|--|--|--|--|
|Références|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|symboles|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> doit être utilisé à la place de `IIndexWorkspaceService` pour les requêtes|
|Valeurs de données|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Interrogation de données indexées

Deux types asynchrones sont disponibles pour accéder aux données persistantes. La première consiste à <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData> . Il fournit un accès de base aux données et à un seul fichier `FileReferenceResult` `FileDataResult` , et met en cache les résultats. Le second est le <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> qui n’utilise pas la mise en cache, mais autorise davantage de fonctionnalités d’interrogation.

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Indexing;

private static IIndexWorkspaceData GetCachedIndexedData(IWorkspace workspace)
{
    // Gets access to indexed data wrapped in a cache.
    return workspace?.GetIndexWorkspaceDataService()?.CreateIndexWorkspaceData();
}

private static IIndexWorkspaceService GetDirectIndexedData(IWorkspace workspace)
{
    // Gets direct access to indexed data.
    // Can also be casted to IIndexWorkspaceService2.
    return workspace?.GetIndexWorkspaceService();
}
```

## <a name="participating-in-indexing"></a>Participation à l’indexation

L’indexation de l’espace de travail suit à peu près la séquence suivante :

1. Détection et persistance des entités du système de fichiers dans l’espace de travail (uniquement lors de l’analyse d’ouverture initiale).
1. Par fichier, le fournisseur correspondant avec la priorité la plus élevée est invité à rechercher les `FileReferenceInfo` .
1. Par fichier, le fournisseur correspondant avec la priorité la plus élevée est invité à rechercher les `SymbolDefinition` .
1. Par fichier, tous les fournisseurs sont invités à obtenir des `FileDataValue` .

Les extensions peuvent exporter un scanneur en implémentant `IWorkspaceProviderFactory<IFileScanner>` et en exportant le type avec <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute> . L' `SupportedTypes` argument d’attribut doit être une ou plusieurs valeurs de <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants> . Pour obtenir un exemple de scanneur, consultez l' [exemple](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs)du kit de développement Visual Studio.

> [!WARNING]
> N’exportez pas un scanneur de fichiers qui prend en charge le `FileScannerTypeConstants.FileScannerContentType` type. Il est utilisé uniquement à des fins internes Microsoft.

Dans les situations avancées, une extension peut prendre en charge de manière dynamique un ensemble arbitraire de types de fichiers. Au lieu d’exporter MEF `IWorkspaceProviderFactory<IFileScanner>` , une extension peut être exportée `IWorkspaceProviderFactory<IFileScannerProvider>` . Lorsque l’indexation commence, ce type de fabrique est importé, instancié et sa <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> méthode est appelée. `IFileScanner` les instances prenant en charge toute valeur de `FileScannerTpeConstants` sont honorées, pas seulement les symboles.

## <a name="next-steps"></a>Étapes suivantes

* [Espaces de travail et services de langage](workspace-language-services.md) : Découvrez comment intégrer les services de langage dans un espace de travail de dossier ouvert.
* [Espace de travail génération](workspace-build.md) : le dossier ouvert prend en charge les systèmes de génération tels que MSBuild et makefiles.