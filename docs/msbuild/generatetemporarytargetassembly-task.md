---
title: "GenerateTemporaryTargetAssembly, tâche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- build process [WPF MSBuild], XAML page refers to a locally declared type
- GenerateTemporaryTargetAssembly task [WPF MSBuild]
- GenerateTemporaryTargetAssembly task [WPF MSBuild], parameters
- creating an assembly [WPF MSBuild], XAML page refers to a locally declared type
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: dd570e81198f63a22f196e04a5d0a321fc3c6d21
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly, tâche
La tâche <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> génère un assembly si au moins une page [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] dans un projet fait référence à un type déclaré localement dans ce projet. L’assembly généré est supprimé une fois le processus de génération terminé, ou en cas d’échec du processus de génération.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AssemblyName`|Paramètre **String** obligatoire.<br /><br /> Spécifie le nom court de l’assembly généré pour un projet. Il s’agit aussi du nom de l’assembly cible généré temporairement. Par exemple, si un projet génère un exécutable [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] dont le nom est **WinExeAssembly.exe**, le paramètre **AssemblyName** a la valeur **WinExeAssembly**.|  
|`CompileTargetName`|Paramètre **String** obligatoire.<br /><br /> Spécifie le nom de la cible [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] utilisée pour générer des assemblys à partir de fichiers de code source. La valeur par défaut de **CompileTargetName** est **CoreCompile**.|  
|`CompileTypeName`|Paramètre **String** obligatoire.<br /><br /> Spécifie le type de compilation exécutée par la cible spécifiée par le paramètre **CompileTargetName**. Pour la cible **CoreCompile**, cette valeur est **Compile**.|  
|`CurrentProject`|Paramètre **String** obligatoire.<br /><br /> Spécifie le chemin complet du fichier projet [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] pour le projet qui nécessite un assembly cible temporaire.|  
|`GeneratedCodeFiles`|Paramètre **ITaskItem[]** facultatif.<br /><br /> Spécifie la liste des fichiers de code managé propres au langage générés par la tâche [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md).|  
|`IntermediateOutputPath`|Paramètre **String** obligatoire.<br /><br /> Spécifie le répertoire où l’assembly cible temporaire est généré.|  
|`MSBuildBinPath`|Paramètre **String** obligatoire.<br /><br /> Spécifie l’emplacement de **MSBuild.exe**, qui est obligatoire pour compiler l’assembly cible temporaire.|  
|`ReferencePath`|Paramètre **ITaskItem[]** facultatif.<br /><br /> Spécifie une liste d’assemblys, par chemin et nom de fichier, qui sont référencés par les types qui sont compilés dans l’assembly cible temporaire.|  
|`ReferencePathTypeName`|Paramètre **String** obligatoire.<br /><br /> Spécifie le paramètre utilisé par le paramètre de cible de compilation (**CompileTargetName**) qui spécifie la liste des références d’assembly (**ReferencePath**). La valeur appropriée est **ReferencePath**.|  
  
## <a name="remarks"></a>Notes  
 La première passe de compilation du balisage, exécutée par [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md), compile les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] au format binaire. Ainsi, le compilateur a besoin d’une liste des assemblys référencés qui contiennent les types utilisés par les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. Toutefois, si un fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] utilise un type qui est défini dans le même projet, un assembly correspondant à ce projet est créé uniquement quand le projet est généré. Ainsi, une référence d’assembly ne peut pas être fournie pendant la première passe de compilation du balisage.  
  
 Au lieu de cela, **MarkupCompilePass1** diffère la conversion des fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] qui contiennent des références à des types dans le même projet à une deuxième passe de compilation du balisage, qui est exécutée par [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md). Avant l’exécution de **MarkupCompilePass2**, un assembly temporaire est généré. Cet assembly contient les types qui sont utilisés par les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dont la passe de compilation du balisage a été différée. Une référence à l’assembly généré est fournie à **MarkupCompilePass2** quand elle s’exécute, pour permettre la conversion au format binaire des fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dont la compilation a été différée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère un assembly temporaire, car `Page1.xaml` contient une référence à un type qui est dans le même projet.  
  
```xml  
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
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur MSBuild WPF](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/wpf-msbuild-task-reference.md)   
 [Référence MSBuild](../msbuild/msbuild-reference.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)   
 [Génération d’une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [Vue d’ensemble des applications du navigateur XAML WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)