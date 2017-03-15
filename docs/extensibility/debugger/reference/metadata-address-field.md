---
title: "METADATA_ADDRESS_FIELD | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_FIELD"
helpviewer_keywords: 
  - "Structure METADATA_ADDRESS_FIELD"
ms.assetid: 15ab45fe-6b3b-4e09-880b-31b34f523607
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# METADATA_ADDRESS_FIELD
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette structure représente l'adresse d'un champ d'une classe ou d'une structure.  
  
## Syntaxe  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_FIELD {  
   _mdToken tokField;  
} METADATA_ADDRESS_FIELD  
```  
  
```c#  
public struct METADATA_ADDRESS_FIELD {  
   public int tokField;  
}  
```  
  
## termes  
 tokField  
 L'ID du jeton de champ.  
  
 \[C\+\+\] `_mdToken` est `typedef` pour `int`32 bits.  
  
## Notes  
 Cette structure fait partie de l'union dans la structure de [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) lorsque le champ d' `dwKind` de la structure d' `DEBUG_ADDRESS_UNION` est défini à `ADDRESS_KIND_FIELD` \(une valeur de l'énumération d' [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) \).  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)