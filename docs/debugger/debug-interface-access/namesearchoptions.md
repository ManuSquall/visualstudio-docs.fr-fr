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
ms.openlocfilehash: 61905c0c6c40d893cc8723b711d67690133a7155
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738614"
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

`nsfCaseSensitive` applique une correspondance de nom respectant la casse.

`nsfCaseInsensitive` applique une correspondance de nom qui ne respecte pas la casse.

`nsfFNameExt` traite les noms comme des chemins d’accès et applique une correspondance de nom filename. ext.

`nsfRegularExpression` applique une correspondance de nom respectant la casse à l’aide d’astérisques (*) et de points d’interrogation ( ?) comme caractères génériques. (Les autres caractères d’expressions régulières courantes ne sont pas pris en charge.)

`nsfUndecoratedName` s’applique uniquement aux symboles qui ont des noms non décorés et décorés.

## <a name="remarks"></a>Notes
Les valeurs de cette énumération sont passées aux méthodes suivantes :

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>spécifications
En-tête : Dia2. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
