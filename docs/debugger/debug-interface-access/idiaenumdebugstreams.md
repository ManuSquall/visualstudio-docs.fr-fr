---
title: IDiaEnumDebugStreams | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams interface
ms.assetid: 611caf4f-7a5f-4aa4-b909-52feeb3cc752
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70e14e594b385a2fa93f51eed4dec36d74db347e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744694"
---
# <a name="idiaenumdebugstreams"></a>IDiaEnumDebugStreams
Énumère les différents flux de débogage contenus dans la source de données.

## <a name="syntax"></a>Syntaxe

```
IDiaEnumDebugStreams : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant présente les méthodes de `IDiaEnumDebugStreams`.

|Méthode|Description|
|------------|-----------------|
|[IDiaEnumDebugStreams::get__NewEnum](../../debugger/debug-interface-access/idiaenumdebugstreams-get-newenum.md)|Récupère la version `IEnumVARIANT` de cet énumérateur.|
|[IDiaEnumDebugStreams::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreams-get-count.md)|Récupère le nombre de flux de débogage.|
|[IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)|Récupère un flux de débogage au moyen d’un index.|
|[IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)|Récupère un nombre spécifié de flux de débogage dans la séquence d’énumération.|
|[IDiaEnumDebugStreams::Skip](../../debugger/debug-interface-access/idiaenumdebugstreams-skip.md)|Ignore un nombre spécifié de flux de débogage dans une séquence d’énumération.|
|[IDiaEnumDebugStreams::Reset](../../debugger/debug-interface-access/idiaenumdebugstreams-reset.md)|Réinitialise une séquence d’énumération au début.|
|[IDiaEnumDebugStreams::Clone](../../debugger/debug-interface-access/idiaenumdebugstreams-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|

## <a name="remarks"></a>Notes
Le contenu des flux de débogage est dépendant de l’implémentation et les formats de données ne sont pas documentés.

## <a name="notes-for-callers"></a>Notes pour les appelants
Appelez la méthode [IDiaSession :: getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md) pour obtenir un objet `IDiaEnumDebugStreams`.

## <a name="example"></a>Exemple
Cet exemple montre comment accéder aux flux de données disponibles à partir de cette interface. Consultez l’interface [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) pour une implémentation de la fonction `PrintStreamData`.

```C++
void DumpAllDebugStreams( IDiaSession* pSession)
{
    IDiaEnumDebugStreams* pEnumStreams;

    wprintf(L"\n\n*** DEBUG STREAMS\n\n");
    // Retrieve an enumerated sequence of debug data streams
    if(pSession->getEnumDebugStreams(&pEnumStreams) == S_OK)
    {
        IDiaEnumDebugStreamData* pStream;
        ULONG celt = 0;

        for(; pEnumStreams->Next(1, &pStream, &celt) == S_OK; pStream = NULL)
        {
            PrintStreamData(pStream);
            pStream->Release();
        }
        pEnumStreams->Release();
    }
    else
    {
        wprintf(L"Failed to get any debug streams!\n");
    }
    wprintf(L"\n");
}
```

## <a name="requirements"></a>spécifications
En-tête : Dia2. h

Bibliothèque : diaguids. lib

DLL : Msdia80. dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)
