---
title: "Donn&#233;es (Kit de d&#233;veloppement logiciel de Debug&#160;Interface&#160;Access) | Microsoft Docs"
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
  - "variables globales [C++], en tant que symboles"
  - "variables locales [C++], en tant que symboles"
  - "membres de classe [C++], en tant que symboles"
  - "Symbole de données"
ms.assetid: 0f17e96a-2e06-42c9-a877-3e5e670ee0ef
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Donn&#233;es (Kit de d&#233;veloppement logiciel de Debug&#160;Interface&#160;Access)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Toutes les variables, telles que des paramètres, des variables locales, des variables globales, et les membres de classe, sont identifiées par des symboles d' `SymTagData` .  Les valeurs de constante \(`LocIsConstant`\) sont également marquées avec ce type.  
  
## Propriétés  
 Le tableau suivant indique les propriétés qui sont valides pour ce type de symbole.  
  
|Propriété|Type de données|Description|  
|---------------|---------------------|-----------------|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Si un champ, un des valeurs de [CV\_access\_e, énumération](../../debugger/debug-interface-access/cv-access-e.md).|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Partie décalée d'emplacement ; pour plus d'informations, consultez [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Élément de section d'emplacement ; pour plus d'informations, consultez [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_addressTaken](../Topic/IDiaSymbol::get_addressTaken.md)|`BOOL`|`TRUE` si cette adresse de données est référencée par un autre symbole.|  
|[IDiaSymbol::get\_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|`DWORD`|Position de bits d'emplacement ; pour plus d'informations, consultez [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md) \(non pris en charge dans diamètre Kit de développement logiciel v8.0\).|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|Symbole pour la classe, s'il s'agit d'une structure, une union, ou un champ de classe.|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|ID du symbole de parent de classe.|  
|[IDiaSymbol::get\_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|`BOOL`|`TRUE` si les données ont été générée par le compilateur.|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` si les données est marquée comme étant constante.|  
|[IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|`DWORD`|Une des valeurs de [DataKind, énumération](../../debugger/debug-interface-access/datakind.md).|  
|[IDiaSymbol::get\_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|`BOOL`|`TRUE` si les données fait partie d'un type de données agrégées \(uniquement dans diamètre Kit de développement logiciel v8.0 et versions ultérieures\).|  
|[IDiaSymbol::get\_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|`BOOL`|`TRUE` si les données sont a été fractionné en agrégat de plusieurs symboles \(uniquement dans diamètre Kit de développement logiciel v8.0 et versions ultérieures\).|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Taille du champ de bits ; pour plus d'informations, consultez [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbole pour le module, la fonction, du bloc ou englobante.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID du symbole parent lexicale.|  
|[IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)|`DWORD`|Types autorisés l'différents d'emplacement ; pour plus d'informations, consultez [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md)|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|Nom de la variable.|  
|[IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|offset de contenu du registre ; pour plus d'informations, consultez [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_registerId](../Topic/IDiaSymbol::get_registerId.md)|`DWORD`|indicateur de registre d'emplacement ; pour plus d'informations, consultez [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Position relative des données dans le bloc.|  
|[IDiaSymbol::get\_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|`DWORD`|obtient le numéro d'emplacement des données.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d'index de symbole.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retourne `SymTagData` \(une des valeurs de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|le jeton de métadonnées représentant les données.|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbole pour le type de variable.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID du symbole variable de type.|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` si les données sont non alignée.|  
|[IDiaSymbol::get\_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|la valeur des constantes.|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|position des données dans le fichier exécutable.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` si les données est marquée comme volatile.|  
  
## Voir aussi  
 [CV\_access\_e, énumération](../../debugger/debug-interface-access/cv-access-e.md)   
 [DataKind, énumération](../../debugger/debug-interface-access/datakind.md)   
 [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)   
 [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md)