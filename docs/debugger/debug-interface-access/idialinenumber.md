---
title: IDiaLineNumber | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber interface
ms.assetid: 1071f7d0-1f8c-4384-933f-c49c7eb930bd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 62552c6cce3c17da52de14669071bec43db548de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864704"
---
# <a name="idialinenumber"></a>IDiaLineNumber
Accède aux informations qui décrivent le processus de mappage d’un bloc d’octets de texte image à un numéro de ligne de fichier source.

## <a name="syntax"></a>Syntaxe

```
IDiaLineNumber : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant présente les méthodes de `IDiaLineNumber` .

|Méthode|Description|
|------------|-----------------|
|[IDiaLineNumber::get_compiland](../../debugger/debug-interface-access/idialinenumber-get-compiland.md)|Récupère une référence au symbole du compiland qui a contribué aux octets du texte de l’image.|
|[IDiaLineNumber::get_sourceFile](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)|Récupère une référence à l’objet de fichier source.|
|[IDiaLineNumber::get_lineNumber](../../debugger/debug-interface-access/idialinenumber-get-linenumber.md)|Récupère le numéro de ligne dans le fichier source.|
|[IDiaLineNumber::get_lineNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-linenumberend.md)|Récupère le numéro de ligne source de base 1 où l’instruction ou l’expression se termine.|
|[IDiaLineNumber::get_columnNumber](../../debugger/debug-interface-access/idialinenumber-get-columnnumber.md)|Récupère le numéro de colonne où l’expression ou l’instruction commence.|
|[IDiaLineNumber::get_columnNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-columnnumberend.md)|Récupère le numéro de colonne où l’expression ou l’instruction se termine.|
|[IDiaLineNumber::get_addressSection](../../debugger/debug-interface-access/idialinenumber-get-addresssection.md)|Récupère la partie de la section de l’adresse mémoire à laquelle commence un bloc.|
|[IDiaLineNumber::get_addressOffset](../../debugger/debug-interface-access/idialinenumber-get-addressoffset.md)|Récupère la partie offset de l’adresse mémoire à laquelle commence un bloc.|
|[IDiaLineNumber::get_relativeVirtualAddress](../../debugger/debug-interface-access/idialinenumber-get-relativevirtualaddress.md)|Récupère l’adresse virtuelle relative (RVA) d’une image d’un bloc.|
|[IDiaLineNumber::get_virtualAddress](../../debugger/debug-interface-access/idialinenumber-get-virtualaddress.md)|Récupère l’adresse virtuelle (VA) d’un bloc.|
|[IDiaLineNumber::get_length](../../debugger/debug-interface-access/idialinenumber-get-length.md)|Récupère le nombre d’octets dans un bloc.|
|[IDiaLineNumber::get_sourceFileId](../../debugger/debug-interface-access/idialinenumber-get-sourcefileid.md)|Récupère un identificateur de fichier source unique pour le fichier source qui a participé à cette ligne.|
|[IDiaLineNumber::get_statement](../../debugger/debug-interface-access/idialinenumber-get-statement.md)|Récupère un indicateur qui spécifie que ces informations de ligne décrivent le début d’une instruction dans la source du programme.|
|[IDiaLineNumber::get_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Récupère l’identificateur unique pour le compiland qui a participé à cette ligne.|

## <a name="remarks"></a>Remarques

## <a name="notes-for-callers"></a>Notes pour les appelants
Obtenez cette interface en appelant les méthodes [IDiaEnumLineNumbers :: Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md) ou [IDiaEnumLineNumbers :: Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md) .

## <a name="example"></a>Exemple
La fonction suivante affiche les numéros de ligne utilisés dans une fonction (représentée par `pSymbol` ).

```C++
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

## <a name="requirements"></a>Configuration requise
En-tête : Dia2. h

Bibliothèque : diaguids. lib

DLL : msdia80.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)
- [IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md)
