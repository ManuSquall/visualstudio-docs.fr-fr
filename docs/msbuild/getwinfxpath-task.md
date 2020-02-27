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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633965"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath, tâche

La tâche <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> retourne le répertoire du Runtime .NET actuel.

## <a name="task-parameters"></a>Paramètres de tâche

| Paramètre | Description |
|-------------------| - |
| `WinFXPath` | Paramètre de sortie **String** facultatif.<br /><br /> Spécifie le chemin d’accès réel au Runtime .NET. |
| `WinFXNativePath` | Paramètre **String** obligatoire.<br /><br /> Spécifie le chemin d’accès au Runtime .NET natif. |
| `WinFXWowPath` | Paramètre **String** obligatoire.<br /><br /> Spécifie le chemin d’accès aux assemblys .NET dans le module **Windows sur windows** 32 bits sur les systèmes 64 bits. |

## <a name="remarks"></a>Notes

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
- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Générer une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
