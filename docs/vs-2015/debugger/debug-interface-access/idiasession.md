---
title: IDiaSession | Microsoft Docs
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
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a2ff17cc95769a9cada09b31b800afeaa13a44a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252978"
---
# <a name="idiasession"></a>IDiaSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Fournit un contexte de requête pour les symboles de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant présente les méthodes de `IDiaSession`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Récupère l’adresse de chargement du fichier exécutable qui correspond aux symboles dans ce magasin de symboles. C’est la même valeur que celle qui a été passée à la `put_loadAddress` (méthode).|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Définit l’adresse de chargement du fichier exécutable qui correspond aux symboles dans ce magasin de symboles. **Remarque :** il est important d’appeler cette méthode lorsque vous recevez un `IDiaSession` de l’objet et avant de commencer à l’aide de l’objet.|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Récupère une référence à la portée globale.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Récupère un énumérateur pour toutes les tables contenues dans le magasin de symboles.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Récupère un énumérateur pour tous les symboles nommés à des emplacements statiques.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Récupère tous les enfants d’un identificateur du parent spécifié qui correspondent au type de nom et le symbole.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Récupère un type de symbole spécifié qui contienne, ou est le plus proche, une adresse spécifiée.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Récupère un type de symbole spécifié qui contienne, ou est le plus proche, une adresse virtuelle relative (RVA) spécifiée.|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Récupère un type de symbole spécifié qui contienne, ou est le plus proche, une adresse virtuelle spécifiée (VA).|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Récupère le symbole qui contient un jeton de métadonnées spécifié.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Vérifie si deux symboles sont équivalentes.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Récupère un symbole par son identificateur unique.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Récupère un type de symbole spécifié qui contienne, ou est le plus proche, une adresse virtuelle relative spécifiée et le décalage.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Récupère un type de symbole spécifié qui contienne, ou est le plus proche, une adresse virtuelle spécifiée et le décalage.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Récupère un fichier source par compiland et le nom.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Récupère un fichier source par identificateur de fichier source.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Récupère les numéros de ligne dans un identificateur de fichier compiland et source spécifié.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Récupère les lignes dans un compiland spécifiée qui contiennent une adresse spécifiée.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Récupère les lignes dans un compiland spécifiée qui contiennent une adresse virtuelle relative spécifiée.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Recherche les informations de numéro de ligne pour les lignes contenues dans une plage d’adresses spécifiée.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Récupère les lignes dans un compiland spécifié par le nombre de lignes et les fichiers source.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Récupère une source qui a été placée dans le magasin de symboles par les fournisseurs d’attributs ou d’autres composants du processus de compilation.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Récupère une séquence énumérée débogage de flux de données.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Récupère une énumération qui permet au client d’effectuer une itération dans tous les cadres inline sur une adresse donnée.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Récupère une énumération qui permet au client d’effectuer une itération dans tous les cadres inline sur une adresse virtuelle relative (RVA) spécifiée.|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Récupère une énumération qui permet au client d’effectuer une itération dans tous les cadres inline sur une adresse virtuelle spécifiée (VA).|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Récupère une énumération qui permet au client d’effectuer une itération dans les informations de numéro de ligne de toutes les fonctions qui sont inline, directement ou indirectement, par le symbole du parent spécifié.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Récupère une énumération qui permet au client d’effectuer une itération dans les informations de numéro de ligne de toutes les fonctions qui sont inline, directement ou indirectement, par le symbole parent spécifié et est contenue dans la plage d’adresses spécifiée.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Récupère une énumération qui permet au client d’effectuer une itération dans les informations de numéro de ligne de toutes les fonctions qui sont inline, directement ou indirectement, par le symbole parent spécifié et est contenue dans l’adresse virtuelle relative (RVA) spécifié.|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Récupère une énumération qui permet au client d’effectuer une itération dans les informations de numéro de ligne de toutes les fonctions qui sont inline, directement ou indirectement, par le symbole parent spécifié et est contenue dans l’adresse virtuelle spécifiée (VA).|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Récupère une énumération qui permet au client d’effectuer une itération dans les informations de numéro de ligne de toutes les fonctions qui sont inline, directement ou indirectement, dans le nombre de lignes et les fichiers source spécifié.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Récupère une énumération qui permet au client d’effectuer une itération dans les informations de numéro de ligne de toutes les fonctions inline qui correspondent à un nom spécifié.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Retourne une énumération des symboles pour la variable la valeur de balise spécifiée correspond à de la fonction de stub accélérateur page parente.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Étant donné une valeur de balise correspondante, cette méthode retourne une énumération de symboles qui sont contenus dans une fonction de stub d’accélérateur parent spécifié à une adresse virtuelle relative spécifiée.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Retourne une énumération de symboles pour les frames en ligne correspondant au nom de fonction inline spécifiés.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Retourne une énumération de symboles pour les frames en ligne qui correspondent à l’emplacement source spécifié.|  
  
## <a name="remarks"></a>Notes  
 Il est important d’appeler le [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) méthode après avoir créé le `IDiaSession` objet — et la valeur passée à la `put_loadAddress` méthode doit être différente de zéro, pour toutes les propriétés des symboles d’adresse virtuelle (VA) accessible. L’adresse de chargement provient le programme chargé de l’exécutable en cours de débogage. Par exemple, vous pouvez appeler la fonction Win32 `GetModuleInformation` pour récupérer l’adresse de chargement pour le fichier exécutable, étant donné un handle au fichier exécutable.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment obtenir le `IDiaSession` interface en tant que partie d’une initialisation générale du DIA SDK.  
  
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
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Vue d’ensemble](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Interrogation du fichier .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)



