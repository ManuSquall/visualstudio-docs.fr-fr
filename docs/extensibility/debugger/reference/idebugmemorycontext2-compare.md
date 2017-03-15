---
title: "IDebugMemoryContext2::Compare | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::Compare"
helpviewer_keywords: 
  - "IDebugMemoryContext2::Compare (méthode)"
  - "Compare (méthode)"
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugMemoryContext2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Compare le contexte de mémoire à chaque contexte dans le tableau donné de la façon indiquée par comparaison des balises, en retournant un index du premier contexte qui correspond à.  
  
## Syntaxe  
  
```cpp#  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```c#  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### Paramètres  
 `compare`  
 \[in\]  une valeur de l'énumération de [CONTEXT\_COMPARE](../../../extensibility/debugger/reference/context-compare.md) qui détermine le type de comparaison.  
  
 `rgpMemoryContextSet`  
 \[in\]  Un tableau de références aux objets d' [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) à comparer à.  
  
 `dwMemoryContextSetLen`  
 \[in\]  Le nombre de contextes dans le tableau d' `rgpMemoryContextSet` .  
  
 `pdwMemoryContext`  
 \[out\]  Retourne l'index du premier contexte de mémoire qui satisfait la comparaison.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Retourne `E_COMPARE_CANNOT_COMPARE` si les deux contextes ne peuvent pas être comparés.  
  
## Notes  
 un moteur de débogage \(DE\) ne doit pas prendre en charge tous les types de comparaisons, mais il doit prendre en charge au moins `CONTEXT_EQUAL`, `CONTEXT_LESS_THAN`, `CONTEXT_GREATER_THAN` et `CONTEXT_SAME_SCOPE`.  
  
## Voir aussi  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT\_COMPARE](../../../extensibility/debugger/reference/context-compare.md)