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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263090"
---
# <a name="msbuild-project-file-schema-reference"></a>Informations de référence sur le schéma de fichier projet MSBuild

Fournit un tableau de tous les éléments MSBuild XML Schema avec leurs attributs disponibles et les éléments pour enfants.

 MSBuild utilise des fichiers de projet pour indiquer au moteur de construction ce qu’il faut construire et comment le construire. Les fichiers de projet MSBuild sont des fichiers XML qui adhèrent au schéma MSBuild XML. Cette section documente le fichier de définition du schéma XML (*.xsd)* pour MSBuild.

Le lien de schéma dans un fichier de projet MSBuild n’est pas requis dans Visual Studio 2017 et plus tard. Si c’est ` http://schemas.microsoft.com/developer/msbuild/2003` présent, il devrait être indépendamment de la version de Visual Studio.

## <a name="msbuild-xml-schema-elements"></a>Éléments de schéma XML MSBuild

 Le tableau suivant répertorie tous les éléments du schéma MSBuild XML ainsi que leurs éléments et attributs pour enfants.

|Élément|Éléments enfants|Attributs|
|-------------|--------------------|----------------|
|[Choisissez l’élément (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> Lorsque le répertoire|--|
|[Import, élément (MSBuild)](../msbuild/import-element-msbuild.md)|--|Condition<br /><br /> Projet|
|[Élément ImportGroup](../msbuild/importgroup-element.md)|Importer|Condition|
|[Item, élément (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Condition<br /><br /> Exclure<br /><br /> Inclure<br /><br /> Supprimer|
|[Élément ItemDefinitionGroup (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Article*|Condition|
|[ItemGroup, élément (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Article*|Condition|
|[ItemMetadata, élément (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Article*|Condition|
|[Élément OnError (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Condition<br /><br /> ExecuteTargets|
|[Otherwise, élément (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[Élément de sortie (MSBuild)](../msbuild/output-element-msbuild.md)|--|Condition<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|
|[élément Parameter](../msbuild/parameter-element.md)|--|Output<br /><br /> ParameterType<br /><br /> Obligatoire|
|[Élément Paramètregroupe](../msbuild/parametergroup-element.md)|*Paramètre*|--|
|[Élément du projet (MSBuild)](../msbuild/project-element-msbuild.md)|Choose<br /><br /> Importer<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Cible<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[ProjectExtensions élément (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Élément de propriété (MSBuild)](../msbuild/property-element-msbuild.md)|--|Condition|
|[Élément PropertyGroup (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Propriété*|Condition|
|[Élément Sdk (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Nom<br /><br /> Version|
|[Target, élément (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Tâche*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Condition<br /><br /> DependsOnTargets<br /><br /> Entrées<br /><br /> KeepDuplicateOutputs<br /><br /> Nom<br /><br /> Outputs<br /><br /> Retours|
|[Élément de tâche de la cible (MSBuild)](../msbuild/task-element-msbuild.md)|Output|Condition<br /><br /> ContinueOnError<br /><br /> *Paramètre*|
|[Élément de tâche de UsingTask (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Niveau*|Évaluer|
|[Utilisation de l’élément Desk (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> Tâche|AssemblyFile<br /><br /> AssemblyName<br /><br /> Condition<br /><br /> TaskFactory<br /><br /> TaskName|
|[Lorsque l’élément (MSBuild)](../msbuild/when-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|Condition|

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Conditions](../msbuild/msbuild-conditions.md)
- [Référence MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
