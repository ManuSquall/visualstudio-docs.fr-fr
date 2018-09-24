---
title: Élément Parameter | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2d2407d37191e5a083080db579bc18b91b6c9449
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151744"
---
# <a name="parameter-element"></a>Élément de paramètre
Contient des informations sur un paramètre spécifique pour une tâche générée par un `UsingTask` `TaskFactory`.  Le nom de l’élément est le nom du paramètre.  Pour plus d’informations, consultez [Élément UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  

 \<Project>  
 \<UsingTask>  
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
|`Output`|Attribut booléen facultatif.<br /><br /> Si cet attribut présente la valeur `true`, ce paramètre est un paramètre de sortie pour la tâche. Par défaut, la valeur est définie sur `false`.|  
|`Required`|Attribut booléen facultatif.<br /><br /> Si cet attribut présente la valeur `true`, ce paramètre est obligatoire pour la tâche. Par défaut, la valeur est définie sur `false`.|  

### <a name="child-elements"></a>Éléments enfants  
 Aucun.  

### <a name="parent-elements"></a>Éléments parents  

|Élément|Description|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Contient une liste facultative de paramètres qui seront présents sur la tâche générée par un `UsingTask` `TaskFactory`.|  

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
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)   
 [Informations de référence sur le schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
