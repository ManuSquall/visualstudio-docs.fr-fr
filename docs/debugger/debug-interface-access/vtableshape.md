---
title: "VTableShape | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VTableShape (symbole)"
  - "SymTagVTableShape (balise)"
ms.assetid: dd97f4c3-115d-46a9-b506-2531e30a0d8f
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# VTableShape
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

le symbole de [VTable](../../debugger/debug-interface-access/vtable.md) a un symbole enfant de classe identifié par la balise d' `SymTagVTableShape` .  
  
## Propriétés  
 Le tableau suivant affiche les propriétés valides supplémentaires pour ce type de symbole.  
  
|Propriété|Type de données|Description|  
|---------------|---------------------|-----------------|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` si la classe du pointeur VTable est marquée comme constante.|  
|[IDiaSymbol::get\_count](../Topic/IDiaSymbol::get_count.md)|`DWORD`|Nombre d'entrées dans VTable.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbole du module englobant.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID du symbole parent lexicale.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d'index de symbole.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retourne `SymTagVTableShape` \(une des valeurs de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` si la classe du pointeur VTable est non alignée.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` si la classe du pointeur VTable est marquée comme volatile.|  
  
## Voir aussi  
 [Hiérarchie de classes des types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [VTable](../../debugger/debug-interface-access/vtable.md)