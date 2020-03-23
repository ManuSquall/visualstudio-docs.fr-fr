---
title: GetWinFXPath, tâche | Microsoft Docs
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
ms.openlocfilehash: ab8e15cef722e935dde322072f6834ba00be8bc5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633965"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath, tâche

La <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> tâche renvoie le répertoire de l’actuel .NET runtime.

## <a name="task-parameters"></a>Paramètres de tâche

| Paramètre | Description |
|-------------------| - |
| `WinFXPath` | Paramètre de sortie **de chaîne** facultatif.<br /><br /> Spécifie le vrai chemin vers le runtime .NET. |
| `WinFXNativePath` | Paramètre **de chaîne** requis.<br /><br /> Spécifie le chemin vers le runtime natif .NET. |
| `WinFXWowPath` | Paramètre **de chaîne** requis.<br /><br /> Spécifie le chemin vers les assemblages .NET dans le module **Windows 32 bits sur Windows** sur les systèmes 64 bits. |

## <a name="remarks"></a>Notes 

 Si la tâche <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> s’exécute sur un processeur 64 bits, le paramètre **WinFXPath** a comme valeur le chemin stocké dans le paramètre **WinFXWowPath** ; sinon, le paramètre **WinFXPath** a comme valeur le chemin stocké dans le paramètre **WinFXNativePath**.

## <a name="example"></a> Exemple

 L’exemple suivant montre comment utiliser la tâche **GetWinFXPath** pour détecter le chemin natif vers le temps d’exécution .NET.

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

- [WPF MSBuild référence](../msbuild/wpf-msbuild-reference.md)
- [Informations de référence sur les tâches](../msbuild/wpf-msbuild-task-reference.md)
- [Référence MSBuild](../msbuild/msbuild-reference.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Générer une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
