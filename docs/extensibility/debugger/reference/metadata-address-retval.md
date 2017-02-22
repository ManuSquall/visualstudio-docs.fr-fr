---
title: "METADATA_ADDRESS_RETVAL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_RETVAL"
helpviewer_keywords: 
  - "Structure METADATA_ADDRESS_RETVAL"
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# METADATA_ADDRESS_RETVAL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette structure représente une valeur de retournée d'une méthode ou une fonction.  
  
## Syntaxe  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_RETVAL {  
   _mdToken tokMethod;  
   DWORD    dwCorType;  
   DWORD    dwSigSize;  
   BYTE     rgSig[10];  
} METADATA_ADDRESS_RETVAL;  
```  
  
```c#  
public struct METADATA_ADDRESS_RETVAL {  
   public int    tokMethod;  
   public uint   dwCorType;  
   public uint   dwSigSize;  
   public byte[] rgSig;  
}  
```  
  
## Termes  
 tokMethod  
 ID de la méthode pour cette valeur de retour.  
  
 dwCorType  
 Le type de base de la valeur de retour. Il s'agit d'une valeur à partir de la `CorElementType` énumération définie dans le [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] fichier corhdr.h de kit de développement logiciel.  
  
 dwSigSize  
 La taille de la signature de la valeur de retour \(tel que stocké dans `rgSig`\).  
  
 rgSig  
 Un tableau d'octets qui forment la signature de la valeur de retour.  
  
## Notes  
 Cette structure fait partie de l'union dans la [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) lorsque la structure le `dwKind` champ le `DEBUG_ADDRESS_UNION` structure est définie sur `ADDRESS_KIND_RETVAL` \(une valeur à partir de la [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) énumération\).  
  
## Configuration requise  
 En\-tête : sh.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)