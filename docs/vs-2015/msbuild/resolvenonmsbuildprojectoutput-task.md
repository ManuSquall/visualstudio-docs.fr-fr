---
title: ResolveNonMSBuildProjectOutput, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ca4d32d0af5d1db83ed0676171aa77db3ed14fec
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54795332"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>Tâche ResolveNonMSBuildProjectOutput
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Détermine les fichiers de sortie des références de projet non-MSBuild.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `ResolveNonMSBuildProjectOutput` .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`PreresolvedProjectOutputs`|Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne XML contenant les sorties de projet résolues.|  
|`ProjectReferences`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les références de projet.|  
|`ResolvedOutputPaths`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient la liste des chemins des références résolues (et conserve les attributs des références de projet d’origine).|  
|`UnresolvedProjectReferences`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient la liste des éléments de référence de projet qui n’ont pas pu être résolus à l’aide de la liste prérésolue des sorties.<br /><br /> Étant donné que Visual Studio prérésout uniquement les projets non MSBuild, cela signifie que les références de projet de cette liste sont au format MSBuild.|  
  
## <a name="remarks"></a>Remarques  
 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)
