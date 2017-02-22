---
title: "IDiaSegment | Microsoft Docs"
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
  - "IDiaSegment (interface)"
ms.assetid: 384ae0e1-077e-4d4f-98de-ac43c32c882f
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IDiaSegment
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Données de mappage du nombre de section aux segments de l'espace d'adressage.  
  
## Syntaxe  
  
```  
IDiaSegment : IUnknown  
```  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDiaSegment`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaSegment::get\_frame](../../debugger/debug-interface-access/idiasegment-get-frame.md)|Récupère le numéro du segment.|  
|[IDiaSegment::get\_offset](../../debugger/debug-interface-access/idiasegment-get-offset.md)|Récupère l'offset dans les segments où la section démarre.|  
|[IDiaSegment::get\_length](../../debugger/debug-interface-access/idiasegment-get-length.md)|Récupère le nombre d'octets dans le segment.|  
|[IDiaSegment::get\_read](../../debugger/debug-interface-access/idiasegment-get-read.md)|extrait une balise qui indique si le segment peut être lu.|  
|[IDiaSegment::get\_write](../../debugger/debug-interface-access/idiasegment-get-write.md)|extrait une balise qui indique si le segment peut être modifié.|  
|[IDiaSegment::get\_execute](../../debugger/debug-interface-access/idiasegment-get-execute.md)|extrait une balise qui indique si le segment est exécutable.|  
|[IDiaSegment::get\_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|Récupère le numéro de section mappée à ce segment.|  
|[IDiaSegment::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasegment-get-relativevirtualaddress.md)|Récupère l'adresse virtuelle relative \(RVA\) du début de la section.|  
|[IDiaSegment::get\_virtualAddress](../../debugger/debug-interface-access/idiasegment-get-virtualaddress.md)|Récupère l'adresse \(VA\) virtuelle de début de la section.|  
  
## Notes  
 Étant donné que le diamètre Kit de développement logiciel exécute déjà les traductions de la section décalés à des adresses virtuelles relatives, la plupart des applications ne se serviront pas des informations dans le mappage de segment.  
  
## Remarques pour les appelants  
 obtenez cette interface en appelant les méthodes d' [IDiaEnumSegments::Item](../Topic/IDiaEnumSegments::Item.md) ou d' [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md) .  Consultez l'exemple pour plus de détails.  
  
## Exemple  
 cette fonction affiche l'adresse de tous les segments dans un tableau et le symbole le plus proche.  
  
```cpp#  
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pSegments;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                _uuidof( IDiaEnumSegments ),  
                               (void**)&pSegments )  
                  )  
       )  
    {  
        CComPtr<IDiaSegment> pSegment;  
        while ( SUCCEEDED( hr = pSegments->Next( 1, &pSegment, &celt ) ) &&  
                celt == 1 )  
        {  
            DWORD rva;  
            DWORD seg;  
  
            pSegment->get_addressSection( &seg );  
            if ( pSegment->get_relativeVirtualAddress( &rva ) == S_OK )  
            {  
                printf( "Segment %i addr: 0x%.8X\n", seg, rva );  
                pSegment = NULL;  
  
                CComPtr<IDiaSymbol> pSym;  
                if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )  
                {  
                    CDiaBSTR name;  
                    DWORD    tag;  
  
                    pSym->get_symTag( &tag );  
                    pSym->get_name( &name );  
                    printf( "\tClosest symbol: %ws (%ws)\n",  
                            name != NULL ? name : L"",  
                            szTags[ tag ] );  
                }  
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
 [IDiaEnumSegments::Item](../Topic/IDiaEnumSegments::Item.md)   
 [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)