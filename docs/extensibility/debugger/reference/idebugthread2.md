---
title: IDebugThread2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 363f2aa684d45a07978c70b222af7f35ea2b05d3
ms.lasthandoff: 02/22/2017

---
# <a name="idebugthread2"></a>IDebugThread2
Cette interface représente un thread en cours d’exécution dans un programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugThread2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes relatives à l’attention des implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour représenter un thread d’exécution dans un seul programme.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appelez [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) pour obtenir cette interface qui représente le thread actif.  
  
 Cette interface est également utilisée pour créer une demande de point d’arrêt (voir [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).  
  
 Cette interface est également renvoyée lors de la résolution d’un point d’arrêt limite ou erreur (voir [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) et [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugThread2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Récupère une liste des frames de pile de ce thread.|  
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Obtient le nom du thread.|  
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Définit le nom du thread.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Obtient le programme dans lequel un thread s’exécute.|  
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Détermine si l’instruction suivante peut être définie dans le contexte de frame et le code de pile donné.|  
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Définit l’instruction suivante dans le contexte de frame et le code de pile donné.|  
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Obtient l’identificateur du thread du système.|  
|[Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Interrompt un thread.|  
|[Reprise](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Reprend un thread.|  
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Obtient les propriétés qui décrivent un thread.|  
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Obtient le thread logique associé à ce thread physique.|  
  
## <a name="remarks"></a>Remarques  
 Un seul thread physique pouvant s’exécuter dans plusieurs programmes, plusieurs `IDebugThread2` à partir de plusieurs programmes peuvent représenter le même thread physique.  
  
 Lorsqu’un point d’arrêt ou une exception se produit, un événement est envoyé en appelant [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Un des arguments de cette méthode est un `IDebugThread2` interface représentant le thread actuel. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) est utilisée pour obtenir le [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interface pour le frame de pile actuel.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
