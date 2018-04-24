---
title: IDiaTable | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e95c469bb3a1d8747a7f1dabfadec24dc991730c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="idiatable"></a>IDiaTable
Énumère une table de source de données DIA.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDiaTable`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Récupère le [IEnumVARIANT Interface](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e) version de cet énumérateur.|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Récupère le nom de la table.|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Récupère le nombre d’éléments dans la table.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Récupère une référence à un index de l’entrée en question.|  
  
## <a name="remarks"></a>Notes  
 Cette interface implémente la `IEnumUnknown` méthodes d’énumération dans l’espace de noms d’assemblys Microsoft.VisualStudio.OLE.Interop. Le `IEnumUnknown` interface d’énumération est beaucoup plus efficace pour itérer sur la table des matières à le [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) et [IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md) méthodes.  
  
 L’interprétation de la `IUnknown` interface retournée à partir de le le `IDiaTable::Item` (méthode) ou `Next` (méthode) (dans l’espace de noms d’assemblys Microsoft.VisualStudio.OLE.Interop) est dépendant du type de table. Par exemple, si le `IDiaTable` interface représente une liste de sources injectées, le `IUnknown` interface doit être interrogé pour la [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Obtenez cette interface en appelant le [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md) ou [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md) méthodes.  
  
 Les interfaces suivantes sont implémentées avec la `IDiaTable` interface (autrement dit, vous pouvez interroger la `IDiaTable` interface pour l’une des interfaces suivantes) :  
  
-   [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
-   [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
-   [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
-   [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
-   [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
-   [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
-   [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>Exemple  
 La première fonction `ShowTableNames`, affiche les noms de toutes les tables dans la session. La deuxième fonction `GetTable`, recherche toutes les tables pour une table qui implémente une interface spécifiée. La troisième fonction `UseTable`, montre comment utiliser le `GetTable` (fonction).  
  
> [!NOTE]
>  `CDiaBSTR` est une classe qui encapsule un `BSTR` et gère automatiquement la libération de la chaîne lors de l’instanciation est hors de portée.  
  
```C++  
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
  
## <a name="requirements"></a>Spécifications  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)