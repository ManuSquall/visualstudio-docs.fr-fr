---
description: Énumère les différents frames de pile disponibles.
title: IDiaEnumStackFrames | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames interface
ms.assetid: 3d1e8403-c9fc-42ff-ae35-0ab9a5ed2ad7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 52acd9646523f53ce4f95f8e4d312bbd70637c3b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148730"
---
# <a name="idiaenumstackframes"></a>IDiaEnumStackFrames
Énumère les différents frames de pile disponibles.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable

|Méthode|Description|
|------------|-----------------|
|[IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md)|Récupère un nombre spécifié d’éléments de frame de pile à partir de la séquence d’énumération.|
|[IDiaEnumStackFrames::Reset](../../debugger/debug-interface-access/idiaenumstackframes-reset.md)|Réinitialise une séquence d'énumération.|

## <a name="remarks"></a>Notes

## <a name="notes-for-callers"></a>Notes pour les appelants
Obtenez cette interface en appelant les méthodes [IDiaStackWalker :: getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) ou [IDiaStackWalker :: getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) .

## <a name="example"></a>Exemple
Cet exemple montre comment obtenir et utiliser l' `IDiaEnumStackFrames` interface. Consultez l’interface [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) pour une implémentation de la `PrintStackFrame` fonction.

```C++
void DumpStackFrames(IDiaStackWalker*     pStackWalker,
                     IDiaStackWalkHelper* pStackWalkHelper,
                     CV_CPU_TYPE_e        cpuType)
{
    if (pStackWalker != NULL && pStackWalkHelper != NULL)
    {
        CComPtr<IDiaEnumStackFrames> pEnumsFrames;
        HRESULT hr;
        hr = pStackWalker->getEnumFrames2(cpuType, pStackWalkHelper, &pEnumFrames);
        if (SUCCEEDED(hr) && pEnumFrames != NULL)
        {
            CComPtr<IDiaStackFrame> pStackFrame;
            DWORD celt = 0;

            while (pEnumFrames->Next(1, &pStackFrame, &celt) == S_OK)
            {
                PrintStackFrame(pStackFrame);
            }
            pStackFrame = NULL;
        }
    }
}
```

## <a name="requirements"></a>Configuration requise
En-tête : Dia2. h

Bibliothèque : diaguids. lib

DLL : msdia80.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
