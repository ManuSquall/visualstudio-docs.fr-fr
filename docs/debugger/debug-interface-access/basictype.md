---
title: BasicType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fff76abdecdd8613a462225278053ef4f6d9694
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745475"
---
# <a name="basictype"></a>BasicType
Spécifie le type de base du symbole.

## <a name="syntax"></a>Syntaxe

```C++
enum BasicType {
    btNoType   = 0,
    btVoid     = 1,
    btChar     = 2,
    btWChar    = 3,
    btInt      = 6,
    btUInt     = 7,
    btFloat    = 8,
    btBCD      = 9,
    btBool     = 10,
    btLong     = 13,
    btULong    = 14,
    btCurrency = 25,
    btDate     = 26,
    btVariant  = 27,
    btComplex  = 28,
    btBit      = 29,
    btBSTR     = 30,
    btHresult  = 31,
    btChar16   = 32,  // char16_t
    btChar32   = 33,  // char32_t
};
```

## <a name="elements"></a>Éléments
btNoType aucun type de base n’est spécifié.

btVoid type de base est un `void`.

btChar type de base est un `char` (CC++ /type).

btWChar type de base est un caractère étendu (Unicode) (`WCHAR`).

btInt type de base est `signed int` (CC++ /type).

btUInt type de base est `unsigned int` (CC++ /type).

btFloat type de base est un nombre à virgule flottante (`FLOAT`).

btBCD type de base est un nombre décimal codé binaire (`BCD`).

btBool type de base est un booléen (`BOOL`).

btLong type de base est un `long int` (CC++ /type).

btULong type de base est un `unsigned long int` (CC++ /type).

btCurrency type de base est Currency.

btDate type de base est date/heure (`DATE`).

btVariant type de base est une structure de type variable (`VARIANT`).

btComplex type de base est un nombre complexe.

btBit type de base est un peu.

btBSTR Basic type est une chaîne de base ou binaire (`BSTR`).

btHresult type de base est un `HRESULT`.

## <a name="remarks"></a>Notes
Les valeurs de cette énumération sont retournées par la méthode [IDiaSymbol :: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) .

## <a name="requirements"></a>spécifications
En-tête : cvconst. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
