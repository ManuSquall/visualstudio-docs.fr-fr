---
title: IDiaEnumFrameData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData interface
ms.assetid: 2ca7fd5a-b2fa-4b3a-9492-0263eafc435b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e20fa21d739c79dad94a8445f6d0fe811337fd40
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744560"
---
# <a name="idiaenumframedata"></a>IDiaEnumFrameData
Énumère les différents éléments de données de frame contenus dans la source de données.

## <a name="syntax"></a>Syntaxe

```
IDiaEnumFrameData : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant présente les méthodes de `IDiaEnumFrameData`.

|Méthode|Description|
|------------|-----------------|
|[IDiaEnumFrameData::get__NewEnum](../../debugger/debug-interface-access/idiaenumframedata-get-newenum.md)|Récupère la version `IEnumVARIANT Interface` de cet énumérateur.|
|[IDiaEnumFrameData::get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md)|Récupère le nombre d’éléments de données de frame.|
|[IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)|Récupère un élément de données de frame au moyen d’un index.|
|[IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)|Récupère un nombre spécifié d’éléments de données de frame dans la séquence d’énumération.|
|[IDiaEnumFrameData::Skip](../../debugger/debug-interface-access/idiaenumframedata-skip.md)|Ignore un nombre spécifié d’éléments de données de frame dans une séquence d’énumération.|
|[IDiaEnumFrameData::Reset](../../debugger/debug-interface-access/idiaenumframedata-reset.md)|Réinitialise une séquence d’énumération au début.|
|[IDiaEnumFrameData::Clone](../../debugger/debug-interface-access/idiaenumframedata-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|
|[IDiaEnumFrameData::frameByRVA](../../debugger/debug-interface-access/idiaenumframedata-framebyrva.md)|Retourne un frame par adresse virtuelle relative (RVA).|
|[IDiaEnumFrameData::frameByVA](../../debugger/debug-interface-access/idiaenumframedata-framebyva.md)|Retourne un frame par adresse virtuelle (VA).|

## <a name="remarks"></a>Notes

## <a name="notes-for-callers"></a>Notes pour les appelants
Obtenez cette interface à partir de la méthode [IDiaSession :: getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) . Pour plus d’informations, consultez l’exemple.

## <a name="example"></a>Exemple
Cet exemple montre comment obtenir (la fonction `GetEnumFrameData`) et utiliser (la fonction `ShowFrameData`) l’interface `IDiaEnumFrameData`. Pour obtenir un exemple de la fonction `PrintFrameData`, consultez l’interface [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) .

```C++

      IDiaEnumFrameData* GetEnumFrameData(IDiaSession *pSession)
{
    IDiaEnumFrameData* pUnknown    = NULL;
    REFIID             iid         = __uuidof(IDiaEnumFrameData);
    IDiaEnumTables*    pEnumTables = NULL;
    IDiaTable*         pTable      = NULL;
    ULONG              celt        = 0;

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

void ShowFrameData(IDiaSession *pSession)
{
    IDiaEnumFrameData* pEnumFrameData = GetEnumFrameData(pSession);;

    if (pEnumFrameData != NULL)
    {
        IDiaFrameData* pFrameData;
        ULONG celt = 0;

        while(pEnumFrameData->Next(1, &pFrameData, &celt) == S_OK &&
              celt == 1)
        {
            PrintFrameData(pFrameData);
            pFrameData->Release();
        }
        pEnumFrameData->Release();
    }
}
```

## <a name="requirements"></a>spécifications
**En-tête :** Dia2. h

**Bibliothèque :** diaguids. lib

**Dll :** Msdia80. dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
