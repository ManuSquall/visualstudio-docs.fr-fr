---
title: "MarkupCompilePass2 Task | Microsoft Docs"
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
  - "performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task"
  - "MarkupCompilePass2 task [WPF MSBuild]"
  - "MarkupCompilePass2 task [WPF MSBuild], parameters"
ms.assetid: 1d25689a-d21f-4b05-be26-95aa0ed4fd03
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MarkupCompilePass2 Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> exécute un deuxième passage de compilation du balisage sur les fichiers [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] qui font référence à des types du même projet.  
  
## Paramètres de la tâche  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Paramètre **Boolean** facultatif.<br /><br /> Spécifie s'il faut exécuter la tâche dans un <xref:System.AppDomain> séparé.  Si ce paramètre retourne la valeur **false**, la tâche s'exécute plus rapidement et dans le même <xref:System.AppDomain> que [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)].  Si le paramètre retourne la valeur **true**, la tâche s'exécute plus lentement dans un deuxième <xref:System.AppDomain> isolé de [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)].|  
|`AssembliesGeneratedDuringBuild`|Paramètre **String\[\]** facultatif.<br /><br /> Spécifie des références aux assemblys qui sont modifiés lors du processus de génération.  Par exemple, une solution [!INCLUDE[TLA#tla_visualstu2005](../msbuild/includes/tlasharptla_visualstu2005_md.md)] peut contenir un projet qui référence la sortie compilée d'un autre projet.  Dans ce cas, la sortie compilée du deuxième projet peut être ajoutée à **AssembliesGeneratedDuringBuild**.<br /><br /> Remarque : **AssembliesGeneratedDuringBuild** doit contenir des références au jeu complet des assemblys générés par une solution de génération.|  
|`AssemblyName`|Paramètre **String** requis.<br /><br /> Spécifie le nom court de l'assembly généré pour un projet.  Par exemple, si un projet génère un exécutable [!INCLUDE[TLA#tla_win](../msbuild/includes/tlasharptla_win_md.md)] dont le nom est **WinExeAssembly.exe**, le paramètre **AssemblyName** a la valeur **WinExeAssembly**.|  
|`GeneratedBaml`|Paramètre de sortie **ITaskItem\[\]** facultatif.<br /><br /> Contient la liste des fichiers générés au format binaire [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`KnownReferencePaths`|Paramètre **String\[\]** facultatif.<br /><br /> Spécifie les références aux assemblys qui ne sont jamais modifiés au cours du processus de génération.  Inclut des assemblys localisés dans le [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], dans un répertoire d'installation [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)], et ainsi de suite.|  
|`Language`|Paramètre **String** requis.<br /><br /> Spécifie le langage managé pris en charge par le compilateur.  les options valides sont **C\#**, **VB**, **JScript**, et **C\+\+**.|  
|`LocalizationDirectivesToLocFile`|Paramètre **String** facultatif.<br /><br /> Spécifie comment générer des informations de localisation pour chaque fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] source.  Les options valides sont **None**, **CommentsOnly** et **All**.|  
|`OutputPath`|Paramètre **String** requis.<br /><br /> Spécifie le répertoire dans lequel les fichiers au format binaire [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] sont générés.|  
|`OutputType`|Paramètre **String** requis.<br /><br /> Spécifie le type d'assembly généré par un projet.  Les options valides sont **winexe**, **exe**, **library** et **netmodule**.|  
|`References`|Paramètre **ITaskItem\[\]** facultatif.<br /><br /> Spécifie la liste de références de fichiers aux assemblys qui contiennent les types utilisés dans les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].  L'une des références correspond à l'assembly généré par la tâche <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>, qui doit être exécutée avant la tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>.|  
|`RootNamespace`|Paramètre **String** facultatif.<br /><br /> Spécifie l'espace de noms racine pour les classes à l'intérieur du projet.  **RootNamespace** est également utilisé comme espace de noms par défaut d'un fichier de code managé généré lorsque le fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] correspondant n'inclut pas l'attribut `x:Class`.|  
|`XAMLDebuggingInformation`|Paramètre **Boolean** facultatif.<br /><br /> Lorsque la valeur est **true**, les informations de diagnostic sont générées et incluses dans le [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] compilé pour faciliter le débogage.|  
  
## Notes  
 Avant d'exécuter **MarkupCompilePass2**, vous devez générer un assembly temporaire contenant les types utilisés par les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dont le passage de compilation du balisage a été différé.  Pour générer l'assembly temporaire, exécutez la tâche **GenerateTemporaryTargetAssembly**.  
  
 Une référence à l'assembly temporaire généré est fournie à <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> lors de son exécution afin que les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)], dont la compilation a été différée au premier passage de compilation du balisage, puissent désormais être compilés au format binaire.  
  
## Exemple  
 L'exemple suivant indique comment utiliser la tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> pour exécuter un deuxième passage de compilation.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MarkupCompilePass2Task">  
    <MarkupCompilePass2   
      AssemblyName="WPFMSBuildSample"  
      Language="C#"  
      OutputType="WinExe"  
      OutputPath="obj\Debug\"  
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />  
  </Target>  
</Project>  
```  
  
## Voir aussi  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Génération d'une application WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [Vue d'ensemble des applications de navigateur XAML](../Topic/WPF%20XAML%20Browser%20Applications%20Overview.md)