---
title: "Typedef (Kit de d&#233;veloppement logiciel de Debug&#160;Interface&#160;Access) | Microsoft Docs"
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
  - "Typedef (symbole) (DIA SDK)"
ms.assetid: 9ab441b9-cc72-47fa-83e2-87b3c2b891b4
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Typedef (Kit de d&#233;veloppement logiciel de Debug&#160;Interface&#160;Access)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les symboles avec des balises d' `SymTagTypedef` nom des types pour d'autres types.  
  
## Propriétés  
 Le tableau suivant affiche les propriétés valides supplémentaires pour ce type de symbole.  
  
|Propriété|Type de données|Description|  
|---------------|---------------------|-----------------|  
|[IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|`DWORD`|Une des valeurs de [BasicType, énumération](../../debugger/debug-interface-access/basictype.md).|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|Parent de classe de ce typedef le cas échéant.|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|ID du symbole de parent de classe.|  
|[IDiaSymbol::get\_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|`TRUE` si ce typedef possède un constructeur.|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` si ce typedef est marqué comme constante.|  
|[IDiaSymbol::get\_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|`TRUE` si ce typedef contient un opérateur d'assignation.|  
|[IDiaSymbol::get\_hasCastOperator](../Topic/IDiaSymbol::get_hasCastOperator.md)|`BOOL`|`TRUE` si ce typedef contient un opérateur de cast.|  
|[IDiaSymbol::get\_hasNestedTypes](../Topic/IDiaSymbol::get_hasNestedTypes.md)|`BOOL`|`TRUE` si ce typedef a types imbriqués.|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|longueur de ce typedef en octets.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbole du module englobant.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID du symbole parent lexicale.|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|nom du typedef.|  
|[IDiaSymbol::get\_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|`TRUE` si ce typedef est imbriqué dans une portée lexicale.|  
|[IDiaSymbol::get\_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|`TRUE` si ce typedef contient un opérateur surchargé.|  
|[IDiaSymbol::get\_packed](../Topic/IDiaSymbol::get_packed.md)|`BOOL`|`TRUE` si ce typedef est compressé.|  
|[IDiaSymbol::get\_reference](../Topic/IDiaSymbol::get_reference.md)|`BOOL`|`TRUE` si ce typedef est une référence.|  
|[IDiaSymbol::get\_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|`TRUE` si ce typedef est dans une portée lexicale non globales.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d'index de symbole.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retourne `SymTagTypedef` \(une des valeurs de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbole du type sous\-jacent.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID du symbole de type.|  
|[IDiaSymbol::get\_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|`DWORD`|Une des valeurs de [UdtKind, énumération](../../debugger/debug-interface-access/udtkind.md).|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` si ce typedef est pas aligné.|  
|[IDiaSymbol::get\_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|`IDiaSymbol*`|le symbole qui décrit la forme virtuelle de tableau.|  
|[IDiaSymbol::get\_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|`DWORD`|ID du symbole virtuel de forme de tableau.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` si ce typedef est marqué comme volatile.|  
  
## Notes  
 Étant donné qu'un typedef peut représenter une classe, un pointeur, ou un type défini par \(UDT\) l'utilisateur, le symbole pour les partages d'un typedef les mêmes propriétés que l'un de ces autres types de symboles.  
  
## Voir aussi  
 [Hiérarchie de classes des types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)