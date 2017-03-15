---
title: "METADATA_ADDRESS_LOCAL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_LOCAL"
helpviewer_keywords: 
  - "Structure METADATA_ADDRESS_LOCAL"
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# METADATA_ADDRESS_LOCAL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette structure représente l'adresse d'une variable locale dans une portée \(généralement une fonction ou une méthode\).  
  
## Syntaxe  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_LOCAL {  
   _mdToken  tokMethod;  
   IUnknown* pLocal;  
   DWORD     dwIndex;  
} METADATA_ADDRESS_LOCAL;  
```  
  
```c#  
public struct METADATA_ADDRESS_LOCAL {  
   public int    tokMethod;  
   public object pLocal;  
   public uint   dwIndex;  
}  
```  
  
## termes  
 tokMethod  
 L'ID de la méthode ou fonction la variable locale fait partie de.  
  
 \[C\+\+\] `_mdToken` est `typedef` pour `int`32 bits.  
  
 pLocal  
 le jeton dont l'adresse cette structure représente.  
  
 dwIndex  
 Peut être l'index de cette variable locale dans la fonction ou la méthode, ou un autre valeur \(spécifique au langage\).  
  
## Notes  
 Cette structure fait partie de l'union dans la structure de [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) lorsque le champ d' `dwKind` de la structure d' `DEBUG_ADDRESS_UNION` est défini à `ADDRESS_KIND_LOCAL` \(une valeur de l'énumération d' [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) \).  
  
 `Warning:`\[C\+\+\] uniquement si `pLocal` n'est pas nul, puis vous devez appeler `Release` sur le pointeur de jeton \(`addr` est un champ dans la structure de [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) \) :  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)