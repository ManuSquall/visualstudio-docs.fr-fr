---
title: Espace de travail de l’indexation dans Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3163e98c-1c79-48a7-813f-7923be894ba1
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 5004db0d895d1fdc697c18606c346c24cd484527
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="workspace-indexing"></a>Indexation de l’espace de travail

Dans une solution, systèmes de projet sont chargés de fournir des fonctionnalités pour générer, déboguer, **GoTo** recherche de symbole et bien plus encore. Systèmes de projet peuvent effectuer cette tâche, car ils comprennent la relation et les fonctionnalités de fichiers au sein d’un projet. Un [ouvrir le dossier](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) l’information même pour fournir des fonctionnalités IDE riches ainsi a besoin d’espace de travail. La collecte et le stockage persistant de ces données est un processus appelé l’indexation de l’espace de travail. Ces données indexées peuvent être interrogées via un ensemble d’API asynchrones. Extendeurs peuvent participer au processus d’indexation en fournissant <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>qui sait comment gérer certains types de fichiers.

## <a name="types-of-indexed-data"></a>Types de données indexées

Il existe trois types de données qui sont indexées. Notez que le type attendu par les analyseurs de fichiers est différent du type désérialisé à partir de l’index.

|Données|Type d’analyseur de fichier|Type de résultat de requête index|Types associés|
|--|--|--|--|
|Références|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Symboles|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> doit être utilisé à la place de `IIndexWorkspaceService` pour les requêtes|
|Valeurs de données|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Interrogation des données indexées

Il existe deux types asynchrones permettent d’accéder aux données persistantes. La première consiste à <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>. Il fournit un accès de base dans un fichier d’unique `FileReferenceResult` et `FileDataResult` les données et met en cache les résultats. Le deuxième est le <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> qui n’utilise pas la mise en cache, mais permet plusieurs fonctionnalités d’interrogation.

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

## <a name="participating-in-indexing"></a>Participe à l’indexation

Indexation de l’espace de travail suit à peu près de la séquence suivante :

1. La découverte et la persistance des entités de système de fichiers dans l’espace de travail (uniquement sur l’analyse d’ouverture initiale).
1. Par fichier, le fournisseur de correspondance avec la priorité la plus élevée est invité à analyser pour `FileReferenceInfo`s.
1. Par fichier, le fournisseur de correspondance avec la priorité la plus élevée est invité à analyser pour `SymbolDefinition`s.
1. Par fichier, tous les fournisseurs sont demandées `FileDataValue`s.

Extensions peuvent exporter un scanneur en implémentant `IWorkspaceProviderFactory<IFileScanner>` et de l’exportation du type avec <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>. Le `SupportedTypes` argument d’attribut doit être une ou plusieurs valeurs à partir de <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>. Pour un analyseur d’exemple, consultez le kit SDK VS [exemple](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs).

> [!WARNING]
> Ne pas exporter un analyseur de fichiers qui prend en charge la `FileScannerTypeConstants.FileScannerContentType` type. Il est utilisé pour Microsoft internes, uniquement.

Dans des situations avancées, une extension peut prendre en charge dynamiquement un ensemble arbitraire de types de fichiers. Plutôt que d’exporter de MEF `IWorkspaceProviderFactory<IFileScanner>`, une extension peut exporter `IWorkspaceProviderFactory<IFileScannerProvider>`. Lorsque l’indexation commence, ce type de fabrique sera importé, instancié et des ses <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> méthode appelée. `IFileScanner` prise en charge d’une valeur comprise entre des instances `FileScannerTpeConstants` sera pris en compte, pas seulement des symboles.

## <a name="next-steps"></a>Étapes suivantes

* [Espaces de travail et les services de langage](workspace-language-services.md) -Apprenez à intégrer des services de langage dans un espace de travail d’ouvrir le dossier.
* [Génération de l’espace de travail](workspace-build.md) -prend en charge d’ouvrir le dossier créer des systèmes tels que MSBuild et les makefiles.