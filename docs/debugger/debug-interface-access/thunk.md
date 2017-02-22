---
title: "Thunk | Microsoft Docs"
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
  - "propriétés de conversion de code (DIA SDK)"
  - "symbole de conversion de code"
ms.assetid: 01abb95f-d89a-465c-a4eb-8e8509598c95
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Thunk
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

chaque `thunk` est identifié par une balise d' `SymTagThunk` .  
  
## Propriétés  
 Le tableau suivant indique les propriétés qui sont valides pour ce type de symbole.  
  
|Propriété|Type de données|Description|  
|---------------|---------------------|-----------------|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Attribut de modificateur d'accès, parmi les valeurs de [CV\_access\_e, énumération](../../debugger/debug-interface-access/cv-access-e.md) \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Partie décalée d'emplacement ; pour plus d'informations, consultez [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSegment::get\_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|`DWORD`|Élément de section d'emplacement ; pour plus d'informations, consultez [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|Parent de classe englobante, si approprié \(uniquement sous diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|ID du symbole parent de classe englobante \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|TRUE si la conversion de code est marquée comme constante \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|TRUE si la conversion de code est une introduction à une fonction virtuelle \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\)|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|TRUE si la conversion de code est considéré comme static \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Nombre d'octets de code dans la conversion de code.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbole pour le module \(compiland\), le bloc, ou la fonction englobant.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID du symbole parent lexicale.|  
|[IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)|`DWORD`|Les points de terminaison ont l'emplacement statique ; pour plus d'informations, consultez l'énumération de [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md) .|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|nom de la conversion de code.|  
|[IDiaSymbol::get\_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|TRUE si la conversion de code est purement virtuelle \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|position relative de cette conversion de code dans son module.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d'index de symbole.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retourne `SymTagThunk` \(une des valeurs de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|`DWORD`|Partie décalée de l'emplacement de la cible de conversion de code.|  
|[IDiaSymbol::get\_targetRelativeVirtualAddress](../Topic/IDiaSymbol::get_targetRelativeVirtualAddress.md)|`DWORD`|Adresse virtuelle relative de la cible de thunk dans son bloc englobant.|  
|[IDiaSymbol::get\_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|`DWORD`|Élément de section de la cible de conversion de code.|  
|[IDiaSymbol::get\_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|`ULONGLONG`|Position de la cible de thunk dans l'image exécutable.|  
|[IDiaSymbol::get\_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|`DWORD`|effectuer une converson de code le type, comme défini par [THUNK\_ORDINAL, énumération](../../debugger/debug-interface-access/thunk-ordinal.md).|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Le type de cette conversion \(code uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID du symbole de type \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` si la conversion de code n'est pas alignée \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\),|  
|[IDiaSymbol::get\_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` si la conversion de code est virtuelle \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|position de cette conversion de code dans l'image exécutable.|  
|[IDiaSymbol::get\_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|L'offset dans la table virtuelle à cette conversion \(code uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` si la conversion de code est marquée comme volatile \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
  
## Voir aussi  
 [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)   
 [THUNK\_ORDINAL, énumération](../../debugger/debug-interface-access/thunk-ordinal.md)