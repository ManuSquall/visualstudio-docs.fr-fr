---
description: Un fichier de base de données de programme (extension. pdb) est un fichier binaire qui contient des informations de débogage de type et symboliques rassemblées au cours de la compilation et de la liaison du projet.
title: Interrogation de. Fichier PDB | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ea69572304feb5bb2fcb2ef91c0f94a96c138cf7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161661"
---
# <a name="querying-the-pdb-file"></a>Interrogation du fichier .Pdb
Un fichier de base de données de programme (extension. pdb) est un fichier binaire qui contient des informations de débogage de type et symboliques rassemblées au cours de la compilation et de la liaison du projet. Un fichier PDB est créé quand vous compilez un programme C/C++ avec **/Zi** ou **/Zi** , ou un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] programme, ou [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] avec l’option **/Debug** . Les fichiers objets contiennent des références dans le fichier. pdb pour les informations de débogage. Pour plus d’informations sur les fichiers PDB, consultez [fichiers PDB](/previous-versions/visualstudio/visual-studio-2010/yd4f8bd1(v=vs.100)). Une application DIA peut utiliser les étapes générales suivantes pour obtenir des détails sur les différents symboles, objets et éléments de données dans une image exécutable.

### <a name="to-query-the-pdb-file"></a>Pour interroger le fichier. pdb

1. Acquérir une source de données en créant une interface [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) .

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

2. Appelez [IDiaDataSource :: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) ou [IDiaDataSource :: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) pour charger les informations de débogage.

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

3. Appelez [IDiaDataSource :: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) pour ouvrir un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) afin d’accéder aux informations de débogage.

    ```C++
    CComPtr<IDiaSession> psession;
    if ( FAILED( pSource->openSession( &psession ) ) )
    {
        Fatal( "openSession" );
    }
    ```

4. Utilisez les méthodes dans `IDiaSession` pour rechercher les symboles dans la source de données.

    ```C++
    CComPtr<IDiaSymbol> pglobal;
    if ( FAILED( psession->get_globalScope( &pglobal) ) )
    {
        Fatal( "get_globalScope" );
    }
    ```

5. Utilisez les `IDiaEnum*` interfaces pour énumérer et analyser les symboles ou d’autres éléments des informations de débogage.

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
