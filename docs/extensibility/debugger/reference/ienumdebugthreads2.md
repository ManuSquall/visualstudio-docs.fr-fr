---
title: IEnumDebugThreads2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugThreads2
helpviewer_keywords: IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ca4fedeb7e52fff627a8fab9e100c0a99792f1c6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Cette interfac énumère les threads en cours d’exécution dans la session de débogage en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour représenter une liste de threads dans un programme.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appelez [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) pour obtenir cette interface qui représente une liste de tous les threads dans tous les programmes en cours d’exécution dans un processus. Appelez [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) pour obtenir cette interface qui représente une liste de threads en cours d’exécution dans un programme.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugThreads2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Récupère un nombre spécifié de threads dans la séquence d’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Ignore un nombre spécifié de threads dans une séquence d’énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Réinitialise la séquence d’énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que celui en cours.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Obtient le nombre de threads dans un énumérateur.|  
  
## <a name="remarks"></a>Remarques  
 Visual Studio obtient généralement cette interface pour mettre à jour le **Threads** fenêtre ainsi que pour obtenir le premier thread de la liste, afin d’appeler [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [continuer](../../../extensibility/debugger/reference/idebugprocess3-continue.md), et [Étape](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Étape](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Continuer](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Exécuter](../../../extensibility/debugger/reference/idebugprocess3-execute.md)