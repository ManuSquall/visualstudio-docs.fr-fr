---
title: IDiaSegment | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment interface
ms.assetid: 384ae0e1-077e-4d4f-98de-ac43c32c882f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 855b40f3d35d884a366e8fdc36ed1ec4f2bef85a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742340"
---
# <a name="idiasegment"></a>IDiaSegment
Mappe les données du numéro de section aux segments de l’espace d’adressage.

## <a name="syntax"></a>Syntaxe

```
IDiaSegment : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant présente les méthodes de `IDiaSegment`.

|Méthode|Description|
|------------|-----------------|
|[IDiaSegment::get_frame](../../debugger/debug-interface-access/idiasegment-get-frame.md)|Récupère le numéro de segment.|
|[IDiaSegment::get_offset](../../debugger/debug-interface-access/idiasegment-get-offset.md)|Récupère le décalage dans les segments où commence la section.|
|[IDiaSegment::get_length](../../debugger/debug-interface-access/idiasegment-get-length.md)|Récupère le nombre d’octets dans le segment.|
|[IDiaSegment::get_read](../../debugger/debug-interface-access/idiasegment-get-read.md)|Récupère un indicateur qui signale si le segment peut être lu.|
|[IDiaSegment::get_write](../../debugger/debug-interface-access/idiasegment-get-write.md)|Récupère un indicateur qui signale si le segment peut être modifié.|
|[IDiaSegment::get_execute](../../debugger/debug-interface-access/idiasegment-get-execute.md)|Récupère un indicateur qui signale si le segment est exécutable.|
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|Récupère le numéro de section mappé à ce segment.|
|[IDiaSegment::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasegment-get-relativevirtualaddress.md)|Récupère l’adresse virtuelle relative (RVA) du début de la section.|
|[IDiaSegment::get_virtualAddress](../../debugger/debug-interface-access/idiasegment-get-virtualaddress.md)|Récupère l’adresse virtuelle (VA) du début de la section.|

## <a name="remarks"></a>Notes
Étant donné que le kit de développement logiciel (SDK) DIA effectue déjà des traductions du décalage de section vers des adresses virtuelles relatives, la plupart des applications n’utilisent pas les informations de la carte de segment.

## <a name="notes-for-callers"></a>Notes pour les appelants
Obtenez cette interface en appelant les méthodes [IDiaEnumSegments :: Item](../../debugger/debug-interface-access/idiaenumsegments-item.md) ou [IDiaEnumSegments :: Next](../../debugger/debug-interface-access/idiaenumsegments-next.md) . Pour plus d’informations, consultez l’exemple.

## <a name="example"></a>Exemple
Cette fonction affiche l’adresse de tous les segments d’une table et le symbole le plus proche.

```C++
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

## <a name="requirements"></a>spécifications
En-tête : Dia2. h

Bibliothèque : diaguids. lib

DLL : Msdia80. dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)
- [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)
