---
title: Élément OnError (MSBuild) | Microsoft Docs
description: Découvrez comment MSBuild utilise l’élément OnError pour déclencher l’exécution d’une ou de plusieurs cibles, si l’attribut ContinueOnError a la valeur false pour une tâche ayant échoué.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 574f49b65f47b4a22240ca68b4d74c90ee580a15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905338"
---
# <a name="onerror-element-msbuild"></a>Élément OnError (MSBuild)

Provoque l’exécution d’une ou de plusieurs cibles si l’attribut `ContinueOnError` est défini sur `false` pour une tâche en échec.

 \<Project> \<Target>
 \<OnError>

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
| [Cible](../msbuild/target-element-msbuild.md) | Élément conteneur pour les tâches MSBuild. |

## <a name="remarks"></a>Remarques

 MSBuild exécute l' `OnError` élément si l’une des tâches de l' `Target` élément échoue avec l' `ContinueOnError` attribut défini sur `ErrorAndStop` (ou `false` ). Lorsque la tâche échoue, les cibles spécifiées dans l’attribut `ExecuteTargets` sont exécutées. S’il existe plusieurs éléments `OnError` dans la cible, les éléments `OnError` sont exécutés séquentiellement lorsque la tâche échoue.

 Pour plus d’informations sur l’attribut `ContinueOnError`, voir [Élément Task (MSBuild)](../msbuild/task-element-msbuild.md). Pour plus d’informations sur les cibles, consultez l’article [MSBuild Targets](../msbuild/msbuild-targets.md) (Cibles MSBuild).

## <a name="example"></a>Exemple

 Le code suivant exécute les tâches `TaskOne` et `TaskTwo`. En cas d' `TaskOne` échec, MSBuild évalue l' `OnError` élément et exécute la `OtherTarget` cible.

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

- [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
- [Cibles](../msbuild/msbuild-targets.md)
