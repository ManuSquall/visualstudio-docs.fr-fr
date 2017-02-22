---
title: "IDebugProgram2::Step | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Step"
helpviewer_keywords: 
  - "IDebugProgram2::Step"
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# IDebugProgram2::Step
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

effectue une étape.  
  
> [!NOTE]
>  Cette méthode est déconseillée.  Employez plutôt la méthode [Étape](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## Syntaxe  
  
```cpp#  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```c#  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### Paramètres  
 `pThread`  
 \[in\]  Un objet d' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le thread qui est \- pas.  
  
 `sk`  
 \[in\]  une valeur de l'énumération de [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) qui spécifie le genre d'étape.  
  
 `step`  
 \[in\]  Une valeur de l'énumération de [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) qui spécifie l'unité de l'étape \(par exemple, par l'instruction ou l'instruction\).  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Dans le cas où il y aurait toute synchronisation de threads ou communication entre les threads, les autres threads du programme doivent s'exécuter lorsqu'un thread particulier \- pas.  
  
> [!WARNING]
>  N'envoyez pas d'événement arrêtant ou un événement \(synchrone\) immédiat est [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) tout en gérant cet appel ; sinon le débogueur peut se bloquer.  
  
## Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)