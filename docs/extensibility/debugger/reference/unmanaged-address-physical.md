---
title: "UNMANAGED_ADDRESS_PHYSICAL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UNMANAGED_ADDRESS_PHYSICAL"
helpviewer_keywords: 
  - "Structure UNMANAGED_ADDRESS_PHYSICAL"
ms.assetid: fed09686-caa6-4efc-851e-a0432019e9d0
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# UNMANAGED_ADDRESS_PHYSICAL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette structure représente une adresse physique.  
  
## Syntaxe  
  
```cpp  
typedef struct _tagUNMANAGED_ADDRESS_PHYSICAL {  
   ULONGLONG offset;  
} UNMANAGED_ADDRESS_PHYSICAL;  
```  
  
```c#  
public struct UNMANAGED_ADDRESS_PHYSICAL {  
   public ulong offset;  
}  
```  
  
## termes  
 offset  
 Un décalage 64 bits dans un espace d'adressage physique.  
  
## Notes  
 Cette structure fait partie de l'union dans la structure de [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) lorsque le champ d' `dwKind` de la structure d' `DEBUG_ADDRESS_UNION` est défini à `ADDRESS_KIND_UNMANAGED_PHYSICAL` \(une valeur de l'énumération d' [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) \).  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)