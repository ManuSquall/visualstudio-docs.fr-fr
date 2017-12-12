---
title: "ResolveNonMSBuildProjectOutput, tâche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 82928797c912aac24d41d63d865e575ea90c013e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>Tâche ResolveNonMSBuildProjectOutput
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
 [Tâches MSBuild](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)