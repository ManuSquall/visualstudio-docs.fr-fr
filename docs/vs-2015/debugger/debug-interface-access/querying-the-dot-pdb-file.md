---
title: Interrogation de la. Fichier PDB | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d056224d23f487abf25776a52ca80079c08a9f5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236065"
---
# <a name="querying-the-pdb-file"></a>Interrogation du fichier .Pdb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un fichier de base de données de programme (.pdb extension) est un fichier binaire qui contient le type et les informations de débogage symboliques collectées au cours de la compilation et liaison du projet. Un fichier PDB est créé lorsque vous compilez un programme C/C++ avec **/Zi** ou **/Zi** ou un [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], ou [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] programmer avec le **/debug** option. Fichiers objets contiennent des références dans le fichier .pdb pour les informations de débogage. Pour plus d’informations sur les fichiers pdb, consultez [fichiers PDB](http://msdn.microsoft.com/en-us/1761c84e-8c2c-4632-9649-b5f99964ed3f). Une application de DIA peut utiliser les étapes générales suivantes pour obtenir des détails sur les différents symboles, les objets et les éléments de données dans une image exécutable.  
  
### <a name="to-query-the-pdb-file"></a>Pour interroger le fichier .pdb  
  
1.  Acquérir une source de données en créant un [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) interface.  
  
    ```cpp#  
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
  
2.  Appelez [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) ou [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) pour charger les informations de débogage.  
  
    ```cpp#  
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
  
3.  Appelez [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) pour ouvrir un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) pour accéder aux informations de débogage.  
  
    ```cpp#  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4.  Utilisez les méthodes de `IDiaSession` pour rechercher des symboles dans la source de données.  
  
    ```cpp#  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5.  Utilisez le `IDiaEnum*` interfaces pour énumérer et parcourir les symboles ou d’autres éléments d’informations de débogage.  
  
    ```cpp#  
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
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)



