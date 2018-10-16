---
title: UidManager, tâche | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa51ddb8f2cf6e200b7313069fca3ee6db3ebcf3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208063"
---
# <a name="uidmanager-task"></a>UidManager, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
La tâche <xref:Microsoft.Build.Tasks.Windows.UidManager> vérifie, met à jour ou supprime les identificateurs uniques (UID) pour localiser tous les éléments [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] inclus dans les fichiers [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] sources.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`IntermediateDirectory`|Paramètre **String** facultatif.<br /><br /> Spécifie le répertoire utilisé pour sauvegarder les fichiers [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] sources spécifiés par le paramètre **MarkupFiles**.|  
|`MarkupFiles`|Paramètre **ITaskItem[]** obligatoire.<br /><br /> Spécifie les fichiers [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] sources à inclure pour la vérification, la mise à jour ou la suppression des UID.|  
|`Task`|Paramètre **String** obligatoire.<br /><br /> Spécifie la tâche de gestion des UID à exécuter. Les options valides sont **Check**, **Update** et **Remove**.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la tâche <xref:Microsoft.Build.Tasks.Windows.UidManager> pour vérifier si les fichiers [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] sources spécifiés contiennent des éléments [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] avec des UID appropriés.  
  
```  
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
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/wpf-msbuild-task-reference.md)   
 [Référence MSBuild](../msbuild/msbuild-reference.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)   
 [Génération d’une application WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Guide pratique pour localiser une application](http://msdn.microsoft.com/library/5001227e-9326-48a4-9dcd-ba1b89ee6653)



