---
title: MarkupCompilePass2, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
ms.assetid: 1d25689a-d21f-4b05-be26-95aa0ed4fd03
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 47e27dbfa221a9476488d563ae2a48235a08f769
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703448"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> effectue la première passe de compilation du balisage sur les fichiers [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] qui référencent des types dans le même projet.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Paramètre **Boolean** facultatif.<br /><br /> Spécifie si la tâche doit être exécutée dans un <xref:System.AppDomain> distinct. Si ce paramètre retourne **false**, la tâche s’exécute dans le même <xref:System.AppDomain> que [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)], et plus rapidement. Si le paramètre retourne **true**, la tâche s’exécute dans un deuxième <xref:System.AppDomain> isolé de [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)], et plus lentement.|  
|`AssembliesGeneratedDuringBuild`|Paramètre **String[]** facultatif.<br /><br /> Spécifie des références à des assemblys qui changent pendant le processus de génération. Par exemple, une solution [!INCLUDE[TLA#tla_visualstu2005](../includes/tlasharptla-visualstu2005-md.md)] peut contenir un projet qui référence la sortie compilée d’un autre projet. Dans ce cas, la sortie compilée du deuxième projet peut être ajoutée à **AssembliesGeneratedDuringBuild**.<br /><br /> Remarque : **AssembliesGeneratedDuringBuild** doit contenir des références au jeu complet des assemblys générés par une solution de génération.|  
|`AssemblyName`|Paramètre **String** obligatoire.<br /><br /> Spécifie le nom court de l’assembly généré pour un projet. Par exemple, si un projet génère un exécutable [!INCLUDE[TLA#tla_win](../includes/tlasharptla-win-md.md)] dont le nom est **WinExeAssembly.exe**, le paramètre **AssemblyName** a la valeur **WinExeAssembly**.|  
|`GeneratedBaml`|Paramètre de sortie **ITaskItem[]** facultatif.<br /><br /> Contient la liste des fichiers générés au format binaire [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)].|  
|`KnownReferencePaths`|Paramètre **String[]** facultatif.<br /><br /> Spécifie les références à des assemblys qui ne sont jamais modifiés pendant le processus de génération. Inclut les assemblys qui se trouvent dans le [!INCLUDE[TLA#tla_gac](../includes/tlasharptla-gac-md.md)], dans un répertoire d’installation [!INCLUDE[TLA#tla_netframewk](../includes/tlasharptla-netframewk-md.md)], et ainsi de suite.|  
|`Language`|Paramètre **String** obligatoire.<br /><br /> Spécifie le langage managé pris en charge par le compilateur. Les options valides sont **C#**, **VB**, **JScript** et **C++**.|  
|`LocalizationDirectivesToLocFile`|Paramètre **String** facultatif.<br /><br /> Spécifie comment générer des informations de localisation pour chaque fichier [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] source. Les options valides sont **None**, **CommentsOnly** et **All**.|  
|`OutputPath`|Paramètre **String** obligatoire.<br /><br /> Spécifie le répertoire dans lequel les fichiers au format binaire [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] sont générés.|  
|`OutputType`|Paramètre **String** obligatoire.<br /><br /> Spécifie le type d’assembly généré par un projet. Les options valides sont **winexe**, **exe**, **library** et **netmodule**.|  
|`References`|Paramètre **ITaskItem[]** facultatif.<br /><br /> Spécifie la liste des références des fichiers aux assemblys qui contiennent les types qui sont utilisés dans les fichiers [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]. Une des références correspond à l’assembly qui a été généré par la tâche <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>, qui doit être exécutée avant la tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>.|  
|`RootNamespace`|Paramètre **String** facultatif.<br /><br /> Spécifie l’espace de noms racine pour les classes qui se trouvent dans le projet. **RootNamespace** est également utilisé comme espace de noms par défaut d’un fichier de code managé généré quand le fichier [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] correspondant n’inclut pas l’attribut `x:Class`.|  
|`XAMLDebuggingInformation`|Paramètre **Boolean** facultatif.<br /><br /> Quand la valeur est **true**, des informations de diagnostic sont générées et incluses dans le [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] compilé pour faciliter le débogage.|  
  
## <a name="remarks"></a>Remarques  
 Avant d’exécuter **MarkupCompilePass2**, vous devez générer un assembly temporaire qui contient les types utilisés par les fichiers [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dont la passe de compilation du balisage a été différée. Pour générer l’assembly temporaire, exécutez la tâche **GenerateTemporaryTargetAssembly**.  
  
 Une référence à l’assembly temporaire généré est fournie à <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> lors de son exécution, ce qui permet aux fichiers [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dont la compilation a été différée lors de la première passe de compilation du balisage d’être maintenant compilés au format binaire.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> pour exécuter une deuxième passe de compilation.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur MSBuild WPF](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/wpf-msbuild-task-reference.md)   
 [Référence MSBuild](../msbuild/msbuild-reference.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)   
 [Génération d’une application WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Vue d’ensemble des applications du navigateur XAML WPF](https://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
