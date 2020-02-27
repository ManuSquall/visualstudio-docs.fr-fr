---
title: Élément Parameter | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7c4fa5d093952eefc870aded3d3e14a1f5983a7
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633003"
---
# <a name="parameter-element"></a>Élément de paramètre

Contient des informations sur un paramètre spécifique pour une tâche générée par une `TaskFactory``UsingTask`.  Le nom de l’élément est le nom du paramètre.  Pour plus d’informations, consultez [Élément UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask> \<ParameterGroup> \<Parameter>

## <a name="syntax"></a>Syntaxe

```xml
<ParameterGroup ParameterType="SystemType"
    Output="true/false"
    Required="true/false" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`ParameterType`|Attribut facultatif.<br /><br /> Le type .NET du paramètre, par exemple `System.String`.|
|`Output`|Attribut booléen facultatif.<br /><br /> Si cet attribut présente la valeur `true`, ce paramètre est un paramètre de sortie pour la tâche. Par défaut, la valeur est `false`.|
|`Required`|Attribut booléen facultatif.<br /><br /> Si cet attribut présente la valeur `true`, ce paramètre est obligatoire pour la tâche. Par défaut, la valeur est `false`.|

### <a name="child-elements"></a>Éléments enfants

 None.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Contient une liste facultative de paramètres qui seront présents sur la tâche générée par une `TaskFactory``UsingTask`.|

## <a name="example"></a>Exemple

 L'exemple suivant montre comment utiliser l'élément `Parameter`.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
             ...
</ParameterGroup>
       <TaskBody Evaluate="true">
      ... Task factory-specific data ...
       </TaskBody>
</UsingTask>
```

## <a name="see-also"></a>Voir aussi

- [Tâches :](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Informations de référence sur le schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
