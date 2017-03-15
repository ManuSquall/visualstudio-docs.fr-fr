---
title: "IDebugProgram2::Continue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Continue"
helpviewer_keywords: 
  - "IDebugProgram2::Continue"
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProgram2::Continue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Continue de s'exécuter ce programme d'un état arrêté.  Tout état précédent de exécution \(par exemple une étape\) est conservé, et le démarrage du programme qui s'exécute à nouveau.  
  
> [!NOTE]
>  Cette méthode est déconseillée.  Employez plutôt la méthode [Continuer](../../../extensibility/debugger/reference/idebugprocess3-continue.md).  
  
## Syntaxe  
  
```cpp#  
HRESULT Continue(   
   IDebugThread2* pThread  
);  
```  
  
```c#  
int Continue(   
   IDebugThread2 pThread  
);  
```  
  
#### Paramètres  
 `pThread`  
 \[in\]  un objet d' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le thread.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode est appelée sur ce programme quel que soit le nombre programmes sont débogué, ou le programme a généré l'événement arrêtant.  L'implémentation doit conserver l'état précédent de exécution \(par exemple une étape\) et reprendre l'exécution comme s'il n'avait jamais interrompu avant de compléter son exécution antérieure.  Autrement dit, si un thread dans ce programme faisait a étape\-au\-dessus d'opération et a été arrêté car un autre programme arrêté, puis cette méthode a été appelé, le programme doit effectuer l'origine étape\-au\-dessus de l'opération.  
  
> [!WARNING]
>  N'envoyez pas d'événement arrêtant ou un événement \(synchrone\) immédiat est [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) tout en gérant cet appel ; sinon le débogueur peut se bloquer.  
  
## Voir aussi  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)