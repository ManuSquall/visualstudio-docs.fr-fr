---
title: "IDebugPortEvents2::Event | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEvents2::Event"
helpviewer_keywords: 
  - "IDebugPortEvents2::Event"
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# IDebugPortEvents2::Event
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette méthode envoie les événements qui signifient la création et la destruction des processus et des programmes sur un port.  
  
## Syntaxe  
  
```cpp#  
HRESULT Event(  
   IDebugCoreServer2* pServer,  
   IDebugPort2*       pPort,  
   IDebugProcess2*    pProcess,  
   IDebugProgram2*    pProgram,  
   IDebugEvent2*      pEvent,  
   REFIID             riidEvent  
);  
```  
  
```c#  
int Event(  
   IDebugCoreServer2 pServer,   
   IDebugPort2       pPort,   
   IDebugProcess2    pProcess,   
   IDebugProgram2    pProgram,   
   IDebugEvent2      pEvent,   
   ref Guid          riidEvent  
);  
```  
  
#### Paramètres  
 `pMachine`  
 \[in\]  Un objet d' [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) qui représente le serveur de débogage \(qu'un pour chaque instance de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]\) dans lequel l'événement s'est produit.  
  
 `pPort`  
 \[in\]  un objet d' [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) qui représente le port dans lequel l'événement s'est produit.  
  
 `pProcess`  
 \[in\]  un objet d' [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) qui représente le processus dans lequel l'événement s'est produit.  
  
 `pProgram`  
 \[in\]  un objet d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente le programme dans lequel l'événement s'est produit.  
  
 `pEvent`  
 \[in\]  un objet d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) qui identifie l'événement.  Les événements possibles :  
  
-   [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)  
  
-   [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)  
  
-   [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
-   [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)  
  
 `riidEvent`  
 \[in\]  Le GUID de l'événement.  Étant donné que l'événement est casté à [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) avant d'appeler cette méthode, cet identificateur le plus facile pour déterminer l'événement est envoyé.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)