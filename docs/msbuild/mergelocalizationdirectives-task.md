---
title: "MergeLocalizationDirectives Task | Microsoft Docs"
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
  - "localizing XAML [WPF MSBuild], moving comments and attributes to a separate file"
  - "MergeLocalizationDirectives task [WPF MSBuild], parameters"
  - "MergeLocalizationDirectives task [WPF MSBuild]"
  - "moving localization comments and attributes to a separate file [WPF MSBuild]"
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MergeLocalizationDirectives Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La tâche <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> fusionne les attributs et les commentaires de localisation d'un ou plusieurs fichiers au format binaire [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dans un seul fichier pour l'intégralité de l'assembly.  
  
## Paramètres de la tâche  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`GeneratedLocalizationFiles`|Paramètre **ITaskItem\[\]** obligatoire.<br /><br /> Spécifie la liste des fichiers de directives concernant la localisation pour des fichiers individuels au format binaire [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`OutputFile`|Paramètre de sortie **String** obligatoire.<br /><br /> Spécifie le chemin de sortie de l'assembly compilé des directives concernant la localisation.|  
  
## Notes  
 Vous pouvez ajouter des attributs et des commentaires de localisation au contenu [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)].  La prise en charge de la localisation [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)] vous permet de retirer des attributs et des commentaires de localisation pour les placer dans un fichier .loc distinct de l'assembly généré.  Pour ce faire, utilisez l'attribut **LocalizationPropertyStorage**.  Pour plus d'informations sur les attributs et les commentaires de localisation, ainsi que sur **LocalizationPropertyStorage**, consultez [Attributs et commentaires de localisation](../Topic/Localization%20Attributes%20and%20Comments.md).  
  
## Exemple  
 L'exemple suivant fusionne les commentaires de localisation de plusieurs fichiers au format binaire [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dans un seul fichier .loc.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MergeLocalizationDirectivesTask">  
    <MergeLocalizationDirectives   
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"  
      OutputFile="obj\debug\WPFMSBuildSample.loc" />  
  </Target>  
</Project>  
```  
  
## Voir aussi  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Génération d'une application WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)