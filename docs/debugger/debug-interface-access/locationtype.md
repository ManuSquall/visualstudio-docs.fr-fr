---
title: LocationType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc40cc6cc8e821db7c28a4647e36e7bad241b29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738645"
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
les informations d’emplacement de `LocIsNull` ne sont pas disponibles.

`LocIsStatic` emplacement est statique.

`LocIsTLS` emplacement se trouve dans le stockage local des threads.

`LocIsRegRel` emplacement est Register-relative.

`LocIsThisRel` emplacement est `this` relatif.

`LocIsEnregistered` emplacement se trouve dans un registre.

`LocIsBitField` emplacement est dans un champ de bits.

`LocIsSlot` emplacement est un emplacement MSIL (Microsoft Intermediate Language).

`LocIsIlRel` emplacement est relatif à MSIL.

`LocInMetaData` emplacement se trouve dans les métadonnées.

`LocIsConstant` emplacement est dans une valeur constante.

`LocTypeMax` le nombre de types d’emplacement dans cette énumération.

## <a name="remarks"></a>Notes
Les propriétés disponibles pour l’interface [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) dépendent de l’emplacement du symbole dans le fichier image. Pour plus d’informations, consultez [emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md).

Les valeurs de cette énumération sont retournées par un appel à la méthode [IDiaSymbol :: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) .

## <a name="requirements"></a>spécifications
En-tête : cvconst. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md)
