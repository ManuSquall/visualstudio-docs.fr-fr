---
title: Champ TASK_STATE_RAN_TO_COMPLETION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_RAN_TO_COMPLETION field, Task class [.NET Framework debug engines]
ms.assetid: 0f4830af-fe0c-4141-b768-817f4e426b8c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea3a68237b82873cc4c6646957832beb8880dcac
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001371"
---
# <a name="taskstaterantocompletion-field"></a>Champ TASK_STATE_RAN_TO_COMPLETION
L’exécution de la tâche s’est terminée avec succès.  
  
 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans *mscorlib.dll*)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
.field static assembly literal int32 TASK_STATE_RAN_TO_COMPLETION = int32(0x02000000)  
```  
  
## <a name="remarks"></a>Notes  
 Si le [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) champ contient cette valeur, le <xref:System.Threading.Tasks.Task.Status%2A> retourne de la propriété <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)