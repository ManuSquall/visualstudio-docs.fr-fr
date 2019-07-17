---
title: Élément Project (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 132d1c3fbf23433ea89e7dba39bc226bc253b015
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205651"
---
# <a name="project-element-msbuild"></a>Project, élément (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Project InitialTargets="TargetA;TargetB"  
         DefaultTargets="TargetC;TargetD"  
         TreatAsLocalProperty="PropertyA;PropertyB"  
         ToolsVersion=<version number>  
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Choose>... </Choose>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Target>... </Target>  
    <UsingTask.../>  
    <ProjectExtensions>... </ProjectExtensions>  
    <Import... />  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|       Attribut        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `DefaultTargets`    |                                                                                                                                                                                                                                                                                                 Attribut facultatif.<br /><br /> Cible ou cibles par défaut définies comme point d’entrée de la génération si aucune cible n’a été spécifiée. Plusieurs cibles sont séparées par un point-virgule (;).<br /><br /> Si aucune cible par défaut n’est spécifiée dans l’attribut `DefaultTargets` ou la ligne de commande [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], le moteur exécute la première cible dans le fichier projet après l’évaluation des éléments [Import](../msbuild/import-element-msbuild.md).                                                                                                                                                                                                                                                                                                  |
|    `InitialTargets`    |                                                                                                                                                                                                                                                                                                                                                                                                                                             Attribut facultatif.<br /><br /> Cible ou cibles initiales à exécuter avant les cibles spécifiées dans l’attribut `DefaultTargets` ou sur la ligne de commande. Plusieurs cibles sont séparées par un point-virgule (;).                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|     `ToolsVersion`     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Attribut facultatif.<br /><br /> Version de l’ensemble d’outils que MSBuild utilise pour déterminer les valeurs de $ (MSBuildBinPath) et $(MSBuildToolsPath).                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `TreatAsLocalProperty` | Attribut facultatif.<br /><br /> Noms des propriétés qui ne sont pas considérées comme étant globales. Cet attribut empêche des propriétés de ligne de commande particulières de remplacer les valeurs de propriété définies dans un fichier projet ou de cibles et dans toutes les importations ultérieures. Plusieurs propriétés sont séparées par un point-virgule (;).<br /><br /> Normalement, les propriétés globales remplacent les valeurs de propriété qui sont définies dans le fichier projet ou de cible. Si la propriété est indiquée dans la valeur `TreatAsLocalProperty`, la valeur de propriété globale ne remplace pas les valeurs de propriété qui sont définies dans ce fichier et dans toutes les importations ultérieures. Pour plus d'informations, voir [Procédure : Générer les mêmes fichiers sources avec des Options différentes](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Remarque :**  Vous définissez des propriétés globales à l’invite de commande à l’aide de la **cette propriété** (ou **/p**) basculer. Vous pouvez également définir ou modifier des propriétés globales pour des projets enfants d’une génération multiprojet à l’aide de l’attribut `Properties` de la tâche MSBuild. Pour plus d’informations, consultez l’article [Tâche MSBuild](../msbuild/msbuild-task.md). |
|        `Xmlns`         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Attribut requis.<br /><br /> Le `xmlns` attribut doit avoir la valeur de «<http://schemas.microsoft.com/developer/msbuild/2003>».                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Élément facultatif.<br /><br /> Évalue des éléments enfants pour sélectionner un ensemble d’éléments `ItemGroup` et/ou d’éléments `PropertyGroup` à évaluer.|  
|[Importationation](../msbuild/import-element-msbuild.md)|Élément facultatif.<br /><br /> Permet à un fichier projet d’importer un autre fichier projet. Un projet peut ne contenir aucun élément `Import` ou en contenir plusieurs.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Élément facultatif.<br /><br /> Élément grouping d’éléments individuels. Les éléments sont spécifiés à l’aide de l’élément [Item](../msbuild/item-element-msbuild.md). Un projet peut ne contenir aucun élément `ItemGroup` ou en contenir plusieurs.|  
|[ProjectExtensions](../msbuild/projectextensions-element-msbuild.md)|Élément facultatif.<br /><br /> Permet de conserver des informations autres que [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] dans un fichier projet [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Un projet peut ne contenir aucun élément `ProjectExtensions` ou en contenir un.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Élément facultatif.<br /><br /> Élément grouping de propriétés individuelles. Les propriétés sont spécifiées à l’aide de l’élément [Property](../msbuild/property-element-msbuild.md). Un projet peut ne contenir aucun élément `PropertyGroup` ou en contenir plusieurs.|  
|[Target](../msbuild/target-element-msbuild.md)|Élément facultatif.<br /><br /> Contient un ensemble de tâches que [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] doit exécuter séquentiellement. Les tâches sont spécifiées à l’aide de l’élément [Task](../msbuild/task-element-msbuild.md). Un projet peut ne contenir aucun élément `Target` ou en contenir plusieurs.|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Élément facultatif.<br /><br /> Permet d’inscrire des tâches dans [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Un projet peut ne contenir aucun élément `UsingTask` ou en contenir plusieurs.|  
  
### <a name="parent-elements"></a>Éléments parents  
 Aucune.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Spécifier la cible à générer en premier](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [Command-Line Reference (Informations de référence sur la ligne de commande MSBuild)](../msbuild/msbuild-command-line-reference.md)   
 [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](msbuild.md)
