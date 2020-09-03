---
title: Élément Project (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df9eff3e941cc21aaa71c2779a72084e12e8e590
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632977"
---
# <a name="project-element-msbuild"></a>Élément Project (MSBuild)

Élément racine requis d’un fichier projet MSBuild.

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
| `DefaultTargets` | Attribut facultatif.<br /><br /> Cible ou cibles par défaut définies comme point d’entrée de la génération si aucune cible n’a été spécifiée. Plusieurs cibles sont séparées par un point-virgule (;).<br /><br /> Si aucune cible par défaut n’est spécifiée dans l' `DefaultTargets` attribut ou la ligne de commande MSBuild, le moteur exécute la première cible dans le fichier projet une fois que les éléments d' [importation](../msbuild/import-element-msbuild.md) ont été évalués. |
| `InitialTargets` | Attribut facultatif.<br /><br /> Cible ou cibles initiales à exécuter avant les cibles spécifiées dans l’attribut `DefaultTargets` ou sur la ligne de commande. Plusieurs cibles sont séparées par un point-virgule (`;`). Si plusieurs fichiers importés définissent `InitialTargets`, toutes les cibles indiquées seront exécutées, dans l’ordre où elles sont trouvées. |
| `Sdk` | Attribut facultatif. <br /><br /> Le nom et la version facultative du kit SDK à utiliser pour créer des instructions d’importation implicites qui sont ajoutées au fichier .proj. Si aucune version n’est spécifiée, MSBuild tente de résoudre une version par défaut.   Par exemple, `<Project Sdk="Microsoft.NET.Sdk" />` ou `<Project Sdk="My.Custom.Sdk/1.0.0" />`. |
| `ToolsVersion` | Attribut facultatif.<br /><br /> Version de l’ensemble d’outils utilisée par MSBuild pour déterminer les valeurs de $(MSBuildBinPath) et de $(MSBuildToolsPath). |
| `TreatAsLocalProperty` | Attribut facultatif.<br /><br /> Noms des propriétés qui ne sont pas considérées comme étant globales. Cet attribut empêche des propriétés de ligne de commande particulières de remplacer les valeurs de propriété définies dans un fichier projet ou de cibles et dans toutes les importations ultérieures. Plusieurs propriétés sont séparées par un point-virgule (;).<br /><br /> Normalement, les propriétés globales remplacent les valeurs de propriété qui sont définies dans le fichier projet ou de cible. Si la propriété est indiquée dans la valeur `TreatAsLocalProperty`, la valeur de propriété globale ne remplace pas les valeurs de propriété qui sont définies dans ce fichier et dans toutes les importations ultérieures. Pour plus d’informations, voir [Guide pratique : Générer les mêmes fichiers sources avec des options différentes](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Remarque :**  Vous définissez les propriétés globales à partir d’une invite de commandes à l’aide du commutateur **-Property** (ou **-p**). Vous pouvez également définir ou modifier des propriétés globales pour des projets enfants d’une génération multiprojet à l’aide de l’attribut `Properties` de la tâche MSBuild. Pour plus d’informations, consultez [MSBuild, tâche](../msbuild/msbuild-task.md). |
| `xmlns` | Attribut facultatif.<br /><br /> Quand il est spécifié, l’attribut `xmlns` doit avoir la valeur `http://schemas.microsoft.com/developer/msbuild/2003`. |

### <a name="child-elements"></a>Éléments enfants

| Élément | Description |
| - | - |
| [Choisissez](../msbuild/choose-element-msbuild.md) | Élément facultatif.<br /><br /> Évalue des éléments enfants pour sélectionner un ensemble d’éléments `ItemGroup` et/ou d’éléments `PropertyGroup` à évaluer. |
| [Importer](../msbuild/import-element-msbuild.md) | Élément facultatif.<br /><br /> Permet à un fichier projet d’importer un autre fichier projet. Un projet peut ne contenir aucun élément `Import` ou en contenir plusieurs. |
| [ImportGroup](../msbuild/importgroup-element.md) | Élément facultatif.<br /><br /> Contient une collection d’éléments `Import` regroupés sous une condition facultative. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Élément facultatif.<br /><br /> Élément grouping d’éléments individuels. Les éléments sont spécifiés à l’aide de l’élément [Item](../msbuild/item-element-msbuild.md). Un projet peut ne contenir aucun élément `ItemGroup` ou en contenir plusieurs. |
| [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) | Élément facultatif.<br /><br /> Permet de définir un ensemble de définitions d’élément, correspondant à des valeurs de métadonnées appliquées par défaut à tous les éléments du projet. ItemDefinitionGroup évite d’avoir à utiliser les tâches `CreateItem` et `CreateProperty`. |
| [ProjectExtensions](../msbuild/projectextensions-element-msbuild.md) | Élément facultatif.<br /><br /> Fournit un moyen de rendre persistants les informations non-MSBuild dans un fichier projet MSBuild. Un projet peut ne contenir aucun élément `ProjectExtensions` ou en contenir un. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Élément facultatif.<br /><br /> Élément grouping de propriétés individuelles. Les propriétés sont spécifiées à l’aide de l’élément [Property](../msbuild/property-element-msbuild.md). Un projet peut ne contenir aucun élément `PropertyGroup` ou en contenir plusieurs. |
| [SDK](../msbuild/sdk-element-msbuild.md) | Élément facultatif.<br /><br /> Référence un kit de développement logiciel (SDK) de projet MSBuild.  Cet élément peut être utilisé comme alternative à l’attribut Sdk. |
| [Cible](../msbuild/target-element-msbuild.md) | Élément facultatif.<br /><br /> Contient un ensemble de tâches que MSBuild doit exécuter séquentiellement. Les tâches sont spécifiées à l’aide de l’élément [Task](../msbuild/task-element-msbuild.md). Un projet peut ne contenir aucun élément `Target` ou en contenir plusieurs. |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Élément facultatif.<br /><br /> Fournit un moyen d’inscrire des tâches dans MSBuild. Un projet peut ne contenir aucun élément `UsingTask` ou en contenir plusieurs. |

### <a name="parent-elements"></a>Éléments parents

 Aucun.

## <a name="see-also"></a>Voir aussi

- [Comment : spécifier la cible à générer en premier](../msbuild/how-to-specify-which-target-to-build-first.md)
- [Informations de référence sur la ligne de commande](../msbuild/msbuild-command-line-reference.md)
- [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
