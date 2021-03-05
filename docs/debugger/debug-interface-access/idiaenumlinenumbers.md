---
description: Énumère les différents numéros de ligne contenus dans la source de données.
title: IDiaEnumLineNumbers | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers interface
ms.assetid: cdf07b4f-19e4-4dcd-8af8-c2dbca586a7c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f7daca5951ba543e69d74c664cddb863ec703e9f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159334"
---
# <a name="idiaenumlinenumbers"></a>IDiaEnumLineNumbers
Énumère les différents numéros de ligne contenus dans la source de données.

## <a name="syntax"></a>Syntaxe

```
IDiaEnumLineNumbers : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant présente les méthodes de `IDiaEnumLineNumbers` .

|Méthode|Description|
|------------|-----------------|
|[IDiaEnumLineNumbers::get__NewEnum](../../debugger/debug-interface-access/idiaenumlinenumbers-get-newenum.md)|Récupère la version d' [interface IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) de cet énumérateur.|
|[IDiaEnumLineNumbers::get_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md)|Récupère le nombre de numéros de ligne.|
|[IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)|Récupère un numéro de ligne au moyen d’un index.|
|[IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md)|Récupère un nombre spécifié de numéros de ligne dans la séquence d’énumération.|
|[IDiaEnumLineNumbers::Skip](../../debugger/debug-interface-access/idiaenumlinenumbers-skip.md)|Ignore un nombre spécifié de numéros de ligne dans une séquence d’énumération.|
|[IDiaEnumLineNumbers::Reset](../../debugger/debug-interface-access/idiaenumlinenumbers-reset.md)|Réinitialise une séquence d'énumération.|
|[IDiaEnumLineNumbers::Clone](../../debugger/debug-interface-access/idiaenumlinenumbers-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|

## <a name="remarks"></a>Notes

## <a name="notes-for-callers"></a>Notes pour les appelants
Cette interface est obtenue en appelant l’une des méthodes suivantes dans l’interface [IDiaSession](../../debugger/debug-interface-access/idiasession.md) :

- [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)

- [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)

- [IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)

- [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)

- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)

## <a name="example"></a>Exemple
Cet exemple montre comment obtenir l' `IDiaEnumLineNumbers` interface à partir d’une session. Dans ce cas, l’exemple montre comment obtenir l’énumération de numéros de ligne pour une fonction (représentée par `pSymbol` ). Pour obtenir un exemple plus complet de l’utilisation de numéros de ligne, consultez l’interface [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) .

```C++
void dumpFunctionLines( IDiaSymbol* pSymbol, IDiaSession* pSession )
{
    ULONGLONG length = 0;
    DWORD isect = 0;
    DWORD offset = 0;
    pSymbol->get_addressSection( &isect );
    pSymbol->get_addressOffset( &offset );
    pSymbol->get_length( &length );
    if ( isect != 0 && length > 0 )
    {
        CComPtr< IDiaEnumLineNumbers > pLines;
        if ( SUCCEEDED( pSession->findLinesByAddr(
                                      isect,
                                      offset,
                                      static_cast<DWORD>( length ),
                                      &pLines )
                      )
           )
        {
            // Do something with the enumeration
        }
    }
}
```

## <a name="requirements"></a>Configuration requise
En-tête : Dia2. h

Bibliothèque : diaguids. lib

DLL : msdia80.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)
- [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)
- [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)
- [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)
