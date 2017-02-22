---
title: "Atteignez un point d&#39;arr&#234;t | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage (débogage SDK), en appuyant sur les points d'arrêt"
  - "points d'arrêt, en appuyant sur"
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Atteignez un point d&#39;arr&#234;t
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les éléments suivants décrivent le processus lorsque le moteur de débogage \(DE\) en conflit avec un point d'arrêt pendant l'exécution ou \- à \- pas :  
  
## résoudre un point d'arrêt de correspondance  
  
1.  Le De envoie une interface d' [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) comme **EVENT\_SYNCHRONIZATION\_STOP**.  
  
2.  Le gestionnaire de débogage de session \(SDM\) appelle [IDebugBreakpointEvent2 : : : EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) pour obtenir le point d'arrêt qui atteinte.  
  
## Voir aussi  
 [Appeler les événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)