---
title: "IDebugProcess3::Continue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::Continue"
helpviewer_keywords: 
  - "IDebugProcess3::Continue"
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugProcess3::Continue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Continue de s'exécuter ce processus consistant à l'état arrêté.  Tout état précédent de exécution \(par exemple une étape\) est conservé, et le démarrage du processus exécutant à nouveau.  
  
> [!NOTE]
>  Cette méthode doit être utilisée à la place d' [Continuer](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
## Syntaxe  
  
```cpp  
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
 \[in\]  Un objet d' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) représentant le thread pour continuer.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, le code d'erreur de retour.  
  
## Notes  
 Cette méthode est appelée sur ce processus indépendamment du nombre processus sont débogués, ni quels processus a généré l'événement arrêtant.  L'implémentation doit conserver l'état précédent de exécution \(par exemple une étape\) et reprendre l'exécution comme s'il n'avait jamais interrompu avant de compléter son exécution antérieure.  Autrement dit, si un thread dans ce processus faisait a étape\-au\-dessus d'opération et a été arrêté car un autre processus arrêté, puis un `Continue` a été appelé, le thread spécifié doit effectuer l'origine étape\-au\-dessus de l'opération.  
  
 **Avertissement** n'envoient pas d'événement arrêtant ou un événement \(synchrone\) immédiat est [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) tout en gérant cet appel ; sinon le débogueur peut se bloquer.  
  
## Voir aussi  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)