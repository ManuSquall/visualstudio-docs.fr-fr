---
title: "METADATA_ADDRESS_METHOD | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_METHOD"
helpviewer_keywords: 
  - "Structure METADATA_ADDRESS_METHOD"
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# METADATA_ADDRESS_METHOD
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette structure représente l'adresse d'une méthode de classe.  
  
## Syntaxe  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_METHOD {  
   _mdToken tokMethod;  
   DWORD    dwOffset;  
   DWORD    dwVersion;  
} METADATA_ADDRESS_METHOD;  
```  
  
```c#  
public struct METADATA_ADDRESS_METHOD {  
   public int  tokMethod;  
   public uint dwOffset;  
   public uint dwVersion;  
}  
```  
  
## termes  
 tokMethod  
 L'ID de la méthode.  
  
 \[C\+\+\] `_mdToken` est `typedef` pour `int`32 bits.  
  
 dwOffset  
 L'offset contenu dans le début de classe à cette méthode \(peut représenter l'offset dans vtable\).  
  
 dwVersion  
 la version de la méthode \(cette valeur est unique au fournisseur de symbole\).  
  
## Notes  
 Cette structure fait partie de l'union dans la structure de [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) lorsque le champ d' `dwKind` de la structure d' `DEBUG_ADDRESS_UNION` est défini à `ADDRESS_KIND_METHOD` \(une valeur de l'énumération d' [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) \).  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)