---
title: "IDiaEnumSymbols | Microsoft Docs"
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
  - "IDiaEnumSymbols (interface)"
ms.assetid: 649f7bfd-86ac-49a5-8533-aff77e1bc62e
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IDiaEnumSymbols
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

énumère les différents symboles contenus dans la source de données.  
  
## Syntaxe  
  
```  
IDiaEnumSymbols : IUnknown  
```  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDiaEnumSymbols`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaEnumSymbols::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsymbols-get-newenum.md)|Récupère la version d' `IEnumVARIANT Interface` de cet énumérateur.|  
|[IDiaEnumSymbols::get\_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md)|Récupère le nombre de symboles.|  
|[IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)|Récupère un symbole au moyen d'un index.|  
|[IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)|Récupère un nombre spécifié de symboles dans la séquence d'énumération.|  
|[IDiaEnumSymbols::Skip](../../debugger/debug-interface-access/idiaenumsymbols-skip.md)|Ignore un nombre spécifié de symboles dans une séquence d'énumération.|  
|[IDiaEnumSymbols::Reset](../../debugger/debug-interface-access/idiaenumsymbols-reset.md)|réinitialise une séquence d'énumération au début.|  
|[IDiaEnumSymbols::Clone](../../debugger/debug-interface-access/idiaenumsymbols-clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
  
## Notes  
 Cette interface fournit les symboles regroupés par un type spécifique de symbole, par exemple, d' `SymTagUDT` \(types définis par l'utilisateur\) ou d' `SymTagBaseClass`.  Pour utiliser des symboles regroupés par l'adresse, utilisez l'interface d' [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) .  
  
## Remarques pour les appelants  
 obtenez cette interface en appelant les méthodes suivantes :  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
-   [IDiaSourceFile::get\_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)  
  
## Exemple  
 Cet exemple montre comment obtenir l'interface d' `IDiaEnumSymbols` puis utiliser cette énumération pour répertorier les types définis par l'utilisateur \(UDTs\).  
  
> [!NOTE]
>  `CDiaBSTR` est une classe qui encapsule `BSTR` et automatiquement les handles libérant la chaîne lorsque l'instanciation est hors de portée.  
  
```cpp#  
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
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## Voir aussi  
 [Interfaces \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSourceFile::get\_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)