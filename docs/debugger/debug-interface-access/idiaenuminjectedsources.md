---
description: Énumérez les diverses sources injectées contenues dans la source de données.
title: IDiaEnumInjectedSources | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources interface
ms.assetid: f97e2392-22e1-48da-b7ce-ad94c8b684b0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eb7ba63a06a18db75c969e5bc30ec462c2ccc618
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157993"
---
# <a name="idiaenuminjectedsources"></a>IDiaEnumInjectedSources
Énumérez les diverses sources injectées contenues dans la source de données.

## <a name="syntax"></a>Syntaxe

```
IDiaEnumInjectedSources : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant présente les méthodes de `IDiaEnumInjectedSources` .

|Méthode|Description|
|------------|-----------------|
|[IDiaEnumInjectedSources::get__NewEnum](../../debugger/debug-interface-access/idiaenuminjectedsources-get-newenum.md)|Récupère la version d' [interface IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) de cet énumérateur.|
|[IDiaEnumInjectedSources::get_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md)|Récupère le nombre de sources injectées.|
|[IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)|Récupère une source injectée au moyen d’un index.|
|[IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)|Récupère un nombre spécifié de sources injectées dans la séquence d’énumération.|
|[IDiaEnumInjectedSources::Skip](../../debugger/debug-interface-access/idiaenuminjectedsources-skip.md)|Ignore un nombre spécifié de sources injectées dans une séquence d’énumération.|
|[IDiaEnumInjectedSources::Reset](../../debugger/debug-interface-access/idiaenuminjectedsources-reset.md)|Réinitialise une séquence d'énumération.|
|[IDiaEnumInjectedSources::Clone](../../debugger/debug-interface-access/idiaenuminjectedsources-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|

## <a name="remarks"></a>Notes

## <a name="notes-for-callers"></a>Notes pour les appelants
Cette interface est obtenue en appelant la méthode [IDiaSession :: findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md) avec le nom d’un fichier source spécifique ou en appelant la méthode [IDiaSession :: GETENUMTABLES](../../debugger/debug-interface-access/idiasession-getenumtables.md) avec le GUID de l' `IDiaEnumInjectedSources` interface.

## <a name="example"></a>Exemple
Cet exemple montre comment obtenir (la `GetEnumInjectedSources` fonction) et utiliser (la `DumpAllInjectedSources` fonction) l' `IDiaEnumInjectedSources` interface. Consultez l’interface [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md) pour une implémentation de la `PrintPropertyStorage` fonction. Pour obtenir une autre sortie, consultez l’interface [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) .

```C++

IDiaEnumInjectedSources* GetEnumInjectedSources(IDiaSession *pSession)
{
    IDiaEnumInjectedSources* pUnknown    = NULL;
    REFIID                   iid         = __uuidof(IDiaEnumInjectedSources);
    IDiaEnumTables*          pEnumTables = NULL;
    IDiaTable*               pTable      = NULL;
    ULONG                    celt        = 0;

    if (pSession->getEnumTables(&pEnumTables) != S_OK)
    {
        wprintf(L"ERROR - GetTable() getEnumTables\n");
        return NULL;
    }
    while (pEnumTables->Next(1, &pTable, &celt) == S_OK && celt == 1)
    {
        // There is only one table that matches the given iid
        HRESULT hr = pTable->QueryInterface(iid, (void**)&pUnknown);
        pTable->Release();
        if (hr == S_OK)
        {
            break;
        }
    }
    pEnumTables->Release();
    return pUnknown;
}

void DumpAllInjectedSources( IDiaSession* pSession)
{
    IDiaEnumInjectedSources* pEnumInjSources;

    pEnumInjSources = GetEnumInjectedSources(pSession);
    if (pEnumInjSources != NULL)
    {
        IDiaInjectedSource* pInjSource;
        ULONG celt = 0;

        while(pEnumInjSources->Next(1, &pInjSource, &celt) == S_OK &&
              celt == 1)
        {
            IDiaPropertyStorage *pPropertyStorage;
            if (pInjSource->QueryInterface(__uuidof(IDiaPropertyStorage),
                                          (void **)&pPropertyStorage) == S_OK)
            {
                PrintPropertyStorage(pPropertyStorage);
                pPropertyStorage->Release();
            }
            pInjSource->Release();
        }
        pEnumInjSources->Release();
    }
}
```

## <a name="requirements"></a>Configuration requise
En-tête : Dia2. h

Bibliothèque : diaguids. lib

DLL : msdia80.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
