---
title: "Élément UsingTask (MSBuild) | Microsoft Docs"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UsingTask
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UsingTask element [MSBuild]
- <UsingTask> element [MSBuild]
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
caps.latest.revision: 23
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
ms.openlocfilehash: dfef5e6747783e8a875d08b735a7dbbc72bd84dc
ms.lasthandoff: 03/13/2017

---
# <a name="usingtask-element-msbuild"></a>UsingTask, élément (MSBuild)
Mappe la tâche référencée dans un élément [Task](../msbuild/task-element-msbuild.md) sur l’assembly qui contient l’implémentation de la tâche.  

 \<Project>  
 \<UsingTask>  

## <a name="syntax"></a>Syntaxe  

```  
<UsingTask TaskName="TaskName"  
    AssemblyName = "AssemblyName"   
    TaskFactory = "ClassName"  
    Condition="'String A'=='String B'" />  
```  

## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  

### <a name="attributes"></a>Attributs  

|Attribut|Description|  
|---------------|-----------------|  
|`AssemblyName`|L'attribut `AssemblyName` ou `AssemblyFile` est requis.<br /><br /> Nom de l'assembly à charger. L'attribut `AssemblyName` accepte les assemblys avec nom fort, bien que les noms forts ne soient pas obligatoires. L’utilisation de cet attribut équivaut au chargement d’un assembly à l’aide de la méthode <xref:System.Reflection.Assembly.Load%2A> dans .NET.<br /><br /> Vous ne pouvez pas utiliser cet attribut si l'attribut `AssemblyFile` est utilisé.|  
|`AssemblyFile`|L'attribut `AssemblyName` ou `AssemblyFile` est requis.<br /><br /> Chemin d'accès de l'assembly. Cet attribut accepte les chemins d'accès complets ou relatifs. Les chemins d'accès relatifs sont relatifs au répertoire du fichier projet ou du fichier .targets où l'élément `UsingTask` est déclaré. L’utilisation de cet attribut équivaut au chargement d’un assembly à l’aide de la méthode <xref:System.Reflection.Assembly.LoadFrom%2A> dans .NET.<br /><br /> Vous ne pouvez pas utiliser cet attribut si l'attribut `AssemblyName` est utilisé.|  
|`TaskFactory`|Attribut facultatif.<br /><br /> Spécifie la classe incluse dans l'assembly qui est responsable de la génération des instances du nom `Task` spécifié.  L'utilisateur peut également spécifier un `TaskBody` en tant qu'élément enfant que la fabrique de tâches reçoit et utilise pour générer la tâche. Le contenu de `TaskBody` est propre à la fabrique de tâches.|  
|`TaskName`|Attribut requis.<br /><br /> Nom de la tâche à référencer à partir d'un assembly. Si des ambiguïtés sont possibles, cet attribut doit toujours spécifier des espaces de noms complets. S'il existe des ambiguïtés, MSBuild choisit une correspondance arbitraire, laquelle peut produire des résultats inattendus.|  
|`Condition`|Attribut facultatif.<br /><br /> Condition à évaluer. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Éléments enfants  

|Élément|Description|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Jeu de paramètres qui apparaissent sur la tâche générée par le `TaskFactory` spécifié.|  
|[Task](../msbuild/task-element-msbuild.md)|Données transférées au `TaskFactory` pour générer une instance de la tâche.|  

### <a name="parent-elements"></a>Éléments parents  

|Élément|Description|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  

## <a name="remarks"></a>Notes  
 Les variables d'environnement, les propriétés de ligne de commande et les propriétés au niveau du projet peuvent être référencées n'importe où dans l'élément `UsingTask` s'il apparaît dans le fichier projet, explicitement ou via un fichier projet importé. Pour plus d’informations, consultez l’article [Tâches MSBuild](../msbuild/msbuild-tasks.md).  

> [!NOTE]
>  Les propriétés au niveau du projet n'ont aucune signification si l'élément `UsingTask` provient de l'un des fichiers .tasks inscrits globalement auprès du moteur MSBuild. Les propriétés au niveau du projet ne sont pas globales pour MSBuild.  

 Dans MSBuild 4.0, l’utilisation de tâches peut être chargée à partir de fichiers .overridetask.  

## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser l'élément `UsingTask` avec un attribut `AssemblyName`.  

```xml  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody>  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  

## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser l'élément `UsingTask` avec un attribut `AssemblyFile`.  

```xml  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  

## <a name="see-also"></a>Voir aussi  
 [Tâches MSBuild](../msbuild/msbuild-tasks.md)   
 [Référence des tâches](../msbuild/msbuild-task-reference.md)   
 [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)

