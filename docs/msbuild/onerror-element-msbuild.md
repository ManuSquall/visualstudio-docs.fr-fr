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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 43e76a9ffece66a6330b634bb982ec14b10b803c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53924551"
---
# <a name="onerror-element-msbuild"></a>Élément OnError (MSBuild)
Provoque l’exécution d’une ou de plusieurs cibles si l’attribut `ContinueOnError` est défini sur `false` pour une tâche en échec.  

 \<Project>  
 \<Target>  
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
| [Target](../msbuild/target-element-msbuild.md) | Élément conteneur des tâches [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |

## <a name="remarks"></a>Notes  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] exécute l’élément `OnError` si l’une des tâches de l’élément `Target` échoue avec l’attribut `ContinueOnError` défini sur `ErrorAndStop` (ou `false`). Lorsque la tâche échoue, les cibles spécifiées dans l’attribut `ExecuteTargets` sont exécutées. S’il existe plusieurs éléments `OnError` dans la cible, les éléments `OnError` sont exécutés séquentiellement lorsque la tâche échoue.  

 Pour plus d’informations sur l’attribut `ContinueOnError`, voir [Élément Task (MSBuild)](../msbuild/task-element-msbuild.md). Pour plus d’informations sur les cibles, consultez l’article [MSBuild Targets](../msbuild/msbuild-targets.md) (Cibles MSBuild).  

## <a name="example"></a>Exemple  
 Le code suivant exécute les tâches `TaskOne` et `TaskTwo`. Si `TaskOne` échoue, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] évalue l’élément `OnError` et exécute la cible `OtherTarget`.  

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
 [Informations de référence sur le schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)   
 [Cibles](../msbuild/msbuild-targets.md)
