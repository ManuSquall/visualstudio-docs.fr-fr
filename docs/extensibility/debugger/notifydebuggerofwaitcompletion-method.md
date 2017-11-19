---
title: "Méthode de NotifyDebuggerOfWaitCompletion | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5bfd605665627bcc9269f9225acb7d2e12418ab4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion (méthode)
Méthode d’espace réservé utilisé en tant que point d’arrêt cible par le débogueur. Cette méthode ne doit pas être inline ou optimisé.  
  
 **Namespace :**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>Remarques  
 Toutes les opérations de jointure avec une tâche doivent appeler cette méthode si leur bit de notification de débogueur est défini.  
  
## <a name="requirements"></a>Spécifications  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)