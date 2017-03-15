---
title: "GenerateTemporaryTargetAssembly Task | Microsoft Docs"
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
  - "build process [WPF MSBuild], XAML page refers to a locally declared type"
  - "GenerateTemporaryTargetAssembly task [WPF MSBuild]"
  - "GenerateTemporaryTargetAssembly task [WPF MSBuild], parameters"
  - "creating an assembly [WPF MSBuild], XAML page refers to a locally declared type"
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GenerateTemporaryTargetAssembly Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La tâche <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> génère un assembly si au moins une page [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] d'un projet fait référence à un type localement déclaré dans ce projet.  L'assembly généré est supprimé une fois le processus de génération terminé, ou lorsque le processus de génération échoue.  
  
## Paramètres de la tâche  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AssemblyName`|Paramètre **String** requis.<br /><br /> Spécifie le nom court de l'assembly généré pour un projet ; ce nom est le même que celui de l'assembly cible qui est généré temporairement.  Par exemple, si un projet génère un exécutable [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] dont le nom est **WinExeAssembly.exe**, le paramètre **AssemblyName** a la valeur **WinExeAssembly**.|  
|`CompileTargetName`|Paramètre **String** requis.<br /><br /> Spécifie le nom de la cible [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] utilisée pour générer des assemblys à partir de fichiers de code source.  La valeur type pour **CompileTargetName** est **CoreCompile**.|  
|`CompileTypeName`|Paramètre **String** requis.<br /><br /> Spécifie le type de compilation exécutée par la cible spécifiée par le paramètre **CompileTargetName**.  Pour la cible **CoreCompile**, cette valeur est **Compile**.|  
|`CurrentProject`|Paramètre **String** requis.<br /><br /> Spécifie le chemin d'accès complet du fichier projet [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] pour le projet qui requiert un assembly cible temporaire.|  
|`GeneratedCodeFiles`|Paramètre **ITaskItem\[\]** facultatif.<br /><br /> Spécifie la liste des fichiers de code managé, spécifiques au langage, générés par la tâche [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md).|  
|`IntermediateOutputPath`|Paramètre **String** requis.<br /><br /> Spécifie le répertoire dans lequel l'assembly cible temporaire est généré.|  
|`MSBuildBinPath`|Paramètre **String** requis.<br /><br /> Spécifie l'emplacement de **MSBuild.exe**, requis pour compiler l'assembly cible temporaire.|  
|`ReferencePath`|Paramètre **ITaskItem\[\]** facultatif.<br /><br /> Spécifie, par le chemin d'accès et le nom du fichier, une liste d'assemblys référencés par les types compilés dans l'assembly cible temporaire.|  
|`ReferencePathTypeName`|Paramètre **String** requis.<br /><br /> Spécifie le paramètre utilisé par le paramètre de la cible de la compilation \(**CompileTargetName**\) qui spécifie la liste des références d'assemblys \(**ReferencePath**\).  La valeur appropriée est **ReferencePath**.|  
  
## Notes  
 Le premier passage de compilation du balisage, exécuté par la [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md), compile des fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] au format binaire.  Par conséquent, le compilateur a besoin d'une liste des assemblys référencés qui contiennent les types utilisés par les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].  Toutefois, si un fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] utilise un type défini dans le même projet, aucun assembly correspondant à ce projet ne sera créé tant que le projet ne sera pas généré.  Par conséquent, une référence d'assembly ne peut pas être fournie au cours du premier passage de compilation du balisage.  
  
 À la place, **MarkupCompilePass1** diffère la conversion des fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] qui contiennent des références à des types du même projet à un second passage de compilation du balisage, exécuté par la [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).  Avant l'exécution de **MarkupCompilePass2**, un assembly temporaire est généré.  Cet assembly contient les types utilisés par les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dont le passage de compilation du balisage a été différé.  Une référence à l'assembly généré est fournie à **MarkupCompilePass2** lors de son exécution afin que les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)], dont la compilation a été différée, puissent être convertis au format binaire.  
  
## Exemple  
 L'exemple suivant génère un assembly temporaire car `Page1.xaml` contient une référence à un type du même projet.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GenerateTemporaryTargetAssemblyTask">  
    <GenerateTemporaryTargetAssembly  
      AssemblyName="WPFMSBuildSample"  
      CompileTargetName="CoreCompile"  
      CompileTypeName="Compile"  
      CurrentProject="FullBuild.proj"  
      GeneratedCodeFiles="obj\debug\app.g.cs;obj\debug\Page1.g.cs;obj\debug\Page2.g.cs"  
      ReferencePath="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll"  
      IntermediateOutputPath=".\obj\debug\"  
      MSBuildBinPath="$(MSBuildBinPath)"  
      ReferencePathTypeName="ReferencePath"/>  
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