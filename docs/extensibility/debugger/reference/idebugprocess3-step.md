---
title: "IDebugProcess3::Step | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::Step"
helpviewer_keywords: 
  - "IDebugProcess3::Step"
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess3::Step
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Provoque le processus à l'instruction ou l'instruction d'une étape.  
  
> [!NOTE]
>  Cette méthode doit être utilisée à la place d' [Étape](../../../extensibility/debugger/reference/idebugprogram2-step.md).  
  
## Syntaxe  
  
```cpp  
HRESULT Step(  
   IDebugThread2* pThread,  
   STEPKIND       sk,  
   STEPUNIT       step,  
);  
```  
  
```c#  
int Step(  
   IDebugThread2 pThread,   
   enum_STEPKIND sk,   
   enum_STEPUNIT step  
);  
```  
  
#### Paramètres  
 `pThread`  
 \[in\]  Un objet d' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) représentant le thread qui est \- pas.  
  
 `sk`  
 \[in\]  L'une des valeurs de [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) .  
  
 `step`  
 \[in\]  L'une des valeurs de [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon retourne un code d'erreur.  
  
## Notes  
 Dans le cas où il y aurait toute synchronisation de threads ou communication entre les threads, d'autres threads dans le processus doivent s'exécuter lorsqu'un thread particulier \- pas.  
  
 **Avertissement** n'envoient pas d'événement arrêtant ou un événement \(synchrone\) immédiat est [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) tout en gérant cet appel ; sinon le débogueur peut se bloquer.  
  
## Voir aussi  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)