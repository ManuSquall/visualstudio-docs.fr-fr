---
title: IDiaSession | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f3939ab86cd9f0948a2be44756b9ed94d143ecc8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idiasession"></a>IDiaSession
Fournit un contexte de requête pour les symboles de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant présente les méthodes de `IDiaSession`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Récupère l’adresse de chargement du fichier exécutable qui correspond aux symboles dans ce magasin de symboles. Ceci est la même valeur que celle qui a été passée à la `put_loadAddress` (méthode).|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Définit l’adresse de chargement du fichier exécutable qui correspond aux symboles dans ce magasin de symboles. **Remarque :** qu’il est important d’appeler cette méthode lorsque vous obtenez un `IDiaSession` de l’objet et avant de commencer à l’aide de l’objet.|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Récupère une référence à la portée globale.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Récupère un énumérateur pour toutes les tables contenues dans le magasin de symboles.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Récupère un énumérateur pour tous les symboles nommés à des emplacements statiques.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Récupère tous les enfants d’un identificateur parent spécifié qui correspond au type de nom et le symbole.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Récupère un type de symbole spécifié qui contienne, ou qui est le plus proche, à une adresse spécifiée.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Récupère un type de symbole spécifié qui contienne, ou qui est le plus proche d’une adresse virtuelle relative (RVA) spécifiée.|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Récupère un type de symbole spécifié qui contienne, ou qui est le plus proche d’une adresse virtuelle spécifiée (VA).|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Récupère le symbole qui contient un jeton de métadonnées spécifié.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Vérifie si deux symboles sont équivalents.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Récupère un symbole par son identificateur unique.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Récupère un type de symbole spécifié qui contienne, ou qui est le plus proche d’une adresse virtuelle relative spécifiée et le décalage.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Récupère un type de symbole spécifié qui contienne, ou qui est le plus proche d’une adresse virtuelle spécifiée et le décalage.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Récupère un fichier source par compiland et le nom.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Récupère un fichier source par l’identificateur du fichier source.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Récupère les numéros de ligne dans un identificateur de fichier compiland et source spécifié.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Récupère les lignes qui contiennent une adresse spécifiée dans un module spécifié.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Récupère les lignes qui contiennent une adresse virtuelle relative spécifiée dans un module spécifié.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Recherche les informations de numéro de ligne pour les lignes contenues dans une plage d’adresses spécifiée.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Récupère les lignes dans un compiland spécifié par le nombre de fichiers et de la ligne source.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Récupère une source qui a été placée dans le magasin de symboles par les fournisseurs d’attribut ou d’autres composants du processus de compilation.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Récupère une séquence énumérée débogage de flux de données.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Récupère une énumération qui permet à un client itérer au sein de tous les cadres inline sur une adresse donnée.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Récupère une énumération qui permet à un client itérer au sein de tous les cadres inline sur une adresse virtuelle relative (RVA) spécifiée.|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Récupère une énumération qui permet à un client itérer au sein de tous les cadres inline sur une adresse virtuelle spécifiée (VA).|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Récupère une énumération qui permet à un client parcourir les informations de numéro de ligne de toutes les fonctions qui sont incorporées, directement ou indirectement, par le symbole parent spécifié.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Récupère une énumération qui permet à un client parcourir les informations de numéro de ligne de toutes les fonctions qui sont incorporées, directement ou indirectement, par le symbole parent spécifié et est contenue dans la plage d’adresses spécifiée.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Récupère une énumération qui permet à un client parcourir les informations de numéro de ligne de toutes les fonctions qui sont incorporées, directement ou indirectement, par le symbole parent spécifié et est contenue dans l’adresse virtuelle relative (RVA) spécifié.|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Récupère une énumération qui permet à un client parcourir les informations de numéro de ligne de toutes les fonctions qui sont incorporées, directement ou indirectement, par le symbole parent spécifié et est contenue dans l’adresse virtuelle spécifiée (VA).|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Récupère une énumération qui permet à un client parcourir les informations de numéro de ligne de toutes les fonctions qui sont incorporées, directement ou indirectement, dans le nombre de fichiers et de la ligne source spécifié.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Récupère une énumération qui permet à un client parcourir les informations de numéro de ligne de toutes les fonctions inline qui correspondent à un nom spécifié.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Retourne une énumération de symboles de la valeur de la balise spécifiée correspond à la variable dans la fonction de stub accélérateur parent.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Une valeur correspondante de la balise donnée, cette méthode retourne une énumération de symboles contenus dans une fonction de stub d’accélérateur parent spécifié à une adresse virtuelle relative spécifiée.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Retourne une énumération de symboles de cadres correspondant au nom de la fonction inline spécifiés.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Retourne une énumération de symboles pour les cadres qui correspondent à l’emplacement source spécifié.|  
  
## <a name="remarks"></a>Notes  
 Il est important d’appeler le [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) méthode après avoir créé le `IDiaSession` objet : et la valeur passée à la `put_loadAddress` méthode doit être différente de zéro : pour toutes les propriétés d’adresse virtuelle (VA) de symboles accessible. L’adresse de chargement est fourni à partir de tout programme chargé de l’exécutable en cours de débogage. Par exemple, vous pouvez appeler la fonction Win32 `GetModuleInformation` pour récupérer l’adresse de chargement pour le fichier exécutable, en fonction d’un handle au fichier exécutable.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment obtenir le `IDiaSession` interface en tant que partie d’un général d’initialisation de DIA SDK.  
  
```C++  
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
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Vue d’ensemble](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Interrogation du fichier .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)