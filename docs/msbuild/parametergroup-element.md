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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a531073ba6f2f55272b719a116caad724d29e53
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916161"
---
# <a name="parametergroup-element"></a>Élément ParameterGroup
Contient une liste facultative de paramètres qui seront présents sur la tâche générée par `UsingTask` `TaskFactory`. Pour plus d’informations, consultez [Élément UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  

 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  

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
|[Paramètre](../msbuild/parameter-element.md)|Contient des informations sur un paramètre spécifique pour une tâche générée par un `UsingTask` `TaskFactory`. Le nom de l’élément est le nom du paramètre.|  

### <a name="parent-elements"></a>Éléments parents  

| Élément | Description |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Permet d’inscrire des tâches dans [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Un projet peut ne contenir aucun élément `UsingTask` ou en contenir plusieurs. |

## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser l'élément `ParameterGroup`.  

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
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)   
 [Informations de référence sur le schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
