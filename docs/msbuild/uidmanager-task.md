---
title: UidManager, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37692c541fb2a6e9b2ccf61083dd383e56a79766
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77631521"
---
# <a name="uidmanager-task"></a>UidManager, tâche

La <xref:Microsoft.Build.Tasks.Windows.UidManager> tâche vérifie, met à jour ou supprime les identificateurs uniques (UID), afin de localiser tous les éléments XAML inclus dans les fichiers XAML source.

## <a name="task-parameters"></a>Paramètres de tâche

| Paramètre | Description |
|-------------------------| - |
| `IntermediateDirectory` | Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le répertoire utilisé pour sauvegarder les fichiers XAML source qui sont spécifiés par le paramètre **MarkupFiles** . |
| `MarkupFiles` | Paramètre **ITaskItem []** obligatoire.<br /><br /> Spécifie les fichiers XAML source à inclure pour la vérification, la mise à jour ou la suppression des UID. |
| `Task` | Paramètre de **chaîne** obligatoire.<br /><br /> Spécifie la tâche de gestion des UID à exécuter. Les options valides sont **Check**, **Update** et **Remove**. |

## <a name="example"></a>Exemple

 L’exemple suivant utilise la <xref:Microsoft.Build.Tasks.Windows.UidManager> tâche pour vérifier que les fichiers XAML source spécifiés contiennent des éléments XAML qui ont des UID appropriés.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="UidManagerTask">
    <UidManager
      Task="Check"
      MarkupFiles="Page1.xaml;Page2.xaml"
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />
  </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Informations de référence sur les tâches](../msbuild/wpf-msbuild-task-reference.md)
- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Générer une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Comment : localiser une application](/dotnet/framework/wpf/advanced/how-to-localize-an-application)