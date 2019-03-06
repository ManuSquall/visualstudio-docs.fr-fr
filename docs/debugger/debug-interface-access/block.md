---
title: Block | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagBlock symbol
- nested scopes
- Block symbol
ms.assetid: 95b7b0c1-ecc9-405f-8456-5f9cfb866498
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec30f353c9257643a750306828d76ad2f6f87a26
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56626256"
---
# <a name="block"></a>Bloc
Chaque bloc de code est identifié par un `SymTagBlock` symbole. Symboles de bloc sont utilisés pour identifier des étendues imbriquées au sein de fonctions.

## <a name="properties"></a>Propriétés
 Le tableau suivant présente les propriétés qui sont valides pour ce type de symbole.

|Property|Type de données|Description|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Partie du décalage de l’emplacement ; Pour plus d’informations, consultez le [LocationType (énumération)](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Partie de section d’emplacement ; Pour plus d’informations, consultez le [LocationType (énumération)](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Nombre d’octets de code dans le bloc.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbole de la fonction ou un bloc englobant.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Retourne l’ID du symbole lexicale parente.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Blocs ont des emplacements statiques ; Pour plus d’informations, consultez [emplacements de symboles](../../debugger/debug-interface-access/symbol-locations.md).|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Retourne le nom du bloc (qui est généralement une chaîne vide).|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Retourne l’adresse virtuelle de ce bloc par rapport à son parent lexicale.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d’index de symbole.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retourne `SymTagBlock` (parmi les [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md) valeurs).|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Retourne l’adresse virtuelle de ce bloc dans l’exécutable.|

## <a name="see-also"></a>Voir aussi
- [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)
- [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md)