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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93b3c571d8c68eee8ee00475fad8bda2b5b2ec65
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989128"
---
# <a name="uidmanager-task"></a>UidManager, tâche
La tâche <xref:Microsoft.Build.Tasks.Windows.UidManager> vérifie, met à jour ou supprime les identificateurs uniques (UID) pour localiser tous les éléments [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] inclus dans les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] sources.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
  
| Paramètre | Description |
|-------------------------| - |
| `IntermediateDirectory` | Paramètre **String** facultatif.<br /><br /> Spécifie le répertoire utilisé pour sauvegarder les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] sources spécifiés par le paramètre **MarkupFiles**. |
| `MarkupFiles` | Paramètre **ITaskItem[]** obligatoire.<br /><br /> Spécifie les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] sources à inclure pour la vérification, la mise à jour ou la suppression des UID. |
| `Task` | Paramètre **String** obligatoire.<br /><br /> Spécifie la tâche de gestion des UID à exécuter. Les options valides sont **Check**, **Update** et **Remove**. |
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la tâche <xref:Microsoft.Build.Tasks.Windows.UidManager> pour vérifier si les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] sources spécifiés contiennent des éléments [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] avec des UID appropriés.  
  
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
 [Informations de référence sur MSBuild WPF](../msbuild/wpf-msbuild-reference.md)   
 [Informations de référence sur les tâches](../msbuild/wpf-msbuild-task-reference.md)   
 [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)   
 [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)   
 [Générer une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [Guide pratique pour localiser une application](/dotnet/framework/wpf/advanced/how-to-localize-an-application)