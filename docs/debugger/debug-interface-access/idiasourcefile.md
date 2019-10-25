---
title: IDiaSourceFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile interface
ms.assetid: 6e9be757-797f-4960-ba62-c14092620bbd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08334c59ea061cee1618c76aa61ec6aa6fb8d7d4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741776"
---
# <a name="idiasourcefile"></a>IDiaSourceFile
Représente un fichier source.

## <a name="syntax"></a>Syntaxe

```
IDiaSourceFile : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant présente les méthodes de `IDiaSourceFile`.

|Méthode|Description|
|------------|-----------------|
|[IDiaSourceFile::get_uniqueId](../../debugger/debug-interface-access/idiasourcefile-get-uniqueid.md)|Récupère une valeur de clé entière simple qui est unique pour cette image.|
|[IDiaSourceFile::get_fileName](../../debugger/debug-interface-access/idiasourcefile-get-filename.md)|Récupère le nom du fichier source.|
|[IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)|Récupère le type de somme de contrôle.|
|[IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)|Récupère un énumérateur du compilands avec des numéros de ligne référençant ce fichier.|
|[IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)|Récupère les octets de somme de contrôle.|

## <a name="remarks"></a>Notes

## <a name="notes-for-callers"></a>Notes pour les appelants
Obtenez cette interface en appelant les méthodes [IDiaEnumSourceFiles :: Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md) ou [IDiaEnumSourceFiles :: Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md) . Pour plus d’informations, consultez l’exemple.

## <a name="example"></a>Exemple
Cette fonction affiche les noms de tous les fichiers sources contribuant à la table spécifiée.

```C++
void ShowSourceFiles(IDiaTable *pTable)
{
    CComPtr<IDiaEnumSourceFiles> pSourceFiles;
    if ( SUCCEEDED( pTable->QueryInterface(
                                _uuidof( IDiaEnumSourceFiles ),
                               (void**)&pSourceFiles )
                  )
       )
    {
        CComPtr<IDiaSourceFile> pSourceFile;
        while ( SUCCEEDED( hr = pSourceFiles->Next( 1, &pSourceFile, &celt ) ) &&
                celt == 1 )
        {
            CDiaBSTR fileName;
            if ( pSourceFile->get_fileName( &fileName) == S_OK )
            {
                printf( "file name: %ws\n", fileName );
            }
            pSourceFile = NULL;
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
- [IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)
- [IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)
- [IDiaLineNumber::get_sourceFile](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)
- [IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)
- [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
