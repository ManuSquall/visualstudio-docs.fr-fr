---
title: Élément Parameter | Microsoft Docs
description: En savoir plus sur l’élément de paramètre MSBuild, qui contient des informations sur un paramètre spécifique pour une tâche générée par un TaskFactory de UsingTask.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 728618a6d9ff174d4d4bf7cdc20516433d06036b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918865"
---
# <a name="parameter-element"></a>Élément de paramètre

Contient des informations sur un paramètre spécifique pour une tâche générée par un `UsingTask` `TaskFactory` .  Le nom de l’élément est le nom du paramètre.  Pour plus d’informations, voir [Élément UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask>
 \<ParameterGroup>
 \<Parameter>

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

 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Contient une liste facultative de paramètres qui seront présents sur la tâche générée par un `UsingTask` `TaskFactory` .|

## <a name="example"></a>Exemple

 L'exemple suivant montre comment utiliser l'élément `Parameter`.

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

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
