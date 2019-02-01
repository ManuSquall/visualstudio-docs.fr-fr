---
title: XmlPeek, tâche | Microsoft Docs
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
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fc39cde1a332e925f998a67ed261346320f18a3c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54787793"
---
# <a name="xmlpeek-task"></a>Tâche XmlPeek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
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
