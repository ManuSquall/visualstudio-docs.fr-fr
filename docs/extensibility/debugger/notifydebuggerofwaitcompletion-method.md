---
title: Méthode de NotifyDebuggerOfWaitCompletion | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 95c510cd0b9be97c53d2026a54335b07bcd1da9f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102728"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion (méthode)
Méthode d’espace réservé utilisé en tant que point d’arrêt cible par le débogueur. Cette méthode ne doit pas être inline ou optimisé.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>Notes  
 Toutes les opérations de jointure avec une tâche doivent appeler cette méthode si leur bit de notification de débogueur est défini.  
  
## <a name="requirements"></a>Spécifications  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)