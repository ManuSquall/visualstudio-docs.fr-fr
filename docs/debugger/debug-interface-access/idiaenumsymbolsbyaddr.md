---
title: "IDiaEnumSymbolsByAddr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumSymbolsbyAddr (interface)"
ms.assetid: 37d3dcdf-e4fa-4354-b5e1-8843566b52ac
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaEnumSymbolsByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Énumère par l'adresse que différents symboles auront contenue dans la source de données.  
  
## Syntaxe  
  
```  
IDiaEnumSymbolsByAddr : IUnknown  
```  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDiaEnumSymbolsByAddr`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)|positionne l'énumérateur en effectuant une recherche par la section et l'offset.|  
|[IDiaEnumSymbolsByAddr::symbolByRVA](../Topic/IDiaEnumSymbolsByAddr::symbolByRVA.md)|Positionne l'énumérateur en effectuant une recherche par l'adresse virtuelle associée \(RVA\).|  
|[IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)|positionne l'énumérateur en effectuant une recherche par l'adresse virtuelle \(VA\).|  
|[IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)|Récupère les symboles ci\-dessous dans l'ordre par l'adresse.  Met à jour la position d'énumérateur par le nombre d'éléments récupérés.|  
|[IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)|Récupère les symboles précédents dans l'ordre par l'adresse.  Met à jour la position d'énumérateur par le nombre d'éléments récupérés.|  
|[IDiaEnumSymbolsByAddr::Clone](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-clone.md)|Effectue une copie d'un objet.|  
  
## Notes  
 Cette interface fournit les symboles regroupés par l'adresse.  Pour utiliser des symboles regroupés par type, par exemple `SymTagUDT` \(type défini par l'utilisateur\) ou `SymTagBaseClass`, utilisez l'interface d' [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) .  
  
## Remarques pour les appelants  
 obtenez cette interface en appelant la méthode d' [IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md) .  
  
## Exemple  
 Cette fonction affiche le nom et l'adresse de tous les symboles classés par l'adresse virtuelle associée.  
  
```cpp#  
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
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## Voir aussi  
 [Interfaces \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)