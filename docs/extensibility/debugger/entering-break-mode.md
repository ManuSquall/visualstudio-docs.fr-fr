---
title: "Passage en Mode arr&#234;t | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mode arrêt"
  - "débogage (débogage SDK), le passage en mode arrêt"
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Passage en Mode arr&#234;t
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les éléments suivants décrivent le processus qui se produit lorsqu'un point d'arrêt est produit après entrant dans une fonction, exécutées à la ligne de code source qui a le curseur dans ce modèle, ou exécutées à un point d'arrêt.  
  
## Processus en mode Arrêt  
  
1.  Le moteur \(DE\) de débogage envoie [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md), ou tout autre événement arrêtant pour faire pour écrire l'IDE mode arrêt.  
  
2.  Le SDM obtient les informations de la pile des appels du thread, comme suit :  
  
    -   [IDebugThread2 : : EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    -   [IEnumDebugFrameInfo2 : : GetCount](../Topic/IEnumDebugFrameInfo2::GetCount.md)  
  
    -   [IEnumDebugFrameInfo2 : : suivant](../Topic/IEnumDebugFrameInfo2::Next.md)  
  
    -   [IDebugStackFrame2 : : GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) pour obtenir des informations de code source  
  
    -   [IDebugDocumentContext2 : : GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) pour obtenir le nom de fichier  
  
    -   [IDebugDocumentContext2 : : GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) pour obtenir la plage d'instruction  
  
    -   [IDebugStackFrame2 : : GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md) pour obtenir des informations de mémoire  
  
## Voir aussi  
 [Appeler les événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)