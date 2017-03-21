---
title: "Élément Project (MSBuild) | Microsoft Docs"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 31
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 203e1e27cc892e96b103fc6cb22a73672a8e16af
ms.openlocfilehash: 224371f6915258a9860c5f05554445f6b1ae106c
ms.lasthandoff: 03/01/2017

---
# <a name="project-element-msbuild"></a>Project, élément (MSBuild)
Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  

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

|Attribut|Description|  
|---------------|-----------------|  
|`DefaultTargets`|Attribut facultatif.<br /><br /> Cible ou cibles par défaut définies comme point d’entrée de la génération si aucune cible n’a été spécifiée. Plusieurs cibles sont séparées par un point-virgule (;).<br /><br /> Si aucune cible par défaut n’est spécifiée dans l’attribut `DefaultTargets` ou la ligne de commande [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], le moteur exécute la première cible dans le fichier projet après l’évaluation des éléments [Import](../msbuild/import-element-msbuild.md).|  
|`InitialTargets`|Attribut facultatif.<br /><br /> Cible ou cibles initiales à exécuter avant les cibles spécifiées dans l’attribut `DefaultTargets` ou sur la ligne de commande. Plusieurs cibles sont séparées par un point-virgule (;).|  
|`SDK`|Attribut facultatif. (Disponible uniquement pour les projets .NET Core dans Visual Studio versions 2017 ou ultérieures).<br /><br /> Version du SDK à utiliser pour créer des instructions d’importation implicites qui sont ajoutées au fichier .proj. Par exemple, `<Project Sdk="Microsoft.NET.Sdk/1.0.0-RC" />`.|  
|`ToolsVersion`|Attribut facultatif.<br /><br /> Version de l’ensemble d’outils que MSBuild utilise pour déterminer les valeurs de $ (MSBuildBinPath) et $(MSBuildToolsPath).|  
|`TreatAsLocalProperty`|Attribut facultatif.<br /><br /> Noms des propriétés qui ne sont pas considérées comme étant globales. Cet attribut empêche des propriétés de ligne de commande particulières de remplacer les valeurs de propriété définies dans un fichier projet ou de cibles et dans toutes les importations ultérieures. Plusieurs propriétés sont séparées par un point-virgule (;).<br /><br /> Normalement, les propriétés globales remplacent les valeurs de propriété qui sont définies dans le fichier projet ou de cible. Si la propriété est indiquée dans la valeur `TreatAsLocalProperty`, la valeur de propriété globale ne remplace pas les valeurs de propriété qui sont définies dans ce fichier et dans toutes les importations ultérieures. Pour plus d’informations, consultez l’article [Comment : générer les mêmes fichiers sources avec des options différentes](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Remarque :** vous définissez des propriétés globales dans une invite de commande à l’aide du commutateur **/property** (or **/p**). Vous pouvez également définir ou modifier des propriétés globales pour des projets enfants d’une génération multiprojet à l’aide de l’attribut `Properties` de la tâche MSBuild. Pour plus d’informations, consultez l’article [Tâche MSBuild](../msbuild/msbuild-task.md).|  
|`Xmlns`|Attribut facultatif.<br /><br /> Quand il est spécifié, l’attribut `xmlns` doit avoir la valeur « http://schemas.microsoft.com/developer/msbuild/2003 ».|  

### <a name="child-elements"></a>Éléments enfants  

|Élément|Description|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Élément facultatif.<br /><br /> Évalue des éléments enfants pour sélectionner un ensemble d’éléments `ItemGroup` et/ou d’éléments `PropertyGroup` à évaluer.|  
|[Import](../msbuild/import-element-msbuild.md)|Élément facultatif.<br /><br /> Permet à un fichier projet d’importer un autre fichier projet. Un projet peut ne contenir aucun élément `Import` ou en contenir plusieurs.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Élément facultatif.<br /><br /> Élément grouping d’éléments individuels. Les éléments sont spécifiés à l’aide de l’élément [Item](../msbuild/item-element-msbuild.md). Un projet peut ne contenir aucun élément `ItemGroup` ou en contenir plusieurs.|  
|[ProjectExtensions](../msbuild/projectextensions-element-msbuild.md)|Élément facultatif.<br /><br /> Permet de conserver des informations autres que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dans un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Un projet peut ne contenir aucun élément `ProjectExtensions` ou en contenir un.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Élément facultatif.<br /><br /> Élément grouping de propriétés individuelles. Les propriétés sont spécifiées à l’aide de l’élément [Property](../msbuild/property-element-msbuild.md). Un projet peut ne contenir aucun élément `PropertyGroup` ou en contenir plusieurs.|  
|[Target](../msbuild/target-element-msbuild.md)|Élément facultatif.<br /><br /> Contient un ensemble de tâches que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] doit exécuter séquentiellement. Les tâches sont spécifiées à l’aide de l’élément [Task](../msbuild/task-element-msbuild.md). Un projet peut ne contenir aucun élément `Target` ou en contenir plusieurs.|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Élément facultatif.<br /><br /> Permet d’inscrire des tâches dans [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Un projet peut ne contenir aucun élément `UsingTask` ou en contenir plusieurs.|  

### <a name="parent-elements"></a>Éléments parents  
 Aucun.  

## <a name="see-also"></a>Voir aussi  
 [Comment : spécifier la cible à générer en premier](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [Command-Line Reference (Informations de référence sur la ligne de commande MSBuild)](../msbuild/msbuild-command-line-reference.md)   
 [Informations de référence sur le schéma de fichier projet MSBuild](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)

