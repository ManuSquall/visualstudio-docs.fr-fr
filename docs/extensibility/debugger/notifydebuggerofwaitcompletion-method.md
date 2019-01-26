---
title: Méthode NotifyDebuggerOfWaitCompletion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 29657a85b72fa57f37a3932465b5aeb874e9a672
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012389"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Méthode NotifyDebuggerOfWaitCompletion
Méthode d’espace réservé utilisée comme cible de point d’arrêt par le débogueur. Cette méthode ne doit pas être inline ou optimisé.  
  
 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans *mscorlib.dll*)  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>Notes  
 Toutes les opérations de jointure avec une tâche doivent appeler cette méthode si leur bit de notification de débogueur est défini.  
  
## <a name="requirements"></a>Spécifications  
  
## <a name="see-also"></a>Voir aussi  
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)