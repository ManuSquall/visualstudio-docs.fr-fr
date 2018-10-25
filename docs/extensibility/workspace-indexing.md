---
title: Espace de travail d’indexation dans Visual Studio | Microsoft Docs
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
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939148"
---
# <a name="workspace-indexing"></a>Espace de travail d’indexation

Dans une solution, les systèmes de projet sont responsables de fournir des fonctionnalités de génération, de déboguer, **GoTo** recherche de symbole et bien plus encore. Systèmes de projet peuvent effectuer cette tâche, car ils comprennent la relation et les fonctionnalités des fichiers dans un projet. Un [ouvrir le dossier](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) l’information même fournir également des fonctionnalités IDE riches a besoin d’espace de travail. La collecte et le stockage persistant de ces données est un processus appelé espace de travail d’indexation. Ces données indexées peuvent être interrogées via un ensemble d’API asynchrones. Extendeurs peuvent participer au processus d’indexation en fournissant <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>s qui savent comment gérer certains types de fichiers.

## <a name="types-of-indexed-data"></a>Types de données indexées

Il existe trois types de données qui sont indexées. Notez que le type attendu à partir des analyseurs de fichiers est différent du type désérialisé à partir de l’index.

|Données|Type d’analyseur de fichier|Type de résultat de requête index|Types associés|
|--|--|--|--|
|Références|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Symbols|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> doit être utilisé au lieu de `IIndexWorkspaceService` pour les requêtes|
|Valeurs de données|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Interrogation des données indexées

Il existe deux types asynchrones disponibles pour accéder aux données persistantes. La première consiste à utiliser <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>. Il fournit un accès de base dans un fichier unique `FileReferenceResult` et `FileDataResult` les données et met en cache les résultats. Le second est le <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> qui n’utilise pas la mise en cache, mais permet plusieurs fonctionnalités d’interrogation.

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

## <a name="participating-in-indexing"></a>Participant à l’indexation

Espace de travail d’indexation suit à peu près de la séquence suivante :

1. Découverte et la persistance des entités de système de fichiers dans l’espace de travail (et uniquement sur l’analyse de l’ouverture initiale).
1. Par fichier, le fournisseur de correspondance avec la priorité la plus élevée est invité à rechercher les `FileReferenceInfo`s.
1. Par fichier, le fournisseur de correspondance avec la priorité la plus élevée est invité à rechercher les `SymbolDefinition`s.
1. Par fichier, tous les fournisseurs êtes invité à entrer `FileDataValue`s.

Extensions peuvent exporter un scanneur en implémentant `IWorkspaceProviderFactory<IFileScanner>` et l’exportation avec le type de <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>. Le `SupportedTypes` argument d’attribut doit être une ou plusieurs valeurs à partir de <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>. Pour un analyseur d’exemple, consultez le kit SDK VS [exemple](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs).

> [!WARNING]
> Ne pas exporter un scanneur de fichier qui prend en charge la `FileScannerTypeConstants.FileScannerContentType` type. Il est utilisé pour Microsoft internes, uniquement.

Des situations avancées, une extension peut dynamiquement prend en charge un ensemble arbitraire de types de fichiers. Au lieu de l’exportation MEF `IWorkspaceProviderFactory<IFileScanner>`, une extension peut exporter `IWorkspaceProviderFactory<IFileScannerProvider>`. Lors de l’indexation commence, ce type de fabrique sera importé, instancié et avoir son <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> méthode appelée. `IFileScanner` prise en charge de n’importe quelle valeur à partir des instances `FileScannerTpeConstants` sera pris en compte, pas seulement les symboles.

## <a name="next-steps"></a>Étapes suivantes

* [Espaces de travail et les services de langage](workspace-language-services.md) -Apprenez à intégrer des services de langage dans un espace de travail d’ouvrir le dossier.
* [Génération de l’espace de travail](workspace-build.md) -prend en charge d’ouvrir le dossier créer des systèmes tels que MSBuild et makefiles.