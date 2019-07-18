---
title: Informations de référence sur le schéma de fichier projet MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 847fa53acad63cec151222521ed8f85090c52080
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158855"
---
# <a name="msbuild-project-file-schema-reference"></a>Référence du schéma de fichier de projet MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fournit un tableau de tous les éléments de schéma XML [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] avec leurs éléments enfants et attributs disponibles.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] utilise des fichiers projet pour indiquer au moteur de génération ce qu’il convient de générer et comment procéder. Les fichiers projet [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] sont des fichiers XML qui respectent le schéma XML [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Cette section documente le fichier de définition de schéma XML (.xsd) pour [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
## <a name="msbuild-xml-schema-elements"></a>Éléments de schéma XML MSBuild  
 Le tableau suivant répertorie tous les éléments de schéma XML [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], ainsi que leurs éléments enfants et leurs attributs.  
  
|Élément|Éléments enfants|Attributs|  
|-------------|--------------------|----------------|  
|[Choose, élément (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> When|--|  
|[Import, élément (MSBuild)](../msbuild/import-element-msbuild.md)|--|Condition<br /><br /> Projet|  
|[ImportGroup, élément](../msbuild/importgroup-element.md)|Import|Condition|  
|[Item, élément (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Condition<br /><br /> Exclure<br /><br /> Inclure<br /><br /> Remove|  
|[ItemDefinitionGroup, élément (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Item*|Condition|  
|[ItemGroup, élément (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Item*|Condition|  
|[ItemMetadata, élément (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Item*|Condition|  
|[OnError, élément (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Condition<br /><br /> ExecuteTargets|  
|[Otherwise, élément (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Choisir<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|  
|[Output, élément (MSBuild)](../msbuild/output-element-msbuild.md)|--|Condition<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|  
|[Parameter, élément](../msbuild/parameter-element.md)|--|Sortie<br /><br /> ParameterType<br /><br /> Obligatoire|  
|[ParameterGroup, élément](../msbuild/parametergroup-element.md)|*Paramètre*|--|  
|[Project, élément (MSBuild)](../msbuild/project-element-msbuild.md)|Choisir<br /><br /> Import<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> une cible<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|  
|[ProjectExtensions, élément (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|  
|[Property, élément (MSBuild)](../msbuild/property-element-msbuild.md)|--|Condition|  
|[PropertyGroup, élément (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Property*|Condition|  
|[Target, élément (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Task*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Condition<br /><br /> DependsOnTargets<br /><br /> Inputs (Entrées)<br /><br /> KeepDuplicateOutputs<br /><br /> Name<br /><br /> Sorties<br /><br /> Returns (Retours)|  
|[Task, élément (MSBuild)](../msbuild/task-element-msbuild.md)|Sortie|Condition<br /><br /> ContinueOnError<br /><br /> *Paramètre*|  
|[TaskBody, élément (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Données*|Évaluer|  
|[UsingTask, élément (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> TaskBody|AssemblyFile<br /><br /> AssemblyName<br /><br /> Condition<br /><br /> TaskFactory<br /><br /> TaskName|  
|[When, élément (MSBuild)](../msbuild/when-element-msbuild.md)|Choisir<br /><br /> ItemGroup<br /><br /> PropertyGroup|Condition|  
  
## <a name="see-also"></a>Voir aussi  
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)   
 [Conditions MSBuild](../msbuild/msbuild-conditions.md)   
 [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](msbuild.md)
