---
title: GetWinFXPath, tâche | Microsoft Docs
description: Découvrez comment utiliser la tâche GetWinFXPath MSBuild, qui retourne le répertoire du Runtime .NET actuel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- getting the directory of the current .NET Framework runtime [WPF MSBuild]
- GetWinFXPath task [WPF MSBuild], parameters
- GetWinFXPath task [WPF MSBuild]
- obtaining the path to the current .NET Framework runtime [WPF MSBuild]
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 820ca103d88cde941fe558e59ed1c78622adccd4
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436770"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath, tâche

La <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> tâche retourne le répertoire du Runtime .net actuel.

## <a name="task-parameters"></a>Paramètres de tâche

| Paramètre | Description |
|-------------------| - |
| `WinFXPath` | Paramètre de sortie de **chaîne** facultatif.<br /><br /> Spécifie le chemin d’accès réel au Runtime .NET. |
| `WinFXNativePath` | Paramètre de **chaîne** obligatoire.<br /><br /> Spécifie le chemin d’accès au Runtime .NET natif. |
| `WinFXWowPath` | Paramètre de **chaîne** obligatoire.<br /><br /> Spécifie le chemin d’accès aux assemblys .NET dans le module **Windows sur windows** 32 bits sur les systèmes 64 bits. |

## <a name="remarks"></a>Remarques

 Si la tâche <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> s’exécute sur un processeur 64 bits, le paramètre **WinFXPath** a comme valeur le chemin stocké dans le paramètre **WinFXWowPath** ; sinon, le paramètre **WinFXPath** a comme valeur le chemin stocké dans le paramètre **WinFXNativePath**.

## <a name="example"></a>Exemple

 L’exemple suivant montre comment utiliser la tâche **GetWinFXPath** pour détecter le chemin d’accès natif au Runtime .net.

```xml
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

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Informations de référence sur les tâches](../msbuild/wpf-msbuild-task-reference.md)
- [Référence MSBuild](../msbuild/msbuild-reference.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Générer une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
