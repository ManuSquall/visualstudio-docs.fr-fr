---
title: IDiaEnumSourceFiles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles interface
ms.assetid: 5c0779a6-a2ea-408a-90da-ebdecf2b83c0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f17deb28c8412743513f41ae3cd1df81aba0de83
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856193"
---
# <a name="idiaenumsourcefiles"></a>IDiaEnumSourceFiles
Énumère les différents fichiers sources contenus dans la source de données.

## <a name="syntax"></a>Syntaxe

```
IDiaEnumSourceFiles : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant présente les méthodes de `IDiaEnumSourceFiles` .

|Méthode|Description|
|------------|-----------------|
|[IDiaEnumSourceFiles::get__NewEnum](../../debugger/debug-interface-access/idiaenumsourcefiles-get-newenum.md)|Récupère la `IEnumVARIANT Interface` version de cet énumérateur.|
|[IDiaEnumSourceFiles::get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md)|Récupère le nombre de fichiers sources.|
|[IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)|Récupère un fichier source au moyen d’un index.|
|[IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)|Récupère un nombre spécifié de fichiers sources dans la séquence d’énumération.|
|[IDiaEnumSourceFiles::Skip](../../debugger/debug-interface-access/idiaenumsourcefiles-skip.md)|Ignore un nombre spécifié de fichiers sources dans une séquence d’énumération.|
|[IDiaEnumSourceFiles::Reset](../../debugger/debug-interface-access/idiaenumsourcefiles-reset.md)|Réinitialise une séquence d'énumération.|
|[IDiaEnumSourceFiles::Clone](../../debugger/debug-interface-access/idiaenumsourcefiles-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|

## <a name="remarks"></a>Remarques

## <a name="notes-for-callers"></a>Notes pour les appelants
Obtenez cette interface en appelant la `QueryInterface` méthode sur un objet [IDiaTable](../../debugger/debug-interface-access/idiatable.md) . Pour plus de détails, voir les exemples.

## <a name="example"></a>Exemple
Cet exemple montre comment obtenir l' `IDiaEnumSourceFiles` interface à partir de la liste de tables dans un objet de session dia. Pour obtenir un exemple d’accès aux informations du fichier source, consultez l’interface [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) .

```C++

IDiaEnumSourceFiles* GetEnumSourceFiles(IDiaSession *pSession)
{
    IDiaEnumSourceFiles * pUnknown    = NULL;
    REFIID                iid         = __uuidof(IDiaEnumSourceFiles);
    IDiaEnumTables*       pEnumTables = NULL;
    IDiaTable*            pTable      = NULL;
    ULONG                 celt        = 0;

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
```

## <a name="requirements"></a>Configuration requise
En-tête : Dia2. h

Bibliothèque : diaguids. lib

DLL : msdia80.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
