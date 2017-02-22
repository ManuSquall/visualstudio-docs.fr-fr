---
title: "IDebugCanStopEvent2::CanStop | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCanStopEvent2::CanStop"
helpviewer_keywords: 
  - "IDebugCanStopEvent2::CanStop"
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Informe le moteur \(DE\) de débogage si vous arrêter à l'emplacement actuel du code ou continuer immédiatement l'exécution.  
  
## Syntaxe  
  
```cpp#  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```c#  
int CanStop (   
   int fCanStop  
);  
```  
  
#### Paramètres  
 `fCanStop`  
 \[in\]  Différente de zéro \(`TRUE`\) si le De s'arrête à l'emplacement actuel du code ; sinon, le zéro \(`FALSE`\).  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Le récepteur de cet événement appelle généralement la méthode d' [GetReason](../Topic/IDebugCanStopEvent2::GetReason.md) pour déterminer la raison décrite dans le De souhaite que, et appelle ensuite la méthode d' `IDebugCanStopEvent2::CanStop` à la réponse appropriée.  
  
 Si le De arrête, il envoie un événement qui décrit la raison de l'arrêt.  Il y a généralement deux événements qui sont envoyés, un utilisateur ou un saut de signal représenté par l'interface d' [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) , et un événement point d'arrêt représenté par l'interface d' [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) .  
  
## Voir aussi  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../Topic/IDebugCanStopEvent2::GetReason.md)