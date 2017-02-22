---
title: "IDiaLineNumber | Microsoft Docs"
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
  - "IDiaLineNumber (interface)"
ms.assetid: 1071f7d0-1f8c-4384-933f-c49c7eb930bd
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IDiaLineNumber
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Accède aux informations qui décrivent le processus du mappage d'un bloc d'octets de texte image à un numéro de ligne du fichier source.  
  
## Syntaxe  
  
```  
IDiaLineNumber : IUnknown  
```  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDiaLineNumber`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaLineNumber::get\_compiland](../../debugger/debug-interface-access/idialinenumber-get-compiland.md)|Extrait une référence au symbole pour le module qui a fourni des octets de texte d'image.|  
|[IDiaLineNumber::get\_sourceFile](../Topic/IDiaLineNumber::get_sourceFile.md)|Extrait une référence à l'objet du fichier source.|  
|[IDiaLineNumber::get\_lineNumber](../Topic/IDiaLineNumber::get_lineNumber.md)|Récupère le numéro de ligne dans le fichier source.|  
|[IDiaLineNumber::get\_lineNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-linenumberend.md)|Récupère le numéro de ligne source de base 1 où l'instruction ou l'expression se termine.|  
|[IDiaLineNumber::get\_columnNumber](../../debugger/debug-interface-access/idialinenumber-get-columnnumber.md)|Récupère le numéro de colonne où l'expression ou l'instruction commence.|  
|[IDiaLineNumber::get\_columnNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-columnnumberend.md)|Récupère le numéro de colonne où l'expression ou l'instruction se termine.|  
|[IDiaLineNumber::get\_addressSection](../../debugger/debug-interface-access/idialinenumber-get-addresssection.md)|Extrait la partie de la section de l'adresse mémoire où un bloc démarre.|  
|[IDiaLineNumber::get\_addressOffset](../../debugger/debug-interface-access/idialinenumber-get-addressoffset.md)|Extrait la partie d'offset de l'adresse mémoire où un bloc démarre.|  
|[IDiaLineNumber::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idialinenumber-get-relativevirtualaddress.md)|Récupère l'adresse virtuelle relative d'image \(RVA\) d'un bloc.|  
|[IDiaLineNumber::get\_virtualAddress](../../debugger/debug-interface-access/idialinenumber-get-virtualaddress.md)|Récupère l'adresse virtuelle \(VA\) d'un bloc.|  
|[IDiaLineNumber::get\_length](../Topic/IDiaLineNumber::get_length.md)|Récupère le nombre d'octets dans un bloc.|  
|[IDiaLineNumber::get\_sourceFileId](../../debugger/debug-interface-access/idialinenumber-get-sourcefileid.md)|Récupère un identificateur unique de fichier source pour le fichier source qui a fourni cette ligne.|  
|[IDiaLineNumber::get\_statement](../Topic/IDiaLineNumber::get_statement.md)|extrait une balise indiquant que ces informations de ligne décrivent le début d'une instruction dans la source de programme.|  
|[IDiaLineNumber::get\_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Extrait l'identificateur unique pour le module qui a fourni cette ligne.|  
  
## Notes  
  
## Remarques pour les appelants  
 obtenez cette interface en appelant les méthodes d' [IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md) ou d' [IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md) .  
  
## Exemple  
 La fonction suivante affiche les numéros de ligne utilisés dans une fonction \(représentée par `pSymbol`\).  
  
```cpp#  
void dumpFunctionLines( IDiaSymbol* pSymbol, IDiaSession* pSession )  
{  
    ULONGLONG length = 0;  
    DWORD     isect  = 0;  
    DWORD     offset = 0;  
  
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
                                      &pLines)  
                      )  
           )  
        {  
            CComPtr< IDiaLineNumber > pLine;  
            DWORD celt      = 0;  
            bool  firstLine = true;  
  
            while ( SUCCEEDED( pLines->Next( 1, &pLine, &celt ) ) &&  
                    celt == 1 )  
            {  
                DWORD offset;  
                DWORD seg;  
                DWORD linenum;  
                CComPtr< IDiaSymbol >     pComp;  
                CComPtr< IDiaSourceFile > pSrc;  
  
                pLine->get_compiland( &pComp );  
                pLine->get_sourceFile( &pSrc );  
                pLine->get_addressSection( &seg );  
                pLine->get_addressOffset( &offset );  
                pLine->get_lineNumber( &linenum );  
                printf( "\tline %d at 0x%x:0x%x\n", linenum, seg, offset );  
                pLine = NULL;  
                if ( firstLine )  
                {  
                    // sanity check  
                    CComPtr< IDiaEnumLineNumbers > pLinesByLineNum;  
                    if ( SUCCEEDED( pSession->findLinesByLinenum(  
                                                  pComp,  
                                                  pSrc,  
                                                  linenum,  
                                                  0,  
                                                  &pLinesByLineNum)  
                                  )  
                       )  
                    {  
                        CComPtr< IDiaLineNumber > pLine;  
                        DWORD celt;  
                        while ( SUCCEEDED( pLinesByLineNum->Next( 1, &pLine, &celt ) ) &&  
                                celt == 1 )  
                        {  
                            DWORD offset;  
                            DWORD seg;  
                            DWORD linenum;  
  
                            pLine->get_addressSection( &seg );  
                            pLine->get_addressOffset( &offset );  
                            pLine->get_lineNumber( &linenum );  
                            printf( "\t\tfound line %d at 0x%x:0x%x\n", linenum, seg, offset );  
                            pLine = NULL;  
                       }  
                    }  
                    firstLine = false;  
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
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)   
 [IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md)