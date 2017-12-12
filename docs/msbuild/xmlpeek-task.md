---
title: "XmlPeek, tâche | Microsoft Docs"
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
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 7238e549011d5f80ce2c8f006f56f6bb0f2de58d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
  
## <a name="remarks"></a>Remarques  
 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches MSBuild](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)