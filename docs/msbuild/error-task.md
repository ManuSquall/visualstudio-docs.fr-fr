---
title: "Error Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Error"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Error task [MSBuild]"
  - "MSBuild, Error task"
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Error Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Arrête une génération et enregistre une erreur basée sur une instruction conditionnelle évaluée.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `Error`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Code`|Paramètre `String` facultatif.<br /><br /> Code d'erreur à associer à l'erreur.|  
|`File`|Paramètre `String` facultatif.<br /><br /> Nom du fichier qui contient l'erreur.  Si aucun nom de fichier n'est fourni, le fichier qui contient la tâche d'erreur \(Error\) sera utilisé.|  
|`HelpKeyword`|Paramètre `String` facultatif.<br /><br /> Mot clé d'aide à associer à l'erreur.|  
|`Text`|Paramètre `String` facultatif.<br /><br /> Texte d'erreur enregistré par [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] si le paramètre `Condition` prend la valeur `true`.|  
  
## Notes  
 La tâche `Error` permet aux projets [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] d'envoyer le texte d'erreur aux enregistreurs d'événements et d'arrêter l'exécution de la génération.  
  
 Si le paramètre `Condition` a la valeur `true`, la génération s'arrête et une erreur est enregistrée.  S'il n'existe pas de paramètre `Condition`, l'erreur est enregistrée et arrête l'exécution de la génération.  Pour plus d'informations sur la journalisation, consultez [Obtention de journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Exemple  
 L'exemple de code suivant vérifie que toutes les propriétés requises sont définies.  Si ce n'est pas le cas, le projet génère un événement d'erreur et enregistre la valeur du paramètre `Text` de la tâche `Error` dans un journal.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Error  
            Text=" The 0 property must be set on the command line."  
            Condition="'$(0)' == ''" />  
        <Error  
            Text="The FREEBUILD property must be set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## Voir aussi  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Obtention de journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)