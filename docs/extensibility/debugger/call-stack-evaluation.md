---
title: "Version d&#39;&#233;valuation de la pile des appels | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "évaluation de pile d'appel [Debugging SDK], le débogage"
  - "piles d'appels, d'évaluation"
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Version d&#39;&#233;valuation de la pile des appels
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Pour afficher les frames de pile de la pile des appels en mode arrêt, vous devez implémenter la méthode d' [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .  
  
## méthodes pour l'évaluation  
 Pour un moteur de débogage simple \(DE\), il peut y avoir qu'un seul frame de pile.  Pour tester le frame de pile en mode arrêt, vous devez implémenter les méthodes suivantes pour [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)|obtient le contexte de code pour un frame de pile.  le contexte de code représente le pointeur d'instruction actuel dans un frame de pile.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtient le contexte de le document pour un frame de pile.  Le contexte de document représente la position actuelle dans le code source pour un frame de pile.  Requis pour afficher le code source lorsque vous êtes arrêté dans un programme.|  
  
 ces méthodes requièrent l'implémentation de plusieurs interfaces et méthodes contexte\-mises en relation.  Par conséquent, vous devez implémenter la méthode d' [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md) et les méthodes suivantes pour [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Obtient la plage d'instructions de fichier d'un contexte de document.|  
  
 Pour énumérer des contextes de code, vous devez implémenter toutes les méthodes d' [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## Voir aussi  
 [Contrôle de l'exécution et l'évaluation de l'état](../../extensibility/debugger/execution-control-and-state-evaluation.md)