---
title: GenerateTemporaryTargetAssembly, tâche | Microsoft Docs
description: Utilisez la tâche MSBuild GenerateTemporaryTargetAssembly pour générer un assembly si un projet fait référence à un type déclaré localement.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f4a41a5cbecea69d4843cbd70479a604f91b2218
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914736"
---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly, tâche

La <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> tâche génère un assembly si au moins une page XAML d’un projet fait référence à un type déclaré localement dans ce projet. L’assembly généré est supprimé une fois le processus de génération terminé, ou en cas d’échec du processus de génération.

## <a name="task-parameters"></a>Paramètres de tâche

| Paramètre | Description |
|--------------------------| - |
| `AssemblyName` | Paramètre de **chaîne** obligatoire.<br /><br /> Spécifie le nom court de l’assembly généré pour un projet. Il s’agit aussi du nom de l’assembly cible généré temporairement. Par exemple, si un projet génère un fichier exécutable Windows dont le nom est *WinExeAssembly.exe*, le paramètre **AssemblyName** a la valeur **WinExeAssembly**. |
| `CompileTargetName` | Paramètre de **chaîne** obligatoire.<br /><br /> Spécifie le nom de la cible MSBuild utilisée pour générer des assemblys à partir de fichiers de code source. La valeur par défaut de **CompileTargetName** est **CoreCompile**. |
| `CompileTypeName` | Paramètre de **chaîne** obligatoire.<br /><br /> Spécifie le type de compilation exécutée par la cible spécifiée par le paramètre **CompileTargetName**. Pour la cible **CoreCompile**, cette valeur est **Compile**. |
| `CurrentProject` | Paramètre de **chaîne** obligatoire.<br /><br /> Spécifie le chemin d’accès complet du fichier projet MSBuild pour le projet qui requiert un assembly cible temporaire. |
| `GeneratedCodeFiles` | Paramètre **ITaskItem []** facultatif.<br /><br /> Spécifie la liste des fichiers de code managé propres au langage générés par la tâche [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md). |
| `IntermediateOutputPath` | Paramètre de **chaîne** obligatoire.<br /><br /> Spécifie le répertoire où l’assembly cible temporaire est généré. |
| `MSBuildBinPath` | Paramètre de **chaîne** obligatoire.<br /><br /> Spécifie l’emplacement de *MSBuild.exe*, qui est obligatoire pour compiler l’assembly cible temporaire. |
| `ReferencePath` | Paramètre **ITaskItem []** facultatif.<br /><br /> Spécifie une liste d’assemblys, par chemin et nom de fichier, qui sont référencés par les types qui sont compilés dans l’assembly cible temporaire. |
| `ReferencePathTypeName` | Paramètre de **chaîne** obligatoire.<br /><br /> Spécifie le paramètre utilisé par le paramètre de cible de compilation (**CompileTargetName**) qui spécifie la liste des références d’assembly (**ReferencePath**). La valeur appropriée est **ReferencePath**. |

## <a name="remarks"></a>Notes

La première passe de compilation du balisage, qui est exécutée par [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md), compile les fichiers XAML au format binaire. Par conséquent, le compilateur a besoin d’une liste des assemblys référencés qui contiennent les types utilisés par les fichiers XAML. Toutefois, si un fichier XAML utilise un type défini dans le même projet, un assembly correspondant pour ce projet n’est pas créé tant que le projet n’est pas généré. Ainsi, une référence d’assembly ne peut pas être fournie pendant la première passe de compilation du balisage.

Au lieu de cela, **MarkupCompilePass1** diffère la conversion des fichiers XAML qui contiennent des références à des types dans le même projet à une deuxième passe de compilation du balisage, qui est exécutée par le [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md). Avant l’exécution de **MarkupCompilePass2**, un assembly temporaire est généré. Cet assembly contient les types utilisés par les fichiers XAML dont la passe de compilation du balisage a été différée. Une référence à l’assembly généré est fournie à **MarkupCompilePass2** lorsqu’il s’exécute pour permettre la conversion des fichiers XAML de compilation différée au format binaire.

## <a name="example"></a>Exemple

L’exemple suivant génère un assembly temporaire, car *Page1.xaml* contient une référence à un type qui est dans le même projet.

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

- [Informations de référence sur MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Informations de référence sur les tâches](../msbuild/wpf-msbuild-task-reference.md)
- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Générer une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Vue d’ensemble des applications de navigateur XAML WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
