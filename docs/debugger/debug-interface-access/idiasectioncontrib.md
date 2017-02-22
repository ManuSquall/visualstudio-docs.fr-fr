---
title: "IDiaSectionContrib | Microsoft Docs"
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
  - "IDiaSectionContrib (interface)"
ms.assetid: 371d40f6-ca0e-4d7e-9210-64d3768996c6
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IDiaSectionContrib
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère les données qui décrit une contribution de section, c. autrement dit., un bloc de mémoire contigu fourni à l'image selon un module \(compiland\).  
  
## Syntaxe  
  
```  
IDiaSectionContrib : IUnknown  
```  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDiaSectionContrib`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaSectionContrib::get\_compiland](../../debugger/debug-interface-access/idiasectioncontrib-get-compiland.md)|Extrait une référence au symbole de module qui a fourni cette section.|  
|[IDiaSectionContrib::get\_addressSection](../../debugger/debug-interface-access/idiasectioncontrib-get-addresssection.md)|Extrait la partie de la section de l'adresse de la contribution.|  
|[IDiaSectionContrib::get\_addressOffset](../../debugger/debug-interface-access/idiasectioncontrib-get-addressoffset.md)|Extrait la partie d'offset de l'adresse de la contribution.|  
|[IDiaSectionContrib::get\_relativeVirtualAddress](../Topic/IDiaSectionContrib::get_relativeVirtualAddress.md)|Récupère l'adresse virtuelle relative de l'image \(RVA\) de la contribution.|  
|[IDiaSectionContrib::get\_virtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-virtualaddress.md)|Récupère l'adresse \(VA\) virtuelle de la contribution.|  
|[IDiaSectionContrib::get\_length](../../debugger/debug-interface-access/idiasectioncontrib-get-length.md)|Récupère le nombre d'octets dans une section.|  
|[IDiaSectionContrib::get\_notPaged](../../debugger/debug-interface-access/idiasectioncontrib-get-notpaged.md)|extrait une balise qui indique si la section ne peut pas être mémoire insuffisante paginé.|  
|[IDiaSectionContrib::get\_nopad](../../debugger/debug-interface-access/idiasectioncontrib-get-nopad.md)|Extrait une balise qui indique si la section ne doit pas être effectuée à la limite suivante de mémoire.|  
|[IDiaSectionContrib::get\_code](../Topic/IDiaSectionContrib::get_code.md)|Extrait une balise qui indique si la section contient le code exécutable.|  
|[IDiaSectionContrib::get\_code16bit](../../debugger/debug-interface-access/idiasectioncontrib-get-code16bit.md)|Extrait une balise qui indique si la section contient le code 16 bits.|  
|[IDiaSectionContrib::get\_initializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-initializeddata.md)|extrait une balise qui indique si la section contient des données initialisées.|  
|[IDiaSectionContrib::get\_uninitializedData](../Topic/IDiaSectionContrib::get_uninitializedData.md)|extrait une balise qui indique si la section contient des données non initialisées.|  
|[IDiaSectionContrib::get\_informational](../../debugger/debug-interface-access/idiasectioncontrib-get-informational.md)|Extrait une balise indiquant si une section contient les commentaires ou les informations similaires.|  
|[IDiaSectionContrib::get\_remove](../../debugger/debug-interface-access/idiasectioncontrib-get-remove.md)|Extrait une balise qui indique si la section est supprimée pour que ce soit effectué à une partie de l'image en mémoire.|  
|[IDiaSectionContrib::get\_comdat](../../debugger/debug-interface-access/idiasectioncontrib-get-comdat.md)|Extrait une balise qui indique si la section est un enregistrement COMDAT.|  
|[IDiaSectionContrib::get\_discardable](../../debugger/debug-interface-access/idiasectioncontrib-get-discardable.md)|extrait une balise qui indique si la section peut être ignorée.|  
|[IDiaSectionContrib::get\_notCached](../../debugger/debug-interface-access/idiasectioncontrib-get-notcached.md)|extrait une balise qui indique si la section ne peut pas être mise en cache.|  
|[IDiaSectionContrib::get\_share](../../debugger/debug-interface-access/idiasectioncontrib-get-share.md)|extrait une balise qui indique si la section peut être partagée dans la mémoire.|  
|[IDiaSectionContrib::get\_execute](../../debugger/debug-interface-access/idiasectioncontrib-get-execute.md)|Extrait une balise qui indique si la section est exécutable comme du code.|  
|[IDiaSectionContrib::get\_read](../../debugger/debug-interface-access/idiasectioncontrib-get-read.md)|Extrait une balise qui indique si la section peuvent être lues.|  
|[IDiaSectionContrib::get\_write](../../debugger/debug-interface-access/idiasectioncontrib-get-write.md)|extrait une balise qui indique si la section peut être écrite.|  
|[IDiaSectionContrib::get\_dataCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-datacrc.md)|Récupère le contrôle de \(CRC\) redondance cyclique des données dans la section.|  
|[IDiaSectionContrib::get\_relocationsCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-relocationscrc.md)|Extrait CRC des informations de réadressage de la section.|  
|[IDiaLineNumber::get\_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Extrait l'identificateur de module \(compiland\) de la section.|  
  
## Notes  
  
## Remarques pour les appelants  
 cette interface est obtenue en appelant les méthodes d' [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md) et d' [IDiaEnumSectionContribs::Next](../Topic/IDiaEnumSectionContribs::Next.md) .  Consultez l'interface d' [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) pour obtenir un exemple d'obtenir `IDiaSectionContrib` pour relier.  
  
## Exemple  
 Cette fonction illustre l'adresse de chaque section ainsi que tous les symboles associés.  Consultez l'interface d' [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) pour voir comment l'interface d' `IDiaSectionContrib` est obtenue.  
  
```cpp#  
void PrintSectionContrib(IDiaSectionContrib* pSecContrib, IDiaSession* pSession)  
{  
    if (pSecContrib != NULL && pSession != NULL)  
    {  
        DWORD rva;  
        if ( pSecContrib->get_relativeVirtualAddress( &rva ) == S_OK )  
        {  
            printf( "\taddr: 0x%.8X", rva );  
            pSecContrib = NULL;  
            CComPtr<IDiaSymbol> pSym;  
            if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )  
            {  
                CDiaBSTR name;  
                DWORD    tag;  
                pSym->get_symTag( &tag );  
                pSym->get_name( &name );  
                printf( "     symbol: %ws (%ws)\n",  
                        name != NULL ? name : L"",  
                        szTags[ tag ] );  
            }  
            else  
            {  
                printf( "<no symbol found?>\n" );  
            }  
        }  
        else  
        {  
            DWORD isect;  
            DWORD offset;  
            pSecContrib->get_addressSection( &isect );  
            pSecContrib->get_addressOffset( &offset );  
            printf( "\taddr: 0x%.4X:0x%.8X", isect, offset );  
            pSecContrib = NULL;  
            CComPtr<IDiaSymbol> pSym;  
            if ( SUCCEEDED( psession->findSymbolByAddr(  
                                              isect,  
                                              offset,  
                                              SymTagNull,  
                                              &pSym )  
                          )  
               )  
            {  
                CDiaBSTR name;  
                DWORD    tag;  
                pSym->get_symTag( &tag );  
                pSym->get_name( &name );  
                printf( "     symbol: %ws (%ws)\n",  
                    name != NULL ? name : L"",  
                    szTags[ tag ] );  
            }  
            else  
            {  
                printf( "<no symbol found?>\n" );  
            }  
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
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)   
 [IDiaEnumSectionContribs::Next](../Topic/IDiaEnumSectionContribs::Next.md)