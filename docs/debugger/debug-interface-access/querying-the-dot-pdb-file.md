---
title: Interrogation de la. Fichier PDB | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a67dc121790acff1f5e39a82a1711317616fc2d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616441"
---
# <a name="querying-the-pdb-file"></a>Interrogation du fichier .Pdb
Un fichier de base de données de programme (.pdb extension) est un fichier binaire qui contient le type et les informations de débogage symboliques collectées au cours de la compilation et liaison du projet. Un fichier PDB est créé lorsque vous compilez un programme C/C++ avec **/Zi** ou **/Zi** ou un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], ou [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] programmer avec le **/debug** option. Fichiers objets contiennent des références dans le fichier .pdb pour les informations de débogage. Pour plus d’informations sur les fichiers pdb, consultez [fichiers PDB](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yd4f8bd1(v=vs.100)). Une application de DIA peut utiliser les étapes générales suivantes pour obtenir des détails sur les différents symboles, les objets et les éléments de données dans une image exécutable.

### <a name="to-query-the-pdb-file"></a>Pour interroger le fichier .pdb

1. Acquérir une source de données en créant un [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) interface.

    ```C++
    CComPtr<IDiaDataSource> pSource;
    hr = CoCreateInstance( CLSID_DiaSource,
                           NULL,
                           CLSCTX_INPROC_SERVER,
                           __uuidof( IDiaDataSource ),
                          (void **) &pSource);

    if (FAILED(hr))
    {
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );
    }
    ```

2. Appelez [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) ou [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) pour charger les informations de débogage.

    ```C++
    wchar_t wszFilename[ _MAX_PATH ];
    mbstowcs( wszFilename, szFilename, sizeof( wszFilename )/sizeof( wszFilename[0] ) );
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )
    {
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )
        {
            Fatal( "loadDataFromPdb/Exe" );
        }
    }
    ```

3. Appelez [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) pour ouvrir un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) pour accéder aux informations de débogage.

    ```C++
    CComPtr<IDiaSession> psession;
    if ( FAILED( pSource->openSession( &psession ) ) )
    {
        Fatal( "openSession" );
    }
    ```

4. Utilisez les méthodes de `IDiaSession` pour rechercher des symboles dans la source de données.

    ```C++
    CComPtr<IDiaSymbol> pglobal;
    if ( FAILED( psession->get_globalScope( &pglobal) ) )
    {
        Fatal( "get_globalScope" );
    }
    ```

5. Utilisez le `IDiaEnum*` interfaces pour énumérer et parcourir les symboles ou d’autres éléments d’informations de débogage.

    ```C++
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    CComPtr< IDiaTable > pTable;
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) ) && celt == 1 )
    {
        // Do something with each IDiaTable.
    }
    ```

## <a name="see-also"></a>Voir aussi
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
