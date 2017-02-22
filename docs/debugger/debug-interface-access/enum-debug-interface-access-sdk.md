---
title: "&#201;num&#233;ration (Kit de d&#233;veloppement logiciel SDK de Debug&#160;Interface&#160;Access) | Microsoft Docs"
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
  - "Types énumérés en tant que symboles"
  - "symbole Enum"
ms.assetid: c777e2e6-88be-435b-b632-8d43f42b0b49
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# &#201;num&#233;ration (Kit de d&#233;veloppement logiciel SDK de Debug&#160;Interface&#160;Access)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les énumérations sont identifiées par des symboles d' `SymTagEnum` .  Chaque valeur d'énumération apparaît comme enfant de classe avec une balise d' `SymTagConstant` .  
  
## Propriétés  
 Le tableau suivant affiche les propriétés valides supplémentaires pour ce type de symbole.  
  
|Propriété|Type de données|Description|  
|---------------|---------------------|-----------------|  
|[IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|`DWORD`|Une des valeurs de [BasicType, énumération](../../debugger/debug-interface-access/basictype.md).|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|Parent de la classe de cette énumération éventuelle.|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|ID du symbole de parent de classe.|  
|[IDiaSymbol::get\_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|`TRUE` si l'énumération a un constructeur.|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` si l'énumération est marquée comme const.|  
|[IDiaSymbol::get\_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|`TRUE` si l'énumération contient un opérateur d'assignation.|  
|[IDiaSymbol::get\_hasCastOperator](../Topic/IDiaSymbol::get_hasCastOperator.md)|`BOOL`|`TRUE` si l'énumération contient un opérateur de cast.|  
|[IDiaSymbol::get\_hasNestedTypes](../Topic/IDiaSymbol::get_hasNestedTypes.md)|`BOOL`|`TRUE` si l'énumération a types imbriqués.|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`DWORD`|longueur de cette énumération en octets.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|symbole de [Compiland](../../debugger/debug-interface-access/compiland.md)englobant.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID du symbole parent lexicale.|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|Nom du type énuméré.|  
|[IDiaSymbol::get\_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|`TRUE` si l'énumération est imbriquée.|  
|[IDiaSymbol::get\_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|`TRUE` si l'énumération a des opérateurs surchargés.|  
|[IDiaSymbol::get\_packed](../Topic/IDiaSymbol::get_packed.md)|`BOOL`|`TRUE` si l'énumération sont compressées.|  
|[IDiaSymbol::get\_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|`TRUE` si l'énumération apparaît dans une portée lexicale non globales.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d'index de symbole.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retourne `SymTagEnum` \(une des valeurs de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbole du type sous\-jacent.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID du symbole de type.|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` si l'énumération est non alignée.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` si l'énumération est marquée comme volatile.|  
  
## Voir aussi  
 [Hiérarchie de classes des types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)