---
title: Champ TASK_STATE_CANCELED | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 54e0b95084bd685d5bc4b025f777c82b0ab1381f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162240"
---
# <a name="task_state_canceled-field"></a>Champ TASK_STATE_CANCELED
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La tâche a été annulée avant d’atteindre l’État en cours d’exécution, ou elle a reconnu son annulation et s’est terminée sans exception.  
  
 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (en mscorlib.dll)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne à partir de la .NET Framework, la syntaxe suivante est fournie en Common Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)  
```  
  
## <a name="remarks"></a>Notes  
 Si le champ [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contient cette valeur, la <xref:System.Threading.Tasks.Task.Status%2A> propriété retourne <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)
