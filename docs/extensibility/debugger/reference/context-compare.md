---
title: "CONTEXT_COMPARE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CONTEXT_COMPARE"
helpviewer_keywords: 
  - "Énumération de CONTEXT_COMPARE"
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# CONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

spécifie les critères pour comparer deux contextes de mémoire.  
  
## Syntaxe  
  
```cpp#  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```c#  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## Membres  
 CONTEXT\_EQUAL  
 recherchez le premier contexte de mémoire dans la liste qui est égale au contexte cible de mémoire.  
  
 CONTEXT\_LESS\_THAN  
 Recherchez le premier contexte de mémoire dans la liste inférieure au contexte cible de mémoire.  
  
 CONTEXT\_GREATER\_THAN  
 Recherchez le premier contexte de mémoire dans la liste supérieure au contexte cible de mémoire.  
  
 CONTEXT\_LESS\_THAN\_OR\_EQUAL  
 Recherchez le premier contexte de mémoire dans la liste qui est inférieure ou égale au contexte cible de mémoire.  
  
 CONTEXT\_GREATER\_THAN\_OR\_EQUAL  
 Recherchez le premier contexte de mémoire dans la liste qui est supérieur ou égal au contexte cible de mémoire.  
  
 CONTEXT\_SAME\_SCOPE  
 Recherchez le premier contexte de mémoire dans la liste figurant dans la même portée que le contexte cible de mémoire.  
  
 CONTEXT\_SAME\_FUNCTION  
 Recherchez le premier contexte de mémoire dans la liste figurant dans la même fonction que la portée cible de mémoire.  
  
 CONTEXT\_SAME\_MODULE  
 Recherchez le premier contexte de mémoire dans la liste qui se trouve dans le même que le contexte cible de mémoire.  
  
 CONTEXT\_SAME\_PROCESS  
 Recherchez le premier contexte de mémoire dans la liste qui se trouve dans le même processus que le contexte cible de mémoire.  
  
## Notes  
 passé comme argument à la méthode d' [Comparer](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) .  
  
 ces valeurs sont utilisées pour rechercher le premier contexte de mémoire dans une liste qui répond aux critères spécifiés de comparaison.  Un contexte de mémoire reçoit une liste des contextes de mémoire pour la comparer à via la méthode d' `IDebugMemoryContext2::Compare` .  Le premier contexte de mémoire dans la liste pour laquelle l'opérateur de comparaison est `true` est ensuite retournée.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Comparer](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)