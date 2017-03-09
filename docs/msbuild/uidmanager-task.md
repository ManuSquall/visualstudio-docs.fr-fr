---
title: "UidManager Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "UidManager task [WPF MSBuild]"
  - "UidManager task [WPF MSBuild], parameters"
  - "managing UIDs when localizing XAML elements [WPF MSBuild]"
  - "localizing XAML elements [WPF MSBuild], managing UIDs"
  - "checking UIDs when localizing XAML elements [WPF MSBuild]"
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# UidManager Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La tâche <xref:Microsoft.Build.Tasks.Windows.UidManager> vérifie, met à jour ou supprime les identificateurs uniques \(UID\), afin de localiser tous les éléments [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] inclus dans les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] sources.  
  
## Paramètres de la tâche  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`IntermediateDirectory`|Paramètre **String** facultatif.<br /><br /> Spécifie le répertoire utilisé pour sauvegarder les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] sources spécifiés par le paramètre **MarkupFiles**.|  
|`MarkupFiles`|Paramètre **ITaskItem\[\]** obligatoire.<br /><br /> Spécifie les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] sources à inclure pour la vérification, la mise à jour ou la suppression des identificateurs uniques \(UID\).|  
|`Task`|Paramètre **String** requis.<br /><br /> Spécifie la tâche de gestion des identificateurs uniques \(UID\) que vous souhaitez exécuter.  Les options valides sont **Vérifier**, **Mettre à jour** ou **Supprimer**.|  
  
## Exemple  
 L'exemple suivant utilise la tâche <xref:Microsoft.Build.Tasks.Windows.UidManager> pour vérifier si les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] sources spécifiés contiennent des éléments [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] avec des identificateurs uniques \(UID\) appropriés.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UidManagerTask">  
    <UidManager  
      Task="Check"  
      MarkupFiles="Page1.xaml;Page2.xaml"  
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />  
  </Target>  
</Project>  
```  
  
## Voir aussi  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Génération d'une application WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [Comment : localiser une application](../Topic/How%20to:%20Localize%20an%20Application.md)