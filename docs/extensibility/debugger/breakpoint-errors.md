---
title: "Erreurs de point d&#39;arr&#234;t | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "points d'arrêt, erreurs"
  - "débogage des erreurs de point d'arrêt [Debugging SDK],"
  - "erreurs (déboguer SDK)"
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Erreurs de point d&#39;arr&#234;t
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les éléments suivants décrivent le processus lorsque les tentatives d'un point d'arrêt à lier au code mais échouer :  
  
## résoudre une erreur de point d'arrêt  
  
1.  le moteur de débogage \(DE\) envoie [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) au gestionnaire de débogage de session \(SDM\).  
  
2.  Le SDM appelle [IDebugBreakpointErrorEvent2 : : GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) \(IDebugErrorBreakpoint2 \*\* `ppErrorBP`\) pour obtenir le point d'arrêt d'erreur.  
  
3.  Le SDM appelle [IDebugErrorBreakpoint2 : : GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) pour obtenir le point d'arrêt en attente dont le point d'arrêt d'erreur a commencé.  
  
4.  Le SDM appelle [IDebugErrorBreakpoint2 : : GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) pour obtenir la raison pour laquelle le point d'arrêt d'erreur ne s'est pas lié.  
  
## Voir aussi  
 [Appeler les événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)