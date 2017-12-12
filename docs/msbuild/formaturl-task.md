---
title: "FormatUrl, tâche | Microsoft Docs"
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
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: ef3882e29a1fb2b65d0fba454ab1c0f45a62fc02
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="formaturl-task"></a>FormatUrl, tâche
Convertit une URL en URL au format correct.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `FormatUrl` .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`InputUrl`|Paramètre `String` facultatif.<br /><br /> Spécifie l’URL à mettre en forme.|  
|`OutputUrl`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie l’URL mise en forme.|  
  
## <a name="remarks"></a>Remarques  
 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches MSBuild](../msbuild/msbuild-tasks.md)   
 [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)