---
title: "XmlPeek, tâche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: da868989d889f04966f106f2f1c1c065c4a88db6
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="xmlpeek-task"></a>Tâche XmlPeek
Retourne des valeurs telles que spécifiées par la requête XPath depuis un fichier XML.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `XmlPeek` .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Namespaces`|Paramètre `String` facultatif.<br /><br /> Spécifie les espaces de noms pour les préfixes de requête XPath.|  
|`Query`|Paramètre `String` facultatif.<br /><br /> Spécifie la requête XPath.|  
|`Result`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient les résultats retournés par cette tâche.|  
|`XmlContent`|Paramètre `String` facultatif.<br /><br /> Spécifie l’entrée XML sous forme de chaîne.|  
|`XmlInputPath`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie l’entrée XML sous forme de chemin de fichier.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)