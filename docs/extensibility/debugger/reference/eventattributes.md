---
title: "EVENTATTRIBUTES | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EVENTATTRIBUTES"
helpviewer_keywords: 
  - "Énumération EVENTATTRIBUTES"
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# EVENTATTRIBUTES
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

spécifie les attributs d'événement.  
  
## Syntaxe  
  
```cpp#  
enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
typedef DWORD EVENTATTRIBUTES;  
```  
  
```c#  
public enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
```  
  
## Membres  
 EVENT\_ASYNCHRONOUS  
 indique que l'événement est asynchrone et aucune réponse à l'événement n'est nécessaire.  
  
 EVENT\_SYNCHRONOUS  
 indique que l'événement est synchrone ; réponse au moyen d' [ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md).  
  
 EVENT\_STOPPING  
 Indique qu'il s'agit d'un événement arrêtant.  Doit être associée à `EVENT_ASYNCHRONOUS` ou `EVENT_SYNCHRONOUS`.  
  
 EVENT\_ASYNC\_STOP  
 Indique un événement arrêtant asynchrone.  Il n'existe actuellement aucun événement.  Cette balise est uniquement un espace réservé.  
  
 EVENT\_SYNCHRONIZATION\_STOP  
 Indique un événement arrêtant synchrone \(une combinaison d' `EVENT_SYNCHRONOUS` et d' `EVENT_STOPPING`\).  Cette valeur est utilisée par un moteur \(DE\) de débogage lorsqu'elle envoie un événement arrêtant.  La réponse est effectuée via un appel à [Exécuter](../../../extensibility/debugger/reference/idebugprogram2-execute.md), à [Étape](../../../extensibility/debugger/reference/idebugprogram2-step.md), ou à [Continuer](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
 EVENT\_IMMEDIATE  
 Indique un événement qui est envoyé immédiatement et de façon synchrone à l'IDE.  Cette balise est combinée avec d'autres balises comme `EVENT_ASYNCHRONOUS`, `EVENT_SYNCHRONOUS`, ou `EVENT_SYNC_STOP` pour indiquer le type de l'événement et du fait que le mécanisme de réponse \(le cas échéant\) est connu.  
  
 EVENT\_EXPRESSION\_EVALUATION  
 L'événement est le résultat d'évaluation de l'expression.  
  
## Notes  
 ces valeurs sont passées dans le paramètre d' `dwAttrib` de la méthode d' [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .  
  
 Ces valeurs peuvent être combinées avec `OR`de bits.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md)   
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)