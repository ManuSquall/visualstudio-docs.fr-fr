---
title: Élément Output (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Output
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Output> Element [MSBuild]
- Output Element [MSBuild]
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90fbd517608c9c36db0b1035f296b9d9402abddd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633029"
---
# <a name="output-element-msbuild"></a>Élément Output (MSBuild)

Stocke les valeurs de sortie d’une tâche dans les éléments et les propriétés.

 \<Project> \<Target>
 \<Task>
 \<Output>

## <a name="syntax"></a>Syntaxe

```xml
<Output TaskParameter="Parameter"
    PropertyName="PropertyName"
    Condition = "'String A' == 'String B'" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`TaskParameter`|Attribut requis.<br /><br /> Nom du paramètre de sortie de la tâche.|
|`PropertyName`|L’attribut `PropertyName` ou `ItemName` est obligatoire.<br /><br /> Propriété recevant la valeur du paramètre de sortie de la tâche. Votre projet peut ensuite référencer la propriété avec la syntaxe $ ( \<PropertyName> ). Ce nom de propriété peut être un nouveau nom de propriété ou un nom déjà défini dans le projet.<br /><br /> Cet attribut n’est pas utilisable si `ItemName` est également utilisé.|
|`ItemName`|L’attribut `PropertyName` ou `ItemName` est obligatoire.<br /><br /> Élément recevant la valeur du paramètre de sortie de la tâche. Votre projet peut ensuite référencer l’élément avec la syntaxe @ ( \<ItemName> ). Ce nom d’élément peut être un nouveau nom d’élément ou un nom déjà défini dans le projet. Quand le nom d’élément est un élément existant, les valeurs de paramètre de sortie sont ajoutées à l’élément existant. <br /><br /> Cet attribut n’est pas utilisable si `PropertyName` est également utilisé.|
|`Condition`|Attribut facultatif.<br /><br /> Condition à évaluer. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Éléments enfants

 Aucun.

### <a name="parent-elements"></a>Éléments parents

| Élément | Description |
| - | - |
| [Tâche](../msbuild/task-element-msbuild.md) | Crée et exécute une instance d’une tâche MSBuild. |

## <a name="example"></a>Exemple

 L’exemple de code ci-après présente l’exécution de la tâche `Csc` au sein d’un élément `Target`. Les éléments et propriétés transmis aux paramètres de la tâche sont déclarés en dehors de la portée de cet exemple. La valeur du paramètre de sortie `OutputAssembly` est stockée dans l’élément `FinalAssemblyName`, et la valeur du paramètre de sortie `BuildSucceeded` est stockée dans la propriété `BuildWorked`. Pour plus d’informations, consultez l’article [Tâches MSBuild](../msbuild/msbuild-tasks.md).

```xml
<Target Name="Compile" DependsOnTargets="Resources">
    <Csc  Sources="@(CSFile)"
            TargetType="library"
            Resources="@(CompiledResources)"
            EmitDebugInformation="$(includeDebugInformation)"
            References="@(Reference)"
            DebugType="$(debuggingType)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
        <Output TaskParameter="BuildSucceeded"
                  PropertyName="BuildWorked" />
    </Csc>
</Target>
```

## <a name="see-also"></a>Voir aussi

- [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
- [Tâches](../msbuild/msbuild-tasks.md)
