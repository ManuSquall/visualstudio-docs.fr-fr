---
title: Élément UsingTask (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
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
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bf2882120f2e4c27e33b105585ba56261122055d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445652"
---
# <a name="usingtask-element-msbuild"></a>UsingTask, élément (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
|`AssemblyName`|L'attribut `AssemblyName` ou `AssemblyFile` est requis.<br /><br /> Nom de l'assembly à charger. L'attribut `AssemblyName` accepte les assemblys avec nom fort, bien que les noms forts ne soient pas obligatoires. L'utilisation de cet attribut équivaut au chargement d'un assembly à l'aide de la méthode <xref:System.Reflection.Assembly.Load%2A> dans .NET.<br /><br /> Vous ne pouvez pas utiliser cet attribut si l'attribut `AssemblyFile` est utilisé.|  
|`AssemblyFile`|L'attribut `AssemblyName` ou `AssemblyFile` est requis.<br /><br /> Chemin d'accès de l'assembly. Cet attribut accepte les chemins d'accès complets ou relatifs. Les chemins d'accès relatifs sont relatifs au répertoire du fichier projet ou du fichier .targets où l'élément `UsingTask` est déclaré. L'utilisation de cet attribut équivaut au chargement d'un assembly à l'aide de la méthode <xref:System.Reflection.Assembly.LoadFrom%2A> dans .NET.<br /><br /> Vous ne pouvez pas utiliser cet attribut si l'attribut `AssemblyName` est utilisé.|  
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
|[Projet](../msbuild/project-element-msbuild.md)|Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
  
## <a name="remarks"></a>Remarques  
 Les variables d'environnement, les propriétés de ligne de commande et les propriétés au niveau du projet peuvent être référencées n'importe où dans l'élément `UsingTask` s'il apparaît dans le fichier projet, explicitement ou via un fichier projet importé. Pour plus d’informations, consultez l’article [Tâches MSBuild](../msbuild/msbuild-tasks.md).  
  
> [!NOTE]
> Les propriétés au niveau du projet n'ont aucune signification si l'élément `UsingTask` provient de l'un des fichiers .tasks inscrits globalement auprès du moteur MSBuild. Les propriétés au niveau du projet ne sont pas globales pour MSBuild.  
  
 Dans MSBuild 4.0, l’utilisation de tâches peut être chargée à partir de fichiers .overridetask.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser l'élément `UsingTask` avec un attribut `AssemblyName`.  
  
```  
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
  
```  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)   
 [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
