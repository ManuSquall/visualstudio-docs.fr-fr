---
title: Informations de référence sur le schéma de fichier projet MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 824a6f562638edb04854431c437289f2741c46d9
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263090"
---
# <a name="msbuild-project-file-schema-reference"></a>Informations de référence sur le schéma de fichier projet MSBuild

Fournit un tableau de tous les éléments de schéma XML MSBuild avec leurs attributs et éléments enfants disponibles.

 MSBuild utilise des fichiers projet pour indiquer au moteur de génération ce qu’il faut générer et comment le générer. Les fichiers projet MSBuild sont des fichiers XML qui adhèrent au schéma XML MSBuild. Cette section documente le fichier de définition de schéma XML ( *. xsd*) pour MSBuild.

Le lien de schéma dans un fichier projet MSBuild n’est pas requis dans Visual Studio 2017 et versions ultérieures. S’il est présent, il doit être ` http://schemas.microsoft.com/developer/msbuild/2003` quelle que soit la version de Visual Studio.

## <a name="msbuild-xml-schema-elements"></a>Éléments de schéma XML MSBuild

 Le tableau suivant répertorie tous les éléments de schéma XML MSBuild, ainsi que leurs éléments enfants et leurs attributs.

|Élément|Éléments enfants|Attributs|
|-------------|--------------------|----------------|
|[Choose, élément (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> Lorsque le répertoire|--|
|[Import, élément (MSBuild)](../msbuild/import-element-msbuild.md)|--|Condition<br /><br /> Projet|
|[ImportGroup, élément](../msbuild/importgroup-element.md)|Importer|Condition|
|[Item, élément (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Condition<br /><br /> Exclure<br /><br /> Inclure<br /><br /> Supprimer|
|[ItemDefinitionGroup, élément (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Item*|Condition|
|[ItemGroup, élément (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Item*|Condition|
|[ItemMetadata, élément (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Item*|Condition|
|[OnError, élément (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Condition<br /><br /> ExecuteTargets|
|[Otherwise, élément (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[Output, élément (MSBuild)](../msbuild/output-element-msbuild.md)|--|Condition<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|
|[Parameter, élément](../msbuild/parameter-element.md)|--|Output<br /><br /> ParameterType<br /><br /> Obligatoire|
|[ParameterGroup, élément](../msbuild/parametergroup-element.md)|*Paramètre*|--|
|[Project, élément (MSBuild)](../msbuild/project-element-msbuild.md)|Choose<br /><br /> Importer<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Cible<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[ProjectExtensions, élément (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Property, élément (MSBuild)](../msbuild/property-element-msbuild.md)|--|Condition|
|[PropertyGroup, élément (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Propriété*|Condition|
|[Sdk, élément (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Name<br /><br /> Version|
|[Target, élément (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Tâche*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Condition<br /><br /> DependsOnTargets<br /><br /> Entrées<br /><br /> KeepDuplicateOutputs<br /><br /> Name<br /><br /> Outputs<br /><br /> Retours|
|[Élément Task de Target (MSBuild)](../msbuild/task-element-msbuild.md)|Output|Condition<br /><br /> ContinueOnError<br /><br /> *Paramètre*|
|[Élément Task de UsingTask (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Données*|Évaluer|
|[UsingTask, élément (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> Tâche|AssemblyFile<br /><br /> AssemblyName<br /><br /> Condition<br /><br /> TaskFactory<br /><br /> TaskName|
|[When, élément (MSBuild)](../msbuild/when-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|Condition|

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Conditions](../msbuild/msbuild-conditions.md)
- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
