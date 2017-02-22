---
title: "BaseClass | Microsoft Docs"
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
  - "types définis par l’utilisateur, classes de base"
  - "BaseClass, symbole"
  - "classes de base, types définis par l’utilisateur"
ms.assetid: 9375ca35-cb91-45f5-8903-7344ee4528e8
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# BaseClass
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Chaque classe de base pour un symbole défini \(UDT\) par l'utilisateur de type est identifiée par un enfant à une balise d' `SymTagBaseClass` .  La propriété de [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) contient le symbole pour le type défini par l'utilisateur sous\-jacent, et toutes les propriétés du type défini par l'utilisateur sous\-jacent sont disponibles dans le cadre de ce symbole de BaseClass.  
  
## Propriétés  
 Le tableau suivant affiche les propriétés valides supplémentaires pour ce type de symbole.  
  
|Propriété|Type de données|Description|  
|---------------|---------------------|-----------------|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|modificateur d'accès appliqué à cette classe de base.  Une des valeurs de [CV\_access\_e, énumération](../../debugger/debug-interface-access/cv-access-e.md).|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|symbole de la classe englobante \(le cas échéant\).|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|ID du symbole de parent de classe.|  
|[IDiaSymbol::get\_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|`TRUE` si la classe de base a un constructeur.|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` si la classe de base est marquée comme const.|  
|[IDiaSymbol::get\_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|`TRUE` si la classe de base a un opérateur d'assignation.|  
|[IDiaSymbol::get\_hasCastOperator](../Topic/IDiaSymbol::get_hasCastOperator.md)|`BOOL`|`TRUE` si la classe de base a un opérateur de cast.|  
|[IDiaSymbol::get\_hasNestedTypes](../Topic/IDiaSymbol::get_hasNestedTypes.md)|`BOOL`|`TRUE` si la classe de base a types imbriqués.|  
|[IDiaSymbol::get\_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|`BOOL`|`TRUE` si la classe de base est indirecte.|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`DWORD`|longueur de cette classe de base en octets.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbole du module englobant.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID du symbole parent lexicale.|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|nom de la classe de base.|  
|[IDiaSymbol::get\_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|`TRUE` si la classe de base est imbriquée.|  
|[IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|offset du sous\-objet qui représente la classe de base dans la structure.|  
|[IDiaSymbol::get\_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|`TRUE` si la classe de base a des opérateurs surchargés.|  
|[IDiaSymbol::get\_packed](../Topic/IDiaSymbol::get_packed.md)|`BOOL`|`TRUE` si la classe de base sont compressées.|  
|[IDiaSymbol::get\_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|`TRUE` si la classe de base s'affiche dans une portée non globales.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d'index de symbole.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retourne `SymTagBaseClass` \(une des valeurs de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|le symbole pour la classe de base [UDT](../../debugger/debug-interface-access/udt.md).|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID du symbole de type.|  
|[IDiaSymbol::get\_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|`DWORD`|une valeur d' [UdtKind, énumération](../../debugger/debug-interface-access/udtkind.md).|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` si la classe de base est non alignée.|  
|[IDiaSymbol::get\_virtualBaseClass](../Topic/IDiaSymbol::get_virtualBaseClass.md)|`BOOL`|`TRUE` si la classe de base est virtuelle.|  
|[IDiaSymbol::get\_virtualBaseDispIndex](../Topic/IDiaSymbol::get_virtualBaseDispIndex.md)|`DWORD`|index dans le tableau de décalage de base virtuel.|  
|[IDiaSymbol::get\_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|`LONG`|offset du pointeur de base virtuel.|  
|[IDiaSymbol::get\_virtualBaseTableType](../Topic/IDiaSymbol::get_virtualBaseTableType.md)|`IDiaSymbol*`|le type du pointeur virtuel de table de base.|  
|[IDiaSymbol::get\_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|`IDiaSymbol*`|Le symbole qui décrit le type du tableau virtuel pour cette classe de base.|  
|[IDiaSymbol::get\_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|`DWORD`|ID du symbole virtuel de forme de tableau.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` si la classe de base est marquée comme volatile.|  
  
## Voir aussi  
 [Hiérarchie de classes des types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [UDT](../../debugger/debug-interface-access/udt.md)