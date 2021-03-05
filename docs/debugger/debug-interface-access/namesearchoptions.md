---
description: Spécifie les options de recherche pour les noms de symboles et de fichiers.
title: NameSearchOptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bd074de0c44803a06d5399f2bd4dc1e3c43618a1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155347"
---
# <a name="namesearchoptions"></a>NameSearchOptions
Spécifie les options de recherche pour les noms de symboles et de fichiers.

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

`nsfCaseSensitive` Applique une correspondance de nom respectant la casse.

`nsfCaseInsensitive` Applique une correspondance de nom ne respectant pas la casse.

`nsfFNameExt` Traite les noms comme des chemins d’accès et applique une correspondance de nom de nom de fichier. ext.

`nsfRegularExpression` Applique une correspondance de nom respectant la casse à l’aide d’astérisques (*) et de points d’interrogation ( ?) comme caractères génériques. (Les autres caractères d’expressions régulières courantes ne sont pas pris en charge.)

`nsfUndecoratedName` S’applique uniquement aux symboles qui ont des noms non décorés et décorés.

## <a name="remarks"></a>Notes
Les valeurs de cette énumération sont passées aux méthodes suivantes :

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Configuration requise
En-tête : Dia2. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
