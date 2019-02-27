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
ms.openlocfilehash: 03e82a8c17b33aa085b4ed64b9ba609bee183e1d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56626113"
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
btNoType Qu'aucun type de base est spécifié.

btVoid type de base est un `void`.

btChar type de base est un `char` (type C/C++).

btWChar type de base est un caractère (Unicode) de large (`WCHAR`).

est de type de base de btInt `signed int` (type C/C++).

est de type de base de btUInt `unsigned int` (type C/C++).

btFloat type de base est un nombre à virgule flottante (`FLOAT`).

btBCD type de base est un nombre décimal codée en binaire (`BCD`).

btBool type de base est une valeur booléenne (`BOOL`).

btLong type de base est un `long int` (type C/C++).

btULong type de base est un `unsigned long int` (type C/C++).

btCurrency type de base est la devise.

btDate type de base est la date/heure (`DATE`).

btVariant type de base est une structure de type de variable (`VARIANT`).

btComplex type de base est un nombre complexe.

btBit type de base est un peu plus tard.

btBSTR type de base est une chaîne binaire ou base (`BSTR`).

btHresult type de base est un `HRESULT`.

## <a name="remarks"></a>Remarques
Les valeurs dans cette énumération sont retournées par la [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) (méthode).

## <a name="requirements"></a>Spécifications
En-tête : cvconst.h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
