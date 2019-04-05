---
title: Données (SDK Debug Interface Access) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- global variables [C++], as symbols
- local variables [C++], as symbols
- class members [C++], as symbols
- Data symbol
ms.assetid: 0f17e96a-2e06-42c9-a877-3e5e670ee0ef
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a69e1cddec945cd797d91a92d28ba46221a20d10
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950132"
---
# <a name="data-debug-interface-access-sdk"></a>Données (Kit de développement logiciel de Debug Interface Access)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Toutes les variables, telles que les paramètres, les variables locales, les variables globales et les membres de classe, sont identifiés par `SymTagData` symboles. Valeurs constantes (`LocIsConstant`) sont également identifiés avec ce type.  
  
## <a name="properties"></a>Properties  
 Le tableau suivant présente les propriétés qui sont valides pour ce type de symbole.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Si un champ, puis une des valeurs de la [CV_access_e (énumération)](../../debugger/debug-interface-access/cv-access-e.md).|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Partie du décalage de l’emplacement ; Pour plus d’informations, consultez le [LocationType (énumération)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Partie de section d’emplacement ; Pour plus d’informations, consultez le [LocationType (énumération)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|`BOOL`|`TRUE` Si les adresses de ces données sont référencé par un autre symbole.|  
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|`DWORD`|Position du bit d’emplacement ; Pour plus d’informations, consultez le [LocationType (énumération)](../../debugger/debug-interface-access/locationtype.md) (non pris en charge dans la version 8.0 DIA SDK).|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Symbole de la classe, s’il s’agit d’une structure, union ou champ de classe.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID du symbole classe parent.|  
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|`BOOL`|`TRUE` Si les données ont été générées par le compilateur.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` Si les données sont marquées comme étant constante.|  
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|`DWORD`|Parmi les [DataKind (énumération)](../../debugger/debug-interface-access/datakind.md) valeurs.|  
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|`BOOL`|`TRUE` Si les données font partie d’un type de données agrégées (uniquement dans DIA SDK 8.0 et versions ultérieures).|  
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|`BOOL`|`TRUE` Si les données sont a été divisé en un agrégat de plusieurs symboles (uniquement dans DIA SDK 8.0 et versions ultérieures).|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Longueur de champ de bits ; Pour plus d’informations, consultez le [LocationType (énumération)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbole de le compiland, fonction ou le bloc englobant.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID du symbole lexicale parente.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Les types d’emplacement autorisé ; Pour plus d’informations, consultez [emplacements de symboles](../../debugger/debug-interface-access/symbol-locations.md)|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nom de la variable.|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Décalage à partir du contenu du Registre ; Pour plus d’informations, consultez le [LocationType (énumération)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|`DWORD`|Inscrire l’indicateur d’emplacement ; Pour plus d’informations, consultez le [LocationType (énumération)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Position relative des données dans le bloc.|  
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|`DWORD`|Obtient le numéro d’emplacement des données.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d’index de symbole.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retourne `SymTagData` (parmi les [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md) valeurs).|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|Le jeton de métadonnées représentant les données.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbole pour le type de variable.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID du symbole de type de variable.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Si les données ne sont pas alignées.|  
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|La valeur de données de la constante.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Position des données dans l’exécutable.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Si les données sont marquées comme volatile.|  
  
## <a name="see-also"></a>Voir aussi  
 [CV_access_e, énumération](../../debugger/debug-interface-access/cv-access-e.md)   
 [DataKind, énumération](../../debugger/debug-interface-access/datakind.md)   
 [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)   
 [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md)
