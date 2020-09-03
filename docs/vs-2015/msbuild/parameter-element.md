---
title: Élément Parameter | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a815d2ef623a35030469fa631cae65653c2fe2d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185223"
---
# <a name="parameter-element"></a>Élément Parameter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contient des informations sur un paramètre spécifique pour une tâche générée par un `UsingTask``TaskFactory`.  Le nom de l’élément est le nom du paramètre.  Pour plus d’informations, consultez l’article [Élément UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  
 \<Parameter>  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`ParameterType`|Attribut facultatif.<br /><br /> Type .NET du paramètre, par exemple « System.String ».|  
|`Output`|Attribut booléen facultatif.<br /><br /> Si cet attribut présente la valeur `true`, ce paramètre est un paramètre de sortie pour la tâche. Par défaut, la valeur est `false`.|  
|`Required`|Attribut booléen facultatif.<br /><br /> Si cet attribut présente la valeur `true`, ce paramètre est un paramètre obligatoire pour la tâche. Par défaut, la valeur est `false`.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Contient une liste facultative de paramètres qui seront présents sur la tâche générée par un `UsingTask``TaskFactory`.|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser l'élément `Parameter`.  
  
```  
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
 [Décrites](../msbuild/msbuild-tasks.md)   
 [Référence de tâche](../msbuild/msbuild-task-reference.md)   
 [Référence de schéma de fichier de projet](../msbuild/msbuild-project-file-schema-reference.md)
