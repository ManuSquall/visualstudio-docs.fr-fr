---
title: ParameterGroup, élément | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c06b9c530d3fff0fdfa429df633daaa4dde8c52
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263073"
---
# <a name="parametergroup-element"></a>Élément ParameterGroup

Contient une liste facultative des paramètres qui seront présents `UsingTask` `TaskFactory`sur la tâche générée par un . Pour plus d’informations, voir [Élément UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask> \<ParameterGroup>

## <a name="syntax"></a>Syntaxe

```xml
<ParameterGroup />
```

## <a name="attributes-and-elements"></a>Attributs et éléments

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

 Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Paramètre](../msbuild/parameter-element.md)|Contient des informations sur un paramètre spécifique `UsingTask` `TaskFactory`pour une tâche qui est générée par un . Le nom de l’élément est le nom du paramètre.|

### <a name="parent-elements"></a>Éléments parents

| Élément | Description |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Fournit un moyen d’enregistrer les tâches dans MSBuild. Un projet peut ne contenir aucun élément `UsingTask` ou en contenir plusieurs. |

## <a name="example"></a> Exemple

 L'exemple suivant montre comment utiliser l'élément `ParameterGroup`.

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
- [Référence du schéma de fichier de projet](../msbuild/msbuild-project-file-schema-reference.md)
