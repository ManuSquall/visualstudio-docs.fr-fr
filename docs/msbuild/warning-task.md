---
title: "Warning Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Warning"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Warning task [MSBuild]"
  - "MSBuild, Warning task"
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Warning Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Enregistre un avertissement lors d'une génération selon une instruction conditionnelle évaluée.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `Warning`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Code`|Paramètre `String` facultatif.<br /><br /> Code d'avertissement à associer à l'avertissement.|  
|`File`|Paramètre `String` facultatif.<br /><br /> Spécifie le fichier pertinent, le cas échéant.  Si aucun fichier n'est fourni, le fichier qui contient la tâche d'avertissement \(Warning\) est utilisé.|  
|`HelpKeyword`|Paramètre `String` facultatif.<br /><br /> Mot clé d'aide à associer à l'avertissement.|  
|`Text`|Paramètre `String` facultatif.<br /><br /> Texte d'avertissement enregistré par [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] si le paramètre `Condition` prend la valeur `true`.|  
  
## Notes  
 La tâche `Warning` permet aux projets [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] de rechercher la présence d'une configuration ou d'une propriété requise avant de passer à l'étape de génération suivante.  
  
 Si le paramètre `Condition` de la tâche `Warning` a la valeur `true`, la valeur de l'attribut `Text` est enregistrée dans un journal et la génération se poursuit.  Si un paramètre `Condition` n'existe pas, le texte d'avertissement est enregistré dans un journal.  Pour plus d'informations sur la journalisation, consultez [Obtention de journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Exemple  
 L'exemple de code suivant vérifie les propriétés définies dans la ligne de commande.  En l'absence de propriétés définies, le projet déclenche un événement d'avertissement et enregistre la valeur du paramètre `Text` de la tâche `Warning` dans un journal.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## Voir aussi  
 [Obtention de journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)