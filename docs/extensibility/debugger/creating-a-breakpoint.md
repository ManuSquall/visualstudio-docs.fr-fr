---
title: "Cr&#233;ation d&#39;un point d&#39;arr&#234;t | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "points d'arrêt, création"
  - "débogage (débogage SDK), la création de points d'arrêt"
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Cr&#233;ation d&#39;un point d&#39;arr&#234;t
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les éléments suivants décrivent le processus de création d'un point d'arrêt.  
  
## méthodes dans la création de point d'arrêt  
 Lorsque le module qui est nécessaire pour lier un point d'arrêt est chargé, le gestionnaire de débogage de session \(SDM\) appelle les méthodes suivantes :  
  
1.  [IDebugPendingBreakpoint2 : : Vérifiez](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)  
  
2.  [IDebugPendingBreakpoint2 : : virtualisez](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)  
  
3.  [IDebugPendingBreakpoint2 : : CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)  
  
    > [!NOTE]
    >  **CanBind** est appelé uniquement lorsqu'un utilisateur fait un point d'arrêt dans la fenêtre points d'arrêt.  
  
4.  [IDebugPendingBreakpoint2 : : Liaison](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)  
  
5.  [IDebugPendingBreakpoint2 : : EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)  
  
## Voir aussi  
 [Appeler les événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)