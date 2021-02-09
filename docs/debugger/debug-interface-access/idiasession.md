---
title: IDiaSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 12337385d2ac9b586176c47d8579ec8ee7a5bd29
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864032"
---
# <a name="idiasession"></a>IDiaSession
Fournit un contexte de requête pour les symboles de débogage.

## <a name="syntax"></a>Syntaxe

```
IDiaSession : IUnknown
```

## <a name="methods"></a>Méthodes
Le tableau suivant présente les méthodes de `IDiaSession` .

|Méthode|Description|
|------------|-----------------|
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Récupère l’adresse de chargement du fichier exécutable qui correspond aux symboles dans ce magasin de symboles. Il s’agit de la même valeur que celle qui a été transmise à la `put_loadAddress` méthode.|
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Définit l’adresse de chargement du fichier exécutable qui correspond aux symboles dans ce magasin de symboles. **Remarque :**  Il est important d’appeler cette méthode lorsque vous recevez un `IDiaSession` objet et avant de commencer à utiliser l’objet.|
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Récupère une référence à la portée globale.|
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Récupère un énumérateur pour toutes les tables contenues dans le magasin de symboles.|
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Récupère un énumérateur pour tous les symboles nommés aux emplacements statiques.|
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Récupère tous les enfants d’un identificateur parent spécifié qui correspondent au nom et au type de symbole.|
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Récupère un type de symbole spécifié qui contient ou est le plus proche d’une adresse spécifiée.|
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Récupère un type de symbole spécifié qui contient ou est le plus proche d’une adresse virtuelle relative (RVA) spécifiée.|
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Récupère un type de symbole spécifié qui contient ou est le plus proche d’une adresse virtuelle spécifiée (VA).|
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Récupère le symbole qui contient un jeton de métadonnées spécifié.|
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Vérifie si deux symboles sont équivalents.|
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Récupère un symbole par son identificateur unique.|
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Récupère un type de symbole spécifié qui contient ou est le plus proche d’une adresse virtuelle et d’un offset relatifs spécifiés.|
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Récupère un type de symbole spécifié qui contient ou est le plus proche d’une adresse virtuelle et d’un offset spécifiés.|
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Récupère un fichier source par compiland et nom.|
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Récupère un fichier source par identificateur de fichier source.|
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Récupère les numéros de ligne dans un module de journalisation et un identificateur de fichier source spécifiés.|
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Récupère les lignes d’un compiland spécifié qui contiennent une adresse spécifiée.|
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Récupère les lignes d’un compiland spécifié qui contiennent une adresse virtuelle relative spécifiée.|
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Recherche les informations de numéro de ligne pour les lignes contenues dans une plage d’adresses spécifiée.|
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Récupère les lignes d’un compiland spécifié par fichier source et numéro de ligne.|
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Récupère une source qui a été placée dans le magasin de symboles par des fournisseurs d’attributs ou d’autres composants du processus de compilation.|
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Récupère une séquence énumérée de flux de données de débogage.|
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Récupère une énumération qui permet à un client d’itérer au sein de tous les frames insérés sur une adresse donnée.|
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Récupère une énumération qui permet à un client d’itérer au sein de tous les frames insérés sur une adresse virtuelle relative (RVA) spécifiée.|
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Récupère une énumération qui permet à un client d’itérer au sein de tous les frames insérés sur une adresse virtuelle spécifiée (VA).|
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Récupère une énumération qui permet à un client d’itérer au sein des informations de numéro de ligne de toutes les fonctions qui sont Inline, directement ou indirectement, par le symbole parent spécifié.|
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Récupère une énumération qui permet à un client d’itérer au sein des informations de numéro de ligne de toutes les fonctions qui sont Inline, directement ou indirectement, par le symbole parent spécifié et qui sont contenues dans la plage d’adresses spécifiée.|
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Récupère une énumération qui permet à un client d’itérer au sein des informations de numéro de ligne de toutes les fonctions qui sont Inline, directement ou indirectement, par le symbole parent spécifié et qui sont contenues dans l’adresse virtuelle relative (RVA) spécifiée.|
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Récupère une énumération qui permet à un client d’itérer au sein des informations de numéro de ligne de toutes les fonctions qui sont Inline, directement ou indirectement, par le symbole parent spécifié et qui sont contenues dans l’adresse virtuelle (VA) spécifiée.|
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Récupère une énumération qui permet à un client d’itérer au sein des informations de numéro de ligne de toutes les fonctions qui sont Inline, directement ou indirectement, dans le fichier source et le numéro de ligne spécifiés.|
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Récupère une énumération qui permet à un client d’itérer au sein des informations de numéro de ligne de toutes les fonctions inline qui correspondent à un nom spécifié.|
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Retourne une énumération de symboles pour la variable à laquelle correspond la valeur de balise spécifiée dans la fonction stub d’accélérateur parente.|
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Pour une valeur de balise correspondante donnée, cette méthode retourne une énumération des symboles contenus dans une fonction stub d’accélérateur parente spécifiée à une adresse virtuelle relative spécifiée.|
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Retourne une énumération de symboles pour les frames insérés correspondant au nom de fonction inline spécifié.|
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Retourne une énumération de symboles pour les frames inclus qui correspondent à l’emplacement source spécifié.|

## <a name="remarks"></a>Remarques
Il est important d’appeler la méthode [IDiaSession ::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) après la création de l' `IDiaSession` objet, et la valeur transmise à la `put_loadAddress` méthode doit être différente de zéro, pour que les propriétés d’adresse virtuelle (va) des symboles soient accessibles. L’adresse de chargement provient du programme chargé de l’exécutable en cours de débogage. Par exemple, vous pouvez appeler la fonction Win32 `GetModuleInformation` pour récupérer l’adresse de chargement de l’exécutable, en fonction d’un handle de l’exécutable.

## <a name="example"></a>Exemple
Cet exemple montre comment obtenir l' `IDiaSession` interface dans le cadre d’une initialisation générale du kit de développement logiciel (SDK) dia.

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
En-tête : Dia2. h

Bibliothèque : diaguids. lib

DLL : msdia80.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [Vue d'ensemble](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [Exe](../../debugger/debug-interface-access/exe.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
- [Interrogation du fichier .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
