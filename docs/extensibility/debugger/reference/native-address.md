---
title: "NATIVE_ADDRESS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NATIVE_ADDRESS"
helpviewer_keywords: 
  - "Structure NATIVE_ADDRESS"
ms.assetid: 7a0cd085-bfc8-45cc-a3d4-4459070e207a
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# NATIVE_ADDRESS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette structure représente une adresse native.  
  
## Syntaxe  
  
```cpp  
typedef struct _tagNATIVE_ADDRESS {  
   DWORD unknown;  
} NATIVE_ADDRESS;  
```  
  
```c#  
public struct NATIVE_ADDRESS {  
   public uint unknown;  
}  
```  
  
## termes  
 inconnu  
 L'adresse native \(la signification de cela dépend du runtime et du système d'exploitation\).  
  
## Notes  
 Cette structure fait partie de l'union dans la structure de [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) lorsque le champ d' `dwKind` de la structure d' `DEBUG_ADDRESS_UNION` est défini à `ADDRESS_KIND_NATIVE` \(une valeur de l'énumération d' [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) \).  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)