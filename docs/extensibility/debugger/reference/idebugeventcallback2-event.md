---
title: "IDebugEventCallback2::Event | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEventCallback2::Event"
helpviewer_keywords: 
  - "IDebugEventCallback2::Event"
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEventCallback2::Event
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Envoie des notifications d'événement de débogage.  
  
## Syntaxe  
  
```cpp#  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```c#  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### Paramètres  
 `pEngine`  
 \[in\]  un objet d' [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) qui représente le moteur de débogage \(DE\) qui envoie cet événement.  Un De est nécessaire pour terminer ce paramètre.  
  
 `pProcess`  
 \[in\]  un objet d' [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) qui représente le processus dans lequel l'événement se produit.  Ce paramètre est rempli par le gestionnaire de débogage de session \(SDM\).  Un De passe toujours une valeur NULL pour ce paramètre.  
  
 `pProgram`  
 \[in\]  Un objet d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente le programme où cet événement se produit.  pour la plupart des événements, ce paramètre n'est pas une valeur NULL.  
  
 `pThread`  
 \[in\]  Un objet d' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le thread dans lequel cet événement se produit.  Pour empêcher les événements, ce paramètre ne peut pas être une valeur NULL à mesure que le frame de pile est obtenu à partir de ce paramètre.  
  
 `pEvent`  
 \[in\]  un objet d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) qui représente l'événement de débogage.  
  
 `riidEvent`  
 \[in\]  GUID identifiant qui interface d'événement à obtenir à partir de le paramètre d' `pEvent` .  
  
 `dwAttrib`  
 \[in\]  Une combinaison des indicateurs d'énumération d' [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 En appelant cette méthode, le paramètre d' `dwAttrib` doit correspondre à la valeur retournée par la méthode d' [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) comme invité l'objet événement est passé dans le paramètre d' `pEvent` .  
  
 Tous les événements de débogage sont publiés de façon asynchrone, et ce, qu'un événement lui\-même soit asynchrone ou pas.  Lorsqu'un De appelle cette méthode, la valeur de retour n'indique pas si l'événement a été traité, uniquement si l'événement a été reçu.  En fait, dans la plupart des circonstances, l'événement n'a pas été géré lorsque cette méthode retourne.  
  
## Voir aussi  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)