---
title: IDiaTable | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b9c9f85ffbf4eed2fdc305a64bd3f32822dacd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682790"
---
# <a name="idiatable"></a>IDiaTable
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Énumère une table de source de données DIA.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDiaTable` .  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Récupère la version d' [interface IEnumVARIANT](https://msdn.microsoft.com/139e3c93-faef-4003-9079-e0e94494db3e) de cet énumérateur.|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Récupère le nom de la table.|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Récupère le nombre d’éléments dans la table.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Récupère une référence à un index d’entrée particulier.|  
  
## <a name="remarks"></a>Notes  
 Cette interface implémente les `IEnumUnknown` méthodes d’énumération dans l’espace de noms Microsoft. VisualStudio. OLE. Interop. L' `IEnumUnknown` interface d’énumération est plus efficace pour itérer au sein du contenu de la table que les méthodes [IDiaTable :: Get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) et [IDiaTable :: Item](../../debugger/debug-interface-access/idiatable-item.md) .  
  
 L’interprétation de l' `IUnknown` interface retournée par la `IDiaTable::Item` méthode ou la `Next` méthode (dans l’espace de noms Microsoft. VisualStudio. OLE. Interop) dépend du type de table. Par exemple, si l' `IDiaTable` interface représente une liste de sources injectées, l’interface `IUnknown` doit être interrogée pour l’interface [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) .  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 Obtenez cette interface en appelant les méthodes [IDiaEnumTables :: Item](../../debugger/debug-interface-access/idiaenumtables-item.md) ou [IDiaEnumTables :: Next](../../debugger/debug-interface-access/idiaenumtables-next.md) .  
  
 Les interfaces suivantes sont implémentées avec l' `IDiaTable` interface (autrement dit, vous pouvez interroger l' `IDiaTable` interface pour l’une des interfaces suivantes) :  
  
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>Exemple  
 La première fonction, `ShowTableNames` , affiche les noms de toutes les tables dans la session. La deuxième fonction, `GetTable` , effectue une recherche dans toutes les tables pour une table qui implémente une interface spécifiée. La troisième fonction, `UseTable` , montre comment utiliser la `GetTable` fonction.  
  
> [!NOTE]
> `CDiaBSTR` est une classe qui encapsule un `BSTR` et gère automatiquement la libération de la chaîne lorsque l’instanciation est hors de portée.  
  
```cpp#  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )  
            && celt == 1 )  
    {  
        CDiaBSTR bstrTableName;  
        if ( pTable->get_name( &bstrTableName ) != 0 )  
        {  
            Fatal( "get_name" );  
        }  
        printf( "Found table: %ws\n", bstrTableName );  
    }  
  
// Searches the list of all tables for a table that supports  
// the specified interface.  Use this function to obtain an  
// enumeration interface.  
HRESULT GetTable(IDiaSession* pSession,  
                 REFIID       iid,  
                 void**       ppUnk)  
{  
    CComPtr<IDiaEnumTables> pEnumTables;  
    HRESULT hResult;  
  
    if (FAILED(pSession->getEnumTables(&pEnumTables)))  
        Fatal("getEnumTables");  
  
    CComPtr<IDiaTable> pTable;  
    ULONG celt = 0;  
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&  
           celt == 1)  
    {  
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)  
        {  
            return S_OK;  
        }  
        pTable = NULL;  
    }  
  
    if (FAILED(hResult))  
        Fatal("EnumTables->Next");  
  
    return E_FAIL;  
}  
  
// This function shows how to use the GetTable function.  
void UseTable(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pEnumSegments;  
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))  
    {  
        // Do something with pEnumSegments.  
    }  
}  
```  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Dia2. h  
  
 Bibliothèque : diaguids. lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (kit de développement logiciel de debug interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaEnumTables :: Item](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
