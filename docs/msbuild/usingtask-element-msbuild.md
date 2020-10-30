---
title: Élément UsingTask (MSBuild) | Microsoft Docs
description: En savoir plus sur l’élément de UsingTask MSBuild, qui mappe la tâche référencée dans un élément Task à l’assembly qui contient l’implémentation de la tâche.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UsingTask
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UsingTask element [MSBuild]
- <UsingTask> element [MSBuild]
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d09f266f5bf51b870dbbbc0f80aa8282e91faa9
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046117"
---
# <a name="usingtask-element-msbuild"></a>Élément UsingTask (MSBuild)

Mappe la tâche référencée dans un élément [Task](../msbuild/task-element-msbuild.md) sur l’assembly qui contient l’implémentation de la tâche.

 \<Project> \<UsingTask>

## <a name="syntax"></a>Syntax

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

> [!NOTE]
> Contrairement aux propriétés et aux éléments, le *premier* `UsingTask` élément qui s’applique à un `TaskName` est utilisé ; pour remplacer des tâches, vous devez définir un nouveau `UsingTask` *avant* celui existant.

## <a name="attributes-and-elements"></a>Attributs et éléments

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`Architecture`|Attribut facultatif.<br /><br /> Spécifie que la tâche doit s’exécuter dans un processus du nombre de bits spécifié. Si le processus actuel ne satisfait pas à la spécification, la tâche est exécutée dans un processus hôte de tâche qui le fait.<br /><br /> Les valeurs prises en charge sont `x86` (32-bit), `x64` (64 bits), `CurrentArchitecture` et `*` (n’importe quelle architecture).|  
|`AssemblyName`|L'attribut `AssemblyName` ou `AssemblyFile` est requis.<br /><br /> Nom de l'assembly à charger. L'attribut `AssemblyName` accepte les assemblys avec nom fort, bien que les noms forts ne soient pas obligatoires. L'utilisation de cet attribut équivaut au chargement d'un assembly à l'aide de la méthode <xref:System.Reflection.Assembly.Load%2A> dans .NET.<br /><br /> Vous ne pouvez pas utiliser cet attribut si l'attribut `AssemblyFile` est utilisé.|
|`AssemblyFile`|L'attribut `AssemblyName` ou `AssemblyFile` est requis.<br /><br /> Chemin d'accès du fichier de l'assembly. Cet attribut accepte les chemins d'accès complets ou relatifs. Les chemins d'accès relatifs sont relatifs au répertoire du fichier projet ou du fichier .targets où l'élément `UsingTask` est déclaré. L'utilisation de cet attribut équivaut au chargement d'un assembly à l'aide de la méthode <xref:System.Reflection.Assembly.LoadFrom%2A> dans .NET.<br /><br /> Vous ne pouvez pas utiliser cet attribut si l'attribut `AssemblyName` est utilisé.|
|`Runtime`|Attribut facultatif.<br /><br /> Spécifie que la tâche doit s’exécuter dans un .NET Framework Runtime de la version spécifiée. Si le processus actuel ne satisfait pas à la spécification, la tâche est exécutée dans un processus hôte de tâche qui le fait. Non pris en charge dans MSBuild .NET Core.<br /><br /> Les valeurs prises en charge sont `CLR2` (.NET Framework 3,5), `CLR4` (.NET Framework 4.7.2 ou version ultérieure), `CurrentRuntime` et `*` (n’importe quel Runtime).|  
|`TaskFactory`|Attribut facultatif.<br /><br /> Spécifie la classe incluse dans l'assembly qui est responsable de la génération des instances du nom `Task` spécifié.  L'utilisateur peut également spécifier un `Task` en tant qu'élément enfant que la fabrique de tâches reçoit et utilise pour générer la tâche. Le contenu de `Task` est propre à la fabrique de tâches.|
|`TaskName`|Attribut requis.<br /><br /> Nom de la tâche à référencer à partir d'un assembly. Si des ambiguïtés sont possibles, cet attribut doit toujours spécifier des espaces de noms complets. S'il existe des ambiguïtés, MSBuild choisit une correspondance arbitraire, laquelle peut produire des résultats inattendus.|
|`Condition`|Attribut facultatif.<br /><br /> Condition à évaluer. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Jeu de paramètres qui apparaissent sur la tâche générée par le `TaskFactory` spécifié.|
|[Tâche](../msbuild/task-element-msbuild.md)|Données transférées au `TaskFactory` pour générer une instance de la tâche.|

### <a name="parent-elements"></a>Éléments parents

| Élément | Description |
| - | - |
| [Projet](../msbuild/project-element-msbuild.md) | Élément racine requis d’un fichier projet MSBuild. |

## <a name="remarks"></a>Remarques

 Les variables d'environnement, propriétés de ligne de commande, propriétés au niveau du projet et éléments au niveau du projet peuvent être référencés n'importe où dans les éléments `UsingTask` inclus dans le fichier projet, directement ou via un fichier projet importé. Pour plus d’informations, consultez l’article [Tâches MSBuild](../msbuild/msbuild-tasks.md).

> [!NOTE]
> Les propriétés et éléments de niveau projet n’ont aucune signification si l’élément `UsingTask` provient de l’un des fichiers *.tasks* inscrits globalement auprès du moteur MSBuild. Les valeurs au niveau du projet ne sont pas globales pour MSBuild.

 Dans MSBuild 4.0, les tâches peuvent être chargées à partir de fichiers *.overridetask* .

L’assembly contenant la tâche personnalisée est chargé lors de la `Task` première utilisation de.

## <a name="example-1"></a>Exemple 1

 L'exemple suivant montre comment utiliser l'élément `UsingTask` avec un attribut `AssemblyName`.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <Task>
      ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="example-2"></a>Exemple 2

 L'exemple suivant montre comment utiliser l'élément `UsingTask` avec un attribut `AssemblyFile`.

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Procédure : configurer des cibles et des tâches](../msbuild/how-to-configure-targets-and-tasks.md)   
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
