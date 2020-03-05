---
title: Élément UsingTask (MSBuild) | Microsoft Docs
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
ms.openlocfilehash: 2d977892956c90fd88ff913b9c9300b0176323a4
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263121"
---
# <a name="usingtask-element-msbuild"></a>Élément UsingTask (MSBuild)

Mappe la tâche référencée dans un élément [Task](../msbuild/task-element-msbuild.md) sur l’assembly qui contient l’implémentation de la tâche.

 \<Project> \<UsingTask>

## <a name="syntax"></a>Syntaxe

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

> [!NOTE]
> Contrairement aux propriétés et aux éléments, le *premier* élément `UsingTask` qui s’applique à un `TaskName` est utilisé ; pour remplacer des tâches, vous devez définir une nouvelle `UsingTask` *avant* celle existante.

## <a name="attributes-and-elements"></a>Attributs et éléments

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`AssemblyName`|L'attribut `AssemblyName` ou `AssemblyFile` est requis.<br /><br /> Nom de l'assembly à charger. L'attribut `AssemblyName` accepte les assemblys avec nom fort, bien que les noms forts ne soient pas obligatoires. L'utilisation de cet attribut équivaut au chargement d'un assembly à l'aide de la méthode <xref:System.Reflection.Assembly.Load%2A> dans .NET.<br /><br /> Vous ne pouvez pas utiliser cet attribut si l'attribut `AssemblyFile` est utilisé.|
|`AssemblyFile`|L'attribut `AssemblyName` ou `AssemblyFile` est requis.<br /><br /> Chemin d'accès de l'assembly. Cet attribut accepte les chemins d'accès complets ou relatifs. Les chemins d'accès relatifs sont relatifs au répertoire du fichier projet ou du fichier .targets où l'élément `UsingTask` est déclaré. L'utilisation de cet attribut équivaut au chargement d'un assembly à l'aide de la méthode <xref:System.Reflection.Assembly.LoadFrom%2A> dans .NET.<br /><br /> Vous ne pouvez pas utiliser cet attribut si l'attribut `AssemblyName` est utilisé.|
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

## <a name="remarks"></a>Notes

 Les variables d'environnement, propriétés de ligne de commande, propriétés au niveau du projet et éléments au niveau du projet peuvent être référencés n'importe où dans les éléments `UsingTask` inclus dans le fichier projet, directement ou via un fichier projet importé. Pour plus d’informations, consultez l’article [Tâches MSBuild](../msbuild/msbuild-tasks.md).

> [!NOTE]
> Les propriétés et éléments de niveau projet n’ont aucune signification si l’élément `UsingTask` provient de l’un des fichiers *.tasks* inscrits globalement auprès du moteur MSBuild. Les valeurs au niveau du projet ne sont pas globales pour MSBuild.

 Dans MSBuild 4.0, les tâches peuvent être chargées à partir de fichiers *.overridetask*.

## <a name="example"></a>Exemple

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

## <a name="example"></a>Exemple

 L'exemple suivant montre comment utiliser l'élément `UsingTask` avec un attribut `AssemblyFile`.

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>Voir aussi

- [Tâches :](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Informations de référence sur le schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
