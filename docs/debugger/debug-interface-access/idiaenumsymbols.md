---
title: IDiaEnumSymbols | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols interface
ms.assetid: 649f7bfd-86ac-49a5-8533-aff77e1bc62e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0864522c079ff1f694072fec3147d006cd2ce43d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743896"
---
# <a name="idiaenumsymbols"></a>IDiaEnumSymbols
Énumère les différents symboles contenus dans la source de données.

## <a name="syntax"></a>Syntaxe

```
IDiaEnumSymbols : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant présente les méthodes de `IDiaEnumSymbols`.

|Méthode|Description|
|------------|-----------------|
|[IDiaEnumSymbols::get__NewEnum](../../debugger/debug-interface-access/idiaenumsymbols-get-newenum.md)|Récupère la version `IEnumVARIANT Interface` de cet énumérateur.|
|[IDiaEnumSymbols::get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md)|Récupère le nombre de symboles.|
|[IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)|Récupère un symbole au moyen d’un index.|
|[IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)|Récupère un nombre spécifié de symboles dans la séquence d’énumération.|
|[IDiaEnumSymbols::Skip](../../debugger/debug-interface-access/idiaenumsymbols-skip.md)|Ignore un nombre spécifié de symboles dans une séquence d’énumération.|
|[IDiaEnumSymbols::Reset](../../debugger/debug-interface-access/idiaenumsymbols-reset.md)|Réinitialise une séquence d’énumération au début.|
|[IDiaEnumSymbols::Clone](../../debugger/debug-interface-access/idiaenumsymbols-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|

## <a name="remarks"></a>Notes
Cette interface fournit des symboles regroupés par un type spécifique de symbole, par exemple, `SymTagUDT` (types définis par l’utilisateur) ou `SymTagBaseClass`. Pour travailler avec des symboles regroupés par adresse, utilisez l’interface [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) .

## <a name="notes-for-callers"></a>Notes pour les appelants
Obtenez cette interface en appelant les méthodes suivantes :

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

- [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)

## <a name="example"></a>Exemple
Cet exemple montre comment obtenir l’interface `IDiaEnumSymbols`, puis utiliser cette énumération pour répertorier les types définis par l’utilisateur (UDT).

> [!NOTE]
> `CDiaBSTR` est une classe qui encapsule un `BSTR` et gère automatiquement la libération de la chaîne lorsque l’instanciation est hors de portée.

```C++
void ShowUDTs(IDiaSymbol *pGlobals)
{
    CComPtr<IDiaEnumSymbols> pEnum;
    CComPtr<IDiaSymbol> pSymbol;
    HRESULT hr;

    hr = pGlobals->findChildren(SymTagUDT,
                                NULL,
                                nsfCaseInsensitive | nsfUndecoratedName,
                                &pEnum);
    if (hr == S_OK)
    {
        while ( SUCCEEDED( hr = pEnum->Next( 1, &pSymbol, &celt ) ) &&
                celt == 1 )
        {
            CDiaBSTR name;
            if ( pSymbol->get_name( &name ) != S_OK )
                Fatal( "get_name" );
            printf( "Found UDT: %ws\n", name );
            pSymbol = 0;
        }
    }
}
```

## <a name="requirements"></a>spécifications
En-tête : Dia2. h

Bibliothèque : diaguids. lib

DLL : Msdia80. dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
