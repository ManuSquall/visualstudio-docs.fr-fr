---
title: "ResourcesGenerator Task | Microsoft Docs"
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
  - "embedding resources into a .resources file [WPF MSBuild]"
  - "ResourcesGenerator task [WPF MSBuild]"
  - "ResourcesGenerator task [WPF MSBuild], parameters"
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResourcesGenerator Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La tâche <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> incorpore une ou plusieurs ressources \(.jpg, .ico, .bmp, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] au format binaire et autres types d'extensions\) dans un fichier .resources.  
  
## Paramètres de la tâche  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`OutputPath`|Paramètre **String** requis.<br /><br /> Spécifie le chemin d'accès du répertoire de sortie.  Si le chemin d'accès n'est pas un chemin absolu, il est traité en tant que chemin relatif au répertoire racine du projet.|  
|`OutputResourcesFile`|Paramètre de sortie **ITaskItem\[\]** obligatoire.<br /><br /> Spécifie le chemin d'accès et le nom du fichier .resources généré.  Si le chemin d'accès n'est pas un chemin absolu, le fichier .resources est généré par rapport au répertoire racine du projet.|  
|`ResourcesFiles`|Paramètre **ITaskItem\[\]** obligatoire.<br /><br /> Spécifie une ou plusieurs ressources à incorporer dans le fichier .resources généré.|  
  
## Exemple  
 L'exemple suivant génère un fichier .resources avec une seule ressource .bmp.  La ressource .bmp est générée dans un répertoire relatif au répertoire racine du projet.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="ResourcesGeneratorTask">  
    <ResourcesGenerator  
      ResourceFiles="Resource1.bmp"  
      OutputPath="myresources"  
      OutputResourcesFile="myresources\my.resources" />  
  </Target>  
</Project>  
```  
  
## Voir aussi  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Génération d'une application WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)