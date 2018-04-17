---
title: IDiaEnumSymbolsByAddr | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsbyAddr interface
ms.assetid: 37d3dcdf-e4fa-4354-b5e1-8843566b52ac
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa96dd55ca3ccdbd047641d01a4123b0ad70a7a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idiaenumsymbolsbyaddr"></a>IDiaEnumSymbolsByAddr
Énumère les différents symboles contenus dans la source de données par adresse.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaEnumSymbolsByAddr : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDiaEnumSymbolsByAddr`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)|Place l’énumérateur en effectuant une recherche par section et le décalage.|  
|[IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)|Place l’énumérateur en effectuant une recherche par adresse virtuelle relative (RVA).|  
|[IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)|Place l’énumérateur en effectuant une recherche par adresse virtuelle (VA).|  
|[IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)|Récupère les symboles suivants dans l’ordre par adresse. Met à jour la position de l’énumérateur par nombre d’éléments extraits.|  
|[IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)|Récupère les symboles précédentes dans l’ordre par adresse. Met à jour la position de l’énumérateur par nombre d’éléments extraits.|  
|[IDiaEnumSymbolsByAddr::Clone](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-clone.md)|Effectue une copie d’un objet.|  
  
## <a name="remarks"></a>Notes  
 Cette interface fournit des symboles groupés par adresse. Pour travailler avec des symboles regroupées par type, par exemple `SymTagUDT` (type défini par l’utilisateur) ou `SymTagBaseClass`, utilisez le [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Obtenez cette interface en appelant le [IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md) (méthode).  
  
## <a name="example"></a>Exemple  
 Cette fonction affiche le nom et l’adresse de tous les symboles sont classés par adresse virtuelle relative.  
  
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
  
## <a name="requirements"></a>Spécifications  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)