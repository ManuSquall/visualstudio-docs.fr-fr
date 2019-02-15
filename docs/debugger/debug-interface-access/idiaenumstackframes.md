---
title: IDiaEnumStackFrames | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames interface
ms.assetid: 3d1e8403-c9fc-42ff-ae35-0ab9a5ed2ad7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d4b46d2b59566df003b455e9dcf07ae96a28872
ms.sourcegitcommit: 34940a18f5b03a59567f54c7024a0b16d4272f1e
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56155342"
---
# <a name="idiaenumstackframes"></a>IDiaEnumStackFrames
Énumère les frames de pile différentes disponibles.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable

|Méthode|Description|
|------------|-----------------|
|[IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md)|Récupère un nombre spécifié d’éléments de frame de pile à partir de la séquence d’énumération.|
|[IDiaEnumStackFrames::Reset](../../debugger/debug-interface-access/idiaenumstackframes-reset.md)|Réinitialise une séquence d’énumération au début.|

## <a name="remarks"></a>Notes

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
Obtenez cette interface en appelant le [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) ou [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) méthodes.

## <a name="example"></a>Exemple
Cet exemple montre comment obtenir et utiliser le `IDiaEnumStackFrames` interface. Consultez le [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) interface pour une implémentation de la `PrintStackFrame` (fonction).

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

## <a name="requirements"></a>Spécifications
En-tête : Dia2.h

Bibliothèque : diaguids.lib

DLL : msdia80.dll

## <a name="see-also"></a>Voir aussi
[Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)  
[IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)  
[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
