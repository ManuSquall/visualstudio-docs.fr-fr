---
title: NameSearchOptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7dbb82946d185e8e5ec81b171f5d9943751eee4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855152"
---
# <a name="namesearchoptions"></a>NameSearchOptions
Spécifie les options de recherche pour les noms de fichiers et de symboles.

## <a name="syntax"></a>Syntaxe

```C++
enum NameSearchOptions {
    nsNone,
    nsfCaseSensitive     = 0x1,
    nsfCaseInsensitive   = 0x2,
    nsfFNameExt          = 0x4,
    nsfRegularExpression = 0x8,
    nsfUndecoratedName   = 0x10,

// For backward compatibility:
    nsCaseSensitive           = nsfCaseSensitive,
    nsCaseInsensitive         = nsfCaseInsensitive,
    nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,
    nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,
    nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive
};
```

## <a name="elements"></a>Éléments
`nsNone` Aucune option n’est spécifiée.

`nsfCaseSensitive` S’applique une correspondance de nom respectant la casse.

`nsfCaseInsensitive` S’applique une correspondance de nom de non-respect de la casse.

`nsfFNameExt` Traite les noms en tant que chemins d’accès et s’applique à une correspondance de nom NomFicher.ext.

`nsfRegularExpression` S’applique une correspondance de nom respectant la casse à l’aide d’astérisques (*) et les points d’interrogation ( ?) comme caractères génériques.

`nsfUndecoratedName` S’applique uniquement aux symboles qui ont à la fois non décorés et les noms décorés.

## <a name="remarks"></a>Notes
Les valeurs de cette énumération sont passées aux méthodes suivantes :

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Configuration requise
En-tête : dia2.h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
