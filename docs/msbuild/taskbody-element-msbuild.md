---
title: Élément Task de UsingTask (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36644a6b21092361d92dba5f0886eb4198884995
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263186"
---
# <a name="task-element-of-usingtask-msbuild"></a>Élément Task de UsingTask (MSBuild)

Contient les données passées à un `UsingTask` `TaskFactory`. Pour plus d’informations, consultez [Élément UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<projet > \<\<de la tâche de > >

## <a name="syntax"></a>Syntaxe

```xml
<Task Evaluate="true/false" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`Evaluate`|Attribut booléen facultatif.<br /><br /> Si cet attribut présente la valeur `true`, MSBuild évalue tous les éléments internes et développe des éléments et des propriétés avant de transmettre les informations à l’élément `TaskFactory` lorsque la tâche est instanciée.|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|Données|Le texte entre les balises `Task` est envoyé mot pour mot à l’élément `TaskFactory`.|

### <a name="parent-elements"></a>Éléments parents

| Élément | Description |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Fournit un moyen d’inscrire des tâches dans MSBuild. Un projet peut ne contenir aucun élément `UsingTask` ou en contenir plusieurs. |

## <a name="example"></a>Exemple

 L'exemple suivant montre comment utiliser l'élément `Task` avec un attribut `Evaluate`.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <Task Evaluate="true">
       ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="see-also"></a>Voir aussi

- [Tâches :](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Informations de référence sur le schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
