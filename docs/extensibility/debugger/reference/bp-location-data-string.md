---
title: "BP_LOCATION_DATA_STRING | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_DATA_STRING"
helpviewer_keywords: 
  - "Structure BP_LOCATION_DATA_STRING"
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_LOCATION_DATA_STRING
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Utilisé pour définir les points d'arrêt de données basées sur une chaîne que l'utilisateur peut entrer de l'environnement de développement intégré \(IDE\) \(IDE\).  
  
## Syntaxe  
  
```cpp#  
typedef struct _BP_LOCATION_DATA_STRING {   
   IDebugThread2* pThread;  
   BSTR           bstrContext;  
   BSTR           bstrDataExpr;  
   DWORD          dwNumElements;  
} BP_LOCATION_DATA_STRING;  
```  
  
## Membres  
 `pThread`  
 l'objet d' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le thread sur lequel le point d'arrêt se produit.  
  
 `bstrContext`  
 Le contexte du point d'arrêt dans le code, en général une méthode ou un nom de fonction comme indiqué sur une pile des appels.  
  
 `bstrDataExpr`  
 La chaîne de données entrées d'utilisateur pour définir le point d'arrêt.  
  
 `dwNumElements`  
 le nombre d'éléments dans la chaîne de données dans laquelle le point d'arrêt se produit.  
  
## Notes  
 Cette structure est un membre de la structure de [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) dans le cadre d'une union.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)