---
title: MarkupCompilePass2, tâche | Microsoft Docs
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
ms.openlocfilehash: d18bc3638454e2a6b034cd2e35c3a158361a033e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633523"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 (tâche)

La <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> tâche effectue la compilation de balisage de deuxième passage sur les fichiers XAML qui font référence aux types dans le même projet.

## <a name="task-parameters"></a>Paramètres de tâche

| Paramètre | Description |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Paramètre **Boolean** optionnel.<br /><br /> Indique si la tâche doit être exécutée dans un <xref:System.AppDomain> séparé. Si ce paramètre revient **faux,** la tâche s’exécute dans le même <xref:System.AppDomain> que MSBuild, et il fonctionne plus vite. Si le paramètre revient **vrai,** la tâche s’exécute en une seconde <xref:System.AppDomain> qui est isolée de MSBuild et fonctionne plus lentement. |
| `AssembliesGeneratedDuringBuild` | Paramètre **de chaîne en** option.<br /><br /> Spécifie des références à des assemblys qui changent pendant le processus de génération. Par exemple, une solution Visual Studio peut contenir un projet qui référence la sortie compilée d’un autre projet. Dans ce cas, la sortie compilée du deuxième projet peut être ajoutée à **AssembliesGeneratedDuringBuild**.<br /><br /> Remarque : **AssembliesGeneratedDuringBuild** doit contenir des références au jeu complet des assemblys générés par une solution de génération. |
| `AssemblyName` | Paramètre **de chaîne** requis.<br /><br /> Spécifie le nom court de l’assembly généré pour un projet. Par exemple, si un projet génère un exécutant dont le nom est *WinExeAssembly.exe*, le paramètre **AssemblyName** a une valeur de **WinExeAssembly**. |
| `GeneratedBaml` | Paramètre de sortie **ITaskItem[]** facultatif.<br /><br /> Contient la liste des fichiers générés dans le format binaire XAML. |
| `KnownReferencePaths` | Paramètre **de chaîne en** option.<br /><br /> Spécifie les références à des assemblys qui ne sont jamais modifiés pendant le processus de génération. Inclut les assemblages situés dans le cache d’assemblage global (GAC), dans un répertoire d’installation .NET, et ainsi de suite. |
| `Language` | Paramètre **de chaîne** requis.<br /><br /> Spécifie le langage managé pris en charge par le compilateur. Les options valides sont **C#**, **VB**, **JScript** et **C++**. |
| `LocalizationDirectivesToLocFile` | Paramètre **de chaîne** facultatif.<br /><br /> Précise comment générer des informations de localisation pour chaque fichier XAML source. Les options valides sont **None**, **CommentsOnly** et **All**. |
| `OutputPath` | Paramètre **de chaîne** requis.<br /><br /> Spécifie l’annuaire dans lequel les fichiers de format binaire XAML générés sont générés. |
| `OutputType` | Paramètre **de chaîne** requis.<br /><br /> Spécifie le type d’assembly généré par un projet. Les options valides sont **winexe**, **exe**, **library** et **netmodule**. |
| `References` | Paramètre **ITaskItem[]** en option.<br /><br /> Spécifie la liste des références des fichiers aux assemblages qui contiennent les types qui sont utilisés dans les fichiers XAML. Une des références correspond à l’assembly qui a été généré par la tâche <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>, qui doit être exécutée avant la tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>. |
| `RootNamespace` | Paramètre **de chaîne** facultatif.<br /><br /> Spécifie l’espace de noms racine pour les classes qui se trouvent dans le projet. **RootNamespace** est également utilisé comme l’espace nom par défaut d’un fichier `x:Class` de code géré généré lorsque le fichier XAML correspondant n’inclut pas l’attribut. |
| `XAMLDebuggingInformation` | Paramètre **Boolean** optionnel.<br /><br /> Lorsque **c’est vrai,** l’information diagnostique est générée et incluse dans le XAML compilé afin d’aider à débogage. |

## <a name="remarks"></a>Notes 

Avant d’exécuter **MarkupCompilePass2**, vous devez générer un assemblage temporaire qui contient les types qui sont utilisés par les fichiers XAML dont le laissez-passer de compilation de balisage ont été reportés. Pour générer l’assembly temporaire, exécutez la tâche **GenerateTemporaryTargetAssembly**.

Une référence à l’assemblage <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> temporaire généré est fournie au moment où elle s’exécute, permettant aux fichiers XAML dont la compilation a été reportée dans le premier passage de compilation de balisage d’être maintenant compilés au format binaire.

## <a name="example"></a> Exemple

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

- [WPF MSBuild référence](../msbuild/wpf-msbuild-reference.md)
- [Référence de tâche WPF MSBuild](../msbuild/wpf-msbuild-task-reference.md)
- [Référence MSBuild](../msbuild/msbuild-reference.md)
- [Référence de tâche MSBuild](../msbuild/msbuild-task-reference.md)
- [Générer une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Vue d’ensemble des applications du navigateur XAML WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
