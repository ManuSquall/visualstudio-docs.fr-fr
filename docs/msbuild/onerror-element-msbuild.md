---
title: "Élément OnError (MSBuild) | Microsoft Docs"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 14
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 0e5a449ef396e7b9fd23a2c018bdc7f8791b7b38
ms.openlocfilehash: 710eecad79b43c7544565d51536136e39c080d5f
ms.lasthandoff: 03/13/2017

---
# <a name="onerror-element-msbuild"></a>OnError, élément (MSBuild)
Provoque l’exécution d’une ou de plusieurs cibles si l’attribut `ContinueOnError` est défini sur `false` pour une tâche en échec.  

 \<Project>  
 \<Target>  
 \<OnError>  

## <a name="syntax"></a>Syntaxe  

```  
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

|Élément|Description|  
|-------------|-----------------|  
|[Target](../msbuild/target-element-msbuild.md)|Élément conteneur des tâches [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  

## <a name="remarks"></a>Remarques  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] exécute l’élément `OnError` si l’une des tâches de l’élément `Target` échoue avec l’attribut `ContinueOnError` défini sur `ErrorAndStop` (ou `false`). Lorsque la tâche échoue, les cibles spécifiées dans l’attribut `ExecuteTargets` sont exécutées. S’il existe plusieurs éléments `OnError` dans la cible, les éléments `OnError` sont exécutés séquentiellement lorsque la tâche échoue.  

 Pour plus d’informations sur l’attribut `ContinueOnError`, consultez l’article [Task Element (MSBuild) (Élément Task [MSBuild])](../msbuild/task-element-msbuild.md). Pour plus d’informations sur les cibles, consultez l’article [MSBuild Targets](../msbuild/msbuild-targets.md) (Cibles MSBuild).  

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
 [Informations de référence sur le schéma de fichier projet MSBuild](../msbuild/msbuild-project-file-schema-reference.md)   
 [Cibles](../msbuild/msbuild-targets.md)

