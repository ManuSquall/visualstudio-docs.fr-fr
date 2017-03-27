---
title: "Élément TaskBody (MSBuild) | Microsoft Docs"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- TaskBody element [MSBuild]
- <TaskBody> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
caps.latest.revision: 7
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
ms.openlocfilehash: 83e34546141a69cf93fb0cbbf86393b8fa749ef4
ms.lasthandoff: 03/13/2017

---
# <a name="taskbody-element-msbuild"></a>Élément TaskBody (MSBuild)
Contient les données transmises à un élément `UsingTask``TaskFactory`. Pour plus d’informations, consultez [UsingTask, élément (MSBuild)](../msbuild/usingtask-element-msbuild.md).  

 \<Project>  
 \<UsingTask>  
 \<TaskBody>  

## <a name="syntax"></a>Syntaxe  

```  
<TaskBody Evaluate="true/false" />  
```  

## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  

### <a name="attributes"></a>Attributs  

|Attribut|Description|  
|---------------|-----------------|  
|`Evaluate`|Attribut booléen facultatif.<br /><br /> Si cet attribut présente la valeur `true`, MSBuild évalue tous les éléments internes et développe des éléments et des propriétés avant de transmettre les informations à l’élément `TaskFactory` lorsque la tâche est instanciée.|  

### <a name="child-elements"></a>Éléments enfants  

|Élément|Description|  
|-------------|-----------------|  
|Données|Le texte entre les balises `TaskBody` est envoyé mot pour mot à l’élément `TaskFactory`.|  

### <a name="parent-elements"></a>Éléments parents  

|Élément|Description|  
|-------------|-----------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Permet d’inscrire des tâches dans [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Un projet peut ne contenir aucun élément `UsingTask` ou en contenir plusieurs.|  

## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser l'élément `TaskBody` avec un attribut `Evaluate`.  

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
 [Tâches MSBuild](../msbuild/msbuild-tasks.md)   
 [Référence des tâches](../msbuild/msbuild-task-reference.md)   
 [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)

