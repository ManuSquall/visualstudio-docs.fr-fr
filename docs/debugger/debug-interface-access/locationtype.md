---
title: LocationType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5aafc62f5920db70bd881bd3a541cfcfabfac360
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862345"
---
# <a name="locationtype"></a>LocationType
Indique le type d’informations d’emplacement contenu dans un symbole.

## <a name="syntax"></a>Syntaxe

```C++
enum LocationType {
    LocIsNull,
    LocIsStatic,
    LocIsTLS,
    LocIsRegRel,
    LocIsThisRel,
    LocIsEnregistered,
    LocIsBitField,
    LocIsSlot,
    LocIsIlRel,
    LocInMetaData,
    LocIsConstant,
    LocTypeMax
};
```

## <a name="elements"></a>Éléments
`LocIsNull` Les informations d’emplacement ne sont pas disponibles.

`LocIsStatic` L’emplacement est statique.

`LocIsTLS` L’emplacement se trouve dans le stockage local des threads.

`LocIsRegRel` L’emplacement est Register-relative.

`LocIsThisRel` L’emplacement est `this` -relative.

`LocIsEnregistered` L’emplacement se trouve dans un registre.

`LocIsBitField` L’emplacement est un champ de bits.

`LocIsSlot` L’emplacement est un emplacement MSIL (Microsoft Intermediate Language).

`LocIsIlRel` L’emplacement est relatif à MSIL.

`LocInMetaData` L’emplacement se trouve dans les métadonnées.

`LocIsConstant` L’emplacement est dans une valeur constante.

`LocTypeMax` Nombre de types d’emplacement dans cette énumération.

## <a name="remarks"></a>Remarques
Les propriétés disponibles pour l’interface [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) dépendent de l’emplacement du symbole dans le fichier image. Pour plus d’informations, consultez [emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md).

Les valeurs de cette énumération sont retournées par un appel à la méthode [IDiaSymbol :: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) .

## <a name="requirements"></a>Configuration requise
En-tête : cvconst. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md)
