---
title: Champ TASK_STATE_FAULTED | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_FAULTED field, Task class [.NET Framework debug engines]
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7c9b3b831e998b11c76a45831586c7ec58483e63
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276908"
---
# <a name="taskstatefaulted-field"></a>Champ TASK_STATE_FAULTED
Tâche terminée suite à une exception non gérée.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans *mscorlib.dll*)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)  
```  
  
## <a name="remarks"></a>Notes  
 Si le [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) champ contient cette valeur, le <xref:System.Threading.Tasks.Task.Status%2A> retourne de la propriété <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)