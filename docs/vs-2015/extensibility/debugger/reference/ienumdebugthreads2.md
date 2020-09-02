---
title: IEnumDebugThreads2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97bc8383f990f6c0c35a402f2ab36b2595d82a9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147685"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ce interfac énumère les threads qui s’exécutent dans la session de débogage actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour représenter une liste de threads dans un programme.  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 Appelez [enumthreads,](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) pour obtenir cette interface représentant une liste de tous les threads dans tous les programmes en cours d’exécution dans un processus. Appelez [enumthreads,](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) pour obtenir cette interface représentant une liste de threads s’exécutant dans un programme.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugThreads2` .  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Récupère un nombre spécifié de threads dans la séquence d’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Ignore un nombre spécifié de threads dans une séquence d’énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Réinitialise une séquence d'énumération.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que le même état d’énumération actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Obtient le nombre de threads dans un énumérateur.|  
  
## <a name="remarks"></a>Notes  
 Visual Studio obtient généralement cette interface pour mettre à jour la fenêtre **Threads** et pour obtenir le premier thread de la liste, afin d’appeler [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)et [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Enumthreads,](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [Enumthreads,](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Première](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Pouvoir](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
