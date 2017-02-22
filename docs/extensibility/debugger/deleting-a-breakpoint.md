---
title: "Suppression d&#39;un point d&#39;arr&#234;t | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "points d'arrêt, suppression"
  - "débogage (débogage SDK), la suppression des points d'arrêt"
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Suppression d&#39;un point d&#39;arr&#234;t
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les éléments suivants décrivent le processus en supprimant un point d'arrêt en attente :  
  
## Processus de suppression  
 le gestionnaire de débogage de session \(SDM\) appelle la méthode d' [IDebugPendingBreakpoint2 : : suppression](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) pour supprimer le point d'arrêt en attente et tous points d'arrêt liés liés de lui.  
  
> [!NOTE]
>  un point d'arrêt lié unique peut également être supprimé par un appel à [IDebugBoundBreakpoint2 : : suppression](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## Voir aussi  
 [Appeler les événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)