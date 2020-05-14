---
title: Élément OnError (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#OnError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- OnError Element [MSBuild]
- <OnError Element [MSBuild]
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18edfe06a4f2cb98fcb41e93c920b03c53daea8c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633081"
---
# <a name="onerror-element-msbuild"></a>Élément OnError (MSBuild)

Provoque l’exécution d’une ou de plusieurs cibles si l’attribut `ContinueOnError` est défini sur `false` pour une tâche en échec.

 \<Project> \<Target> \<OnError>

## <a name="syntax"></a>Syntaxe

```xml
<OnError ExecuteTargets="TargetName"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`Condition`|Attribut facultatif.<br /><br /> Condition à évaluer. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).|
|`ExecuteTargets`|Attribut requis.<br /><br /> Les cibles à exécuter si une tâche échoue. Séparez les cibles multiples avec des points-virgules. Les cibles multiples sont exécutées dans l’ordre spécifié.|

### <a name="child-elements"></a>Éléments enfants

 Aucun.

### <a name="parent-elements"></a>Éléments parents

| Élément | Description |
| - | - |
| [Target](../msbuild/target-element-msbuild.md) | Élément de conteneur pour les tâches MSBuild. |

## <a name="remarks"></a>Notes 

 MSBuild exécute `OnError` l’élément si `Target` l’une des `ContinueOnError` tâches de `ErrorAndStop` l’élément échoue avec l’attribut défini à (ou `false`). Lorsque la tâche échoue, les cibles spécifiées dans l’attribut `ExecuteTargets` sont exécutées. S’il existe plusieurs éléments `OnError` dans la cible, les éléments `OnError` sont exécutés séquentiellement lorsque la tâche échoue.

 Pour plus d’informations sur l’attribut `ContinueOnError`, voir [Élément Task (MSBuild)](../msbuild/task-element-msbuild.md). Pour plus d’informations sur les cibles, consultez l’article [MSBuild Targets](../msbuild/msbuild-targets.md) (Cibles MSBuild).

## <a name="example"></a> Exemple

 Le code suivant exécute les tâches `TaskOne` et `TaskTwo`. En `TaskOne` cas d’échec, MSBuild évalue l’élément `OnError` et exécute la `OtherTarget` cible.

```xml
<Target Name="ThisTarget">
    <TaskOne ContinueOnError="ErrorAndStop">
    </TaskOne>
    <TaskTwo>
    </TaskTwo>
    <OnError ExecuteTargets="OtherTarget" />
</Target>
```

## <a name="see-also"></a>Voir aussi

- [Référence du schéma de fichier de projet](../msbuild/msbuild-project-file-schema-reference.md)
- [Cibles](../msbuild/msbuild-targets.md)
