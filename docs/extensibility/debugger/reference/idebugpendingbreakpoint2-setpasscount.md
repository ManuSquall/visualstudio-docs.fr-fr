---
title: "IDebugPendingBreakpoint2::SetPassCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2::SetPassCount"
helpviewer_keywords: 
  - "SetPassCount (méthode)"
  - "IDebugPendingBreakpoint2::SetPassCount (méthode)"
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPendingBreakpoint2::SetPassCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Définit ou modifie le nombre de passage associé au point d'arrêt en attente.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```c#  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### Paramètres  
 `bpPassCount`  
 \[in\]  une structure de [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) qui contient le nombre de passage.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Retourne `E_BP_DELETED` si le point d'arrêt a été supprimé.  
  
## Notes  
 Tout nombre de tests qui a été précédemment associé au point d'arrêt en attente est perdu.  Tous les points d'arrêt liés de ce point d'arrêt en attente sont appelés pour définir leur nombre de passage au paramètre d' `bpPassCount` .  
  
## Voir aussi  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)