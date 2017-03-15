---
title: "GetWinFXPath Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "getting the directory of the current .NET Framework runtime [WPF MSBuild]"
  - "GetWinFXPath task [WPF MSBuild], parameters"
  - "GetWinFXPath task [WPF MSBuild]"
  - "obtaining the path to the current .NET Framework runtime [WPF MSBuild]"
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GetWinFXPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La tâche <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> retourne le répertoire de l'exécution [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] en cours.  
  
## Paramètres de la tâche  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`WinFXPath`|Paramètre de sortie **String** facultatif.<br /><br /> Spécifie le chemin d'accès réel au runtime [!INCLUDE[TLA2#tla_winfx](../msbuild/includes/tla2sharptla_winfx_md.md)].|  
|`WinFXNativePath`|Paramètre **String** requis.<br /><br /> Spécifie le chemin d'accès au runtime [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)] natif.|  
|`WinFXWowPath`|Paramètre **String** requis.<br /><br /> Spécifie le chemin d'accès vers les assemblys [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] dans le module 32 bits **Windows on Windows** sur des systèmes 64 bits.|  
  
## Notes  
 Si la tâche <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> s'exécute sur un processeur 64 bits, le paramètre **WinFXPath** a pour valeur le chemin d'accès stocké dans le paramètre **WinFXWowPath** ; sinon, le paramètre **WinFXPath** a pour valeur le chemin d'accès stocké dans le paramètre **WinFXNativePath**.  
  
## Exemple  
 L'exemple suivant indique comment utiliser la tâche **GetWinFXPath** pour détecter le chemin d'accès natif au runtime [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)].  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.GetWinFXPath"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GetWinFXPathTask">  
    <GetWinFXPath  
      WinFXNativePath="c:\WinFXNative"   
      WinFXWowPath="c:\WinFXWowNative" />  
  </Target>  
  <Import Project="$(MSBuildBinPath)\Microsoft.WinFX.targets" />  
</Project>  
```  
  
## Voir aussi  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Génération d'une application WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)