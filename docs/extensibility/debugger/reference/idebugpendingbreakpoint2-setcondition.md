---
title: "IDebugPendingBreakpoint2::SetCondition | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2::SetCondition"
helpviewer_keywords: 
  - "SetCondition (méthode)"
  - "IDebugPendingBreakpoint2::SetCondition (méthode)"
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPendingBreakpoint2::SetCondition
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Définit ou modifie la condition associée au point d'arrêt en attente.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```c#  
int SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
#### Paramètres  
 `bpCondition`  
 \[in\]  Une structure de [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) qui spécifie la condition à définir.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Toute condition qui a été précédemment associée au point d'arrêt en attente est perdue.  Tous les points d'arrêt liés de ce point d'arrêt en attente sont appelés pour définir leur état à la valeur spécifiée dans le paramètre d' `bpCondition` .  
  
## Voir aussi  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)