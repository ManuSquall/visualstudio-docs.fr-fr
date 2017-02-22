---
title: "IEnumDebugFrameInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFrameInfo2"
helpviewer_keywords: 
  - "IEnumDebugFrameInfo2"
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface énumère les structures de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) .  
  
## Syntaxe  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 le moteur de débogage \(DE\) implémente cette interface pour fournir une liste de structures qui décrit la pile des appels actuelle.  
  
## Remarques pour les appelants  
 Visual Studio appelle [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) pour obtenir cette interface chaque fois qu'un point d'arrêt, une exception, ou un arrêt se produit dans un programme en cours de débogage.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IEnumDebugFrameInfo2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Suivant](../Topic/IEnumDebugFrameInfo2::Next.md)|Récupère un nombre spécifié de structures de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) dans une séquence d'énumération.|  
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Ignore un nombre spécifié de structures de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) dans une séquence d'énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|réinitialise une séquence d'énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
|[GetCount](../Topic/IEnumDebugFrameInfo2::GetCount.md)|obtient le nombre de structures de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) dans un énumérateur.|  
  
## Notes  
 Visual Studio reçoit cette interface comme la première étape à gérer un point d'arrêt, une exception, ou une pause fournie par l'utilisateur sur le programme débogué.  La liste de structures de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) représente la pile des appels actuelle, avec l'appel de fonction en cours au début de la liste et l'appel de fonction le plus ancien à la fin de la liste.  Chaque `FRAMEINFO` représente un frame de pile, un contexte dans lequel les expressions peuvent être évaluées et les variables locales être considéré.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)