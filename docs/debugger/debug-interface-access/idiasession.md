---
title: "IDiaSession | Microsoft Docs"
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
  - "IDiaSession (interface)"
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# IDiaSession
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Fournit une zone de requête pour des symboles de débogage.  
  
## Syntaxe  
  
```  
IDiaSession : IUnknown  
```  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes d' `IDiaSession`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaSession::get\_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Récupère l'adresse de charge du fichier exécutable qui correspond aux symboles dans ce magasin de symboles.  C'est la même valeur passée à la méthode d' `put_loadAddress` .|  
|[IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Définit l'adresse de charge du fichier exécutable qui correspond aux symboles dans ce magasin de symboles. **Note:**  Il est important d'appeler cette méthode lorsque vous obtenez un objet d' `IDiaSession` et avant de commencer à utiliser l'objet.|  
|[IDiaSession::get\_globalScope](../Topic/IDiaSession::get_globalScope.md)|Extrait une référence à la portée globale.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Récupère un énumérateur pour toutes les tables contenues dans le magasin de symboles.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Récupère un énumérateur pour tous les symboles nommés aux emplacements statiques.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Récupère tous les enfants d'un parent identificateur spécifié qui correspondent au nom et le type de symboles.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Récupère un type spécifié de symboles qui contient, ou est le plus proche de, une adresse spécifiée.|  
|[IDiaSession::findSymbolByRVA](../Topic/IDiaSession::findSymbolByRVA.md)|Récupère un type spécifié de symboles qui contient, ou est le plus proche de, une adresse virtuelle relative spécifiée \(RVA\).|  
|[IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)|Récupère un type spécifié de symboles qui contient, ou est le plus proche de, une adresse virtuelle spécifiée \(VA\).|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Récupère le symbole qui contient un jeton de métadonnées spécifié.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Vérifie si deux symboles sont identiques.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Récupère un symbole par son identificateur unique.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Récupère un type spécifié de symboles qui contient, ou est le plus proche de, une adresse virtuelle et un offset connexes spécifiés.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Récupère un type spécifié de symboles qui contient, ou est le plus proche de, une adresse virtuelle et un offset spécifiés.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Extrait un fichier source par le module et le nom.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Extrait un fichier source par l'identificateur de fichier source.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Récupère les numéros de ligne dans un identificateur spécifié de module et de fichier source.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Récupère les lignes un module spécifié qui contiennent une adresse spécifiée.|  
|[IDiaSession::findLinesByRVA](../Topic/IDiaSession::findLinesByRVA.md)|Récupère les lignes un module spécifié qui contiennent une adresse virtuelle relative spécifiée.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Recherche des informations de numéro de ligne pour les lignes contenues dans une plage d'adresse spécifiée.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Récupère les lignes un module spécifié par le fichier source et le numéro de ligne.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Extrait une source qui a été définie dans le magasin de symboles par des fournisseurs d'attribut ou d'autres composants du processus de compilation.|  
|[IDiaSession::getEnumDebugStreams](../Topic/IDiaSession::getEnumDebugStreams.md)|Extrait une séquence énumérée de débogage de flux de données.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Extrait une énumération qui permet à un client pour itérer au sein de tous les frames intégrés sur une adresse donnée.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Extrait une énumération qui permet à un client pour itérer au sein de tous les frames intégrés sur une adresse virtuelle relative spécifiée \(RVA\).|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Extrait une énumération qui permet à un client pour itérer au sein de tous les frames intégrés sur une adresse virtuelle spécifiée \(VA\).|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Extrait une énumération qui permet à un client pour itérer au sein de les informations de numéro de ligne de toutes les fonctions qui sont inline, directement ou indirectement, par le symbole parent spécifié.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Extrait une énumération qui permet à un client pour itérer au sein de les informations de numéro de ligne de toutes les fonctions qui sont inline, directement ou indirectement, par le symbole parent spécifié et est contenue dans la marge d'adresse spécifiée.|  
|[IDiaSession::findInlineeLinesByRVA](../Topic/IDiaSession::findInlineeLinesByRVA.md)|Extrait une énumération qui permet à un client pour itérer au sein de les informations de numéro de ligne de toutes les fonctions qui sont inline, directement ou indirectement, par le symbole parent spécifié et est contenue dans l'adresse virtuelle relative spécifiée \(RVA\).|  
|[IDiaSession::findInlineLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Extrait une énumération qui permet à un client pour itérer au sein de les informations de numéro de ligne de toutes les fonctions qui sont inline, directement ou indirectement, par le symbole parent spécifié et est contenue dans l'adresse virtuelle spécifiée \(VA\).|  
|[IDiaSession::findInlineeLinesByLinenum](../Topic/IDiaSession::findInlineeLinesByLinenum.md)|Extrait une énumération qui permet à un client pour itérer au sein de les informations de numéro de ligne de toutes les fonctions qui sont inline, directement ou indirectement, dans le fichier source et le numéro de ligne spécifié.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Extrait une énumération qui permet à un client pour itérer au sein de les informations de numéro de ligne de toutes les fonctions inline qui correspondent à un nom spécifié.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Retourne une énumération de symboles pour la variable à la valeur spécifiée de balises correspond à dans la fonction parente stub d'accélérateur.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Donné une valeur correspondante de balise, cette méthode retourne une énumération de symboles qui sont contenus dans une fonction parente spécifiée stub d'accélérateur à une adresse virtuelle relative spécifiée.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Retourne une énumération les symboles pour les frames intégrés correspondant au nom de la fonction inline spécifié.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Retourne une énumération les symboles pour les frames intégrés qui correspondent à l'emplacement spécifié de la source.|  
  
## Notes  
 Il est important d'appeler la méthode de [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) après avoir créé l'objet d' `IDiaSession` \)et la valeur passée à la méthode d' `put_loadAddress` doit être non nulle \(pour toutes les propriétés de \(VA\) d'adresse virtuelle de symboles pour être accessible.  L'adresse de chargement provient de la valeur que ce programme a chargé le fichier exécutable en cours de débogage.  Par exemple, vous pouvez appeler la fonction `GetModuleInformation` Win32 pour récupérer l'adresse de charge du fichier exécutable, donnée un handle au fichier exécutable.  
  
## Exemple  
 Cet exemple montre comment obtenir l'interface d' `IDiaSession` dans le cadre d'une initialisation diamètre générale du Kit de développement logiciel.  
  
```cpp#  
CComPtr<IDiaDataSource> pSource;  
ComPtr<IDiaSession> psession;  
  
void InitializeDIA(const char *szFilename)  
{  
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,  
                                   NULL,  
                                   CLSCTX_INPROC_SERVER,  
                                   __uuidof( IDiaDataSource ),  
                                  (void **) &pSource);  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename,  
              szFilename,  
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    if ( FAILED( pSource->openSession( &psession ) ) )  
    {  
        Fatal( "openSession" );  
    }  
}  
```  
  
## Configuration requise  
 En\-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## Voir aussi  
 [Interfaces \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Vue d’ensemble](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Interrogation du fichier .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)