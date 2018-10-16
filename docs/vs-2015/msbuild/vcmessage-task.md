---
title: VCMessage, tâche | Microsoft Docs
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
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (Visual C++))
- MSBuild (Visual C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f592160aae4fc1382b36c7331175eb6ab20d3fdc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243930"
---
# <a name="vcmessage-task"></a>VCMessage, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Journalise les messages d’avertissement et d’erreur lors de la génération.  
  
## <a name="remarks"></a>Notes  
 Cette tâche permet d’implémenter MSBuild pour Visual C++ et n’est pas destinée à être appelée par l’utilisateur. Pour plus d'informations, consultez <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche **VCMessage**.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**Arguments**|Paramètre **String** facultatif.<br /><br /> Liste de messages (séparés par des points-virgules) devant être affichée.|  
|**Code**|Paramètre **String** obligatoire.<br /><br /> Numéro d’erreur qui qualifie le message.|  
|**Type**|Paramètre **String** facultatif.<br /><br /> Spécifie le type de message à émettre. Spécifie soit `"Warning"` pour émettre un message d’avertissement, soit `"Error"` pour émettre un message d’erreur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)



