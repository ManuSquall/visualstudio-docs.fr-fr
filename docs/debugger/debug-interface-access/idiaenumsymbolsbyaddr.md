---
title: IDiaEnumSymbolsByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsbyAddr interface
ms.assetid: 37d3dcdf-e4fa-4354-b5e1-8843566b52ac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d8cddaa39635be534e2247b48a370ed88b29ab4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743811"
---
# <a name="idiaenumsymbolsbyaddr"></a>IDiaEnumSymbolsByAddr
Énumère par adresse les différents symboles contenus dans la source de données.

## <a name="syntax"></a>Syntaxe

```
IDiaEnumSymbolsByAddr : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant présente les méthodes de `IDiaEnumSymbolsByAddr`.

|Méthode|Description|
|------------|-----------------|
|[IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)|Positionne l’énumérateur en effectuant une recherche par section et décalage.|
|[IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)|Positionne l’énumérateur en effectuant une recherche par adresse virtuelle relative (RVA).|
|[IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)|Positionne l’énumérateur en effectuant une recherche par adresse virtuelle (VA).|
|[IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)|Récupère les symboles suivants dans l’ordre par adresse. Met à jour la position de l’énumérateur en fonction du nombre d’éléments extraits.|
|[IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)|Récupère les symboles précédents dans l’ordre par adresse. Met à jour la position de l’énumérateur en fonction du nombre d’éléments extraits.|
|[IDiaEnumSymbolsByAddr::Clone](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-clone.md)|Effectue une copie d’un objet.|

## <a name="remarks"></a>Notes
Cette interface fournit des symboles regroupés par adresse. Pour utiliser des symboles regroupés par type, par exemple `SymTagUDT` (type défini par l’utilisateur) ou `SymTagBaseClass`, utilisez l’interface [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) .

## <a name="notes-for-callers"></a>Notes pour les appelants
Obtenez cette interface en appelant la méthode [IDiaSession :: getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md) .

## <a name="example"></a>Exemple
Cette fonction affiche le nom et l’adresse de tous les symboles classés par adresse virtuelle relative.

```C++
void ShowSymbolsByAddress(IDiaSession *pSession)
{
    CComPtr<IDiaEnumSymbolsByAddr> pEnumByAddr;
    if ( FAILED( psession->getSymbolsByAddr( &pEnumByAddr ) ) )
    {
        Fatal( "getSymbolsByAddr" );
    }
    CComPtr<IDiaSymbol> pSym;
    if ( FAILED( pEnumByAddr->symbolByAddr( 1, 0, &pSym ) ) )
    {
        Fatal( "symbolByAddr" );
    }
    DWORD rvaLast = 0;
    if ( pSym->get_relativeVirtualAddress( &rvaLast ) == S_OK )
    {
        pSym = 0;
        if ( FAILED( pEnumByAddr->symbolByRVA( rvaLast, &pSym ) ) )
        {
            Fatal( "symbolByAddr" );
        }
        printf( "Symbols in order\n" );
        do
        {
            CDiaBSTR name;
            if ( pSym->get_name( &name ) != S_OK )
            {
                printf( "\t0x%08X (%ws) <no name>\n", rvaLast );
            }
            else
            {
                printf( "\t0x%08X %ws\n", rvaLast, name );
            }
            pSym = 0;
            celt = 0;
            if ( FAILED( hr = pEnumByAddr->Next( 1, &pSym, &celt ) ) )
            {
                break;
            }
        } while ( celt == 1 );
    }
}
```

## <a name="requirements"></a>spécifications
En-tête : Dia2. h

Bibliothèque : diaguids. lib

DLL : Msdia80. dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
