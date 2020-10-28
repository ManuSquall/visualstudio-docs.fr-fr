---
title: MarkupCompilePass2, tâche | Microsoft Docs
description: Découvrez comment MSBuild utilise la tâche MarkupCompilePass2 pour effectuer une deuxième passe de compilation du balisage sur des fichiers XAML qui référencent des types dans le même projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9efcd6fd293352dfa3396bca35953f0a76feb25
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903860"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 (tâche)

La <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> tâche effectue une deuxième passe de compilation du balisage sur les fichiers XAML qui référencent des types dans le même projet.

## <a name="task-parameters"></a>Paramètres de tâche

| Paramètre | Description |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Paramètre **booléen** facultatif.<br /><br /> Indique si la tâche doit être exécutée dans un <xref:System.AppDomain> séparé. Si ce paramètre retourne la **valeur false** , la tâche s’exécute de la même <xref:System.AppDomain> manière que MSBuild, et elle s’exécute plus rapidement. Si le paramètre retourne la **valeur true** , la tâche s’exécute dans une seconde <xref:System.AppDomain> qui est isolée de MSBuild et s’exécute plus lentement. |
| `AssembliesGeneratedDuringBuild` | Paramètre **String []** facultatif.<br /><br /> Spécifie des références à des assemblys qui changent pendant le processus de génération. Par exemple, une solution Visual Studio peut contenir un projet qui référence la sortie compilée d’un autre projet. Dans ce cas, la sortie compilée du deuxième projet peut être ajoutée à **AssembliesGeneratedDuringBuild** .<br /><br /> Remarque : **AssembliesGeneratedDuringBuild** doit contenir des références au jeu complet des assemblys générés par une solution de génération. |
| `AssemblyName` | Paramètre de **chaîne** obligatoire.<br /><br /> Spécifie le nom court de l’assembly généré pour un projet. Par exemple, si un projet génère un fichier exécutable dont le nom est *WinExeAssembly.exe* , le paramètre **AssemblyName** a la valeur **WinExeAssembly** . |
| `GeneratedBaml` | Paramètre de sortie **ITaskItem[]** facultatif.<br /><br /> Contient la liste des fichiers générés au format binaire XAML. |
| `KnownReferencePaths` | Paramètre **String []** facultatif.<br /><br /> Spécifie les références à des assemblys qui ne sont jamais modifiés pendant le processus de génération. Comprend les assemblys qui se trouvent dans le Global Assembly Cache (GAC), dans un répertoire d’installation .NET, et ainsi de suite. |
| `Language` | Paramètre de **chaîne** obligatoire.<br /><br /> Spécifie le langage managé pris en charge par le compilateur. Les options valides sont **C#** , **VB** , **JScript** et **C++** . |
| `LocalizationDirectivesToLocFile` | Paramètre de **chaîne** facultatif.<br /><br /> Spécifie comment générer des informations de localisation pour chaque fichier XAML source. Les options valides sont **None** , **CommentsOnly** et **All** . |
| `OutputPath` | Paramètre de **chaîne** obligatoire.<br /><br /> Spécifie le répertoire dans lequel les fichiers au format binaire XAML générés sont générés. |
| `OutputType` | Paramètre de **chaîne** obligatoire.<br /><br /> Spécifie le type d’assembly généré par un projet. Les options valides sont **winexe** , **exe** , **library** et **netmodule** . |
| `References` | Paramètre **ITaskItem []** facultatif.<br /><br /> Spécifie la liste des références des fichiers aux assemblys qui contiennent les types utilisés dans les fichiers XAML. Une des références correspond à l’assembly qui a été généré par la tâche <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>, qui doit être exécutée avant la tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>. |
| `RootNamespace` | Paramètre de **chaîne** facultatif.<br /><br /> Spécifie l’espace de noms racine pour les classes qui se trouvent dans le projet. **RootNamespace** est également utilisé comme espace de noms par défaut d’un fichier de code managé généré lorsque le fichier XAML correspondant n’inclut pas l' `x:Class` attribut. |
| `XAMLDebuggingInformation` | Paramètre **booléen** facultatif.<br /><br /> Quand la **valeur est true** , les informations de diagnostic sont générées et incluses dans le XAML compilé afin d’aider au débogage. |

## <a name="remarks"></a>Notes

Avant d’exécuter **MarkupCompilePass2** , vous devez générer un assembly temporaire qui contient les types utilisés par les fichiers XAML dont la passe de compilation du balisage a été différée. Pour générer l’assembly temporaire, exécutez la tâche **GenerateTemporaryTargetAssembly** .

Une référence à l’assembly temporaire généré est fournie à <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> lors de son exécution, ce qui permet aux fichiers XAML dont la compilation a été différée dans la première passe de compilation du balisage de se compiler désormais au format binaire.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> pour exécuter une deuxième passe de compilation.

```xml
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

- [Informations de référence sur MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Référence des tâches MSBuild WPF](../msbuild/wpf-msbuild-task-reference.md)
- [Référence MSBuild](../msbuild/msbuild-reference.md)
- [Référence des tâches MSBuild](../msbuild/msbuild-task-reference.md)
- [Générer une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Vue d’ensemble des applications de navigateur XAML WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
