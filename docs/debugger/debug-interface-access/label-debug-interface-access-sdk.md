---
title: Étiquette (SDK Debug Interface Access) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- locations, in program code
- Label symbol
ms.assetid: 8cef7620-5bc8-4500-8bd0-e9e638bccb24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b445c5f8be55d5290feb1318a3b937980a3e5c06
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616233"
---
# <a name="label-debug-interface-access-sdk"></a>Étiquette (Kit de développement logiciel de Debug Interface Access)
Un emplacement dans le code de programme est identifié par un `SymTagLabel` symbole.

## <a name="properties"></a>Propriétés
 Le tableau suivant présente les propriétés qui sont valides pour ce type de symbole.

|Property|Type de données|Description|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Partie du décalage de l’emplacement ; Pour plus d’informations, consultez le [LocationType (énumération)](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Partie de section d’emplacement ; Pour plus d’informations, consultez le [LocationType (énumération)](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` Si l’étiquette utilise une convention d’appel personnalisée.|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` Si l’étiquette effectue un retour far.|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` Si l’étiquette contient un retour à partir de l’interruption.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbole de compiland, bloc ou fonction englobante.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID du symbole lexicale parente.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Les étiquettes ont des emplacements statiques ; Pour plus d’informations, consultez le [emplacements de symboles](../../debugger/debug-interface-access/symbol-locations.md) énumération.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nom de l’étiquette.|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` Si l’étiquette a été spécifié avec la [noinline](/cpp/cpp/noinline) attribut.|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` Si l’étiquette a été spécifié avec la [noreturn](/cpp/cpp/noreturn) attribut.|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` Si l’étiquette n’est jamais appelée.|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Décalage du symbole dans la mémoire ; Pour plus d’informations, consultez le [LocationType (énumération)](../../debugger/debug-interface-access/locationtype.md), `LocIsRegRel`.|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` Si le code a des informations de débogage pour le code optimisé.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Position relative de cette étiquette au sein de son module.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d’index de symbole.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retourne `SymTagFuncDebugLabel` (parmi les [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md) valeurs).|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Position de cette étiquette dans l’image exécutable.|

## <a name="see-also"></a>Voir aussi
- [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)
- [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md)