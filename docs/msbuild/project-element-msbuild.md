---
title: Élément Project (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb3acd9add6f19ec258f808fd55a955eac14b6e5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831735"
---
# <a name="project-element-msbuild"></a>Élément Project (MSBuild)
Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .  

## <a name="syntax"></a>Syntaxe  

```xml  
<Project InitialTargets="TargetA;TargetB"  
         DefaultTargets="TargetC;TargetD"  
         TreatAsLocalProperty="PropertyA;PropertyB"  
         ToolsVersion=<version number>
         Sdk="name[/version]"
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Sdk... />
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

| Attribut | Description |
|------------------------| - |
| `DefaultTargets` | Attribut facultatif.<br /><br /> Cible ou cibles par défaut définies comme point d’entrée de la génération si aucune cible n’a été spécifiée. Plusieurs cibles sont séparées par un point-virgule (;).<br /><br /> Si aucune cible par défaut n’est spécifiée dans l’attribut `DefaultTargets` ou la ligne de commande [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], le moteur exécute la première cible dans le fichier projet après l’évaluation des éléments [Import](../msbuild/import-element-msbuild.md). |
| `InitialTargets` | Attribut facultatif.<br /><br /> Cible ou cibles initiales à exécuter avant les cibles spécifiées dans l’attribut `DefaultTargets` ou sur la ligne de commande. Plusieurs cibles sont séparées par un point-virgule (;). |
| `Sdk` | Attribut facultatif. <br /><br /> Le nom et la version facultative du kit SDK à utiliser pour créer des instructions d’importation implicites qui sont ajoutées au fichier .proj. Si aucune version n’est spécifiée, MSBuild tente de résoudre une version par défaut.  Par exemple, `<Project Sdk="Microsoft.NET.Sdk" />` ou `<Project Sdk="My.Custom.Sdk/1.0.0" />`. |
| `ToolsVersion` | Attribut facultatif.<br /><br /> Version de l’ensemble d’outils utilisée par MSBuild pour déterminer les valeurs de $(MSBuildBinPath) et de $(MSBuildToolsPath). |
| `TreatAsLocalProperty` | Attribut facultatif.<br /><br /> Noms des propriétés qui ne sont pas considérées comme étant globales. Cet attribut empêche des propriétés de ligne de commande particulières de remplacer les valeurs de propriété définies dans un fichier projet ou de cibles et dans toutes les importations ultérieures. Plusieurs propriétés sont séparées par un point-virgule (;).<br /><br /> Normalement, les propriétés globales remplacent les valeurs de propriété qui sont définies dans le fichier projet ou de cible. Si la propriété est indiquée dans la valeur `TreatAsLocalProperty`, la valeur de propriété globale ne remplace pas les valeurs de propriété qui sont définies dans ce fichier et dans toutes les importations ultérieures. Pour plus d’informations, voir [Guide pratique : Générer les mêmes fichiers sources avec des options différentes](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Remarque :** vous définissez les propriétés générales avec une invite de commande à l’aide du commutateur **-property** (ou **-p**). Vous pouvez également définir ou modifier des propriétés globales pour des projets enfants d’une génération multiprojet à l’aide de l’attribut `Properties` de la tâche MSBuild. Pour plus d’informations, consultez l’article [Tâche MSBuild](../msbuild/msbuild-task.md). |
| `Xmlns` | Attribut facultatif.<br /><br /> Quand il est spécifié, l’attribut `xmlns` doit avoir la valeur `http://schemas.microsoft.com/developer/msbuild/2003`. |

### <a name="child-elements"></a>Éléments enfants  

| Élément | Description |
| - | - |
| [Choose](../msbuild/choose-element-msbuild.md) | Élément facultatif.<br /><br /> Évalue des éléments enfants pour sélectionner un ensemble d’éléments `ItemGroup` et/ou d’éléments `PropertyGroup` à évaluer. |
| [Import](../msbuild/import-element-msbuild.md) | Élément facultatif.<br /><br /> Permet à un fichier projet d’importer un autre fichier projet. Un projet peut ne contenir aucun élément `Import` ou en contenir plusieurs. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Élément facultatif.<br /><br /> Élément grouping d’éléments individuels. Les éléments sont spécifiés à l’aide de l’élément [Item](../msbuild/item-element-msbuild.md). Un projet peut ne contenir aucun élément `ItemGroup` ou en contenir plusieurs. |
| [ProjectExtensions](../msbuild/projectextensions-element-msbuild.md) | Élément facultatif.<br /><br /> Permet de conserver des informations autres que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dans un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Un projet peut ne contenir aucun élément `ProjectExtensions` ou en contenir un. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Élément facultatif.<br /><br /> Élément grouping de propriétés individuelles. Les propriétés sont spécifiées à l’aide de l’élément [Property](../msbuild/property-element-msbuild.md). Un projet peut ne contenir aucun élément `PropertyGroup` ou en contenir plusieurs. |
| [Sdk](../msbuild/sdk-element-msbuild.md) | Élément facultatif.<br /><br /> Référence un kit SDK de projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Cet élément peut être utilisé comme alternative à l’attribut Sdk. |
| [Target](../msbuild/target-element-msbuild.md) | Élément facultatif.<br /><br /> Contient un ensemble de tâches que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] doit exécuter séquentiellement. Les tâches sont spécifiées à l’aide de l’élément [Task](../msbuild/task-element-msbuild.md). Un projet peut ne contenir aucun élément `Target` ou en contenir plusieurs. |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Élément facultatif.<br /><br /> Permet d’inscrire des tâches dans [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Un projet peut ne contenir aucun élément `UsingTask` ou en contenir plusieurs. |

### <a name="parent-elements"></a>Éléments parents  
 Aucun.  

## <a name="see-also"></a>Voir aussi  
 [Guide pratique : Spécifier la cible à générer en premier](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [Informations de référence sur la ligne de commande](../msbuild/msbuild-command-line-reference.md)   
 [Informations de référence sur le schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)
