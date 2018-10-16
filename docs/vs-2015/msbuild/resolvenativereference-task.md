---
title: ResolveNativeReference, tâche | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a874055e5af1a0aafd48296a99f12a83d56369f8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281305"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Résout des références natives. Implémente la classe <xref:Microsoft.Build.Tasks.ResolveNativeReference>. Cette classe prend en charge l’infrastructure .NET Framework et n’est pas destinée à être directement utilisée à partir de votre code.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
 Le tableau ci-dessous décrit les paramètres de la tâche `ResolveNativeReference`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AdditionalSearchPaths`|[String] obligatoire (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->)`[]` paramètre.<br /><br /> Obtient ou définit les chemins de recherche pour la résolution des identités d’assembly des références natives.|  
|`ContainedComComponents`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les composants COM de l’assembly natif.|  
|`ContainedLooseEtcFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les fichiers Etc libres répertoriés dans le manifeste natif.|  
|`ContainedLooseTlbFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les fichiers .tlb libres de l’assembly natif.|  
|`ContainedPrerequisiteAssemblies`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les assemblys qui doivent être présents pour permettre l’utilisation du manifeste.|  
|`ContainedTypeLibraries`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les bibliothèques de types de l’assembly natif.|  
|`ContainingReferenceFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les fichiers de référence.|  
|`NativeReferences`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Obtient ou définit les références d’assemblys natifs Win32.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)



