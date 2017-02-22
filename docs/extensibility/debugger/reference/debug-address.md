---
title: "DEBUG_ADDRESS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_ADDRESS"
helpviewer_keywords: 
  - "Structure DEBUG_ADDRESS"
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DEBUG_ADDRESS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette structure représente une adresse.  
  
## Syntaxe  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```c#  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## termes  
 ulAppDomainID  
 L'identificateur de processus  
  
 guidModule  
 GUID du module qui contient cette adresse.  
  
 tokClass  
 Le jeton qui identifie la classe ou le type de cette adresse.  
  
> [!NOTE]
>  Cette valeur est spécifique à un fournisseur de symbole et par conséquent n'a aucune signification générale que celle d'un identificateur pour un type de classe.  
  
 addr  
 Une structure de [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , qui contient une union des structures qui décrivent différents types d'adresse.  la valeur `addr`.`dwKind` provient de l'énumération d' [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) , qui explique comment interpréter l'union.  
  
## Notes  
 Cette structure est passée à la méthode d' [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) à accomplir.  
  
 **Avertissement \[C\+\+\] uniquement**  
  
 Si `addr.dwKind` est `ADDRESS_KIND_METADATA_LOCAL` et si `addr.addr.addrLocal.pLocal` n'est pas une valeur NULL, vous devez appeler `Release` sur le pointeur symbolique :  
  
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
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)