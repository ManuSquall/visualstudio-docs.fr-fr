---
title: IDebugProgramProvider2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74604e0b3446e33962c6a8e69a69bfc400f0e3e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916695"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Cette interface inscrite permet le débogage de session manager (SDM) pour obtenir des informations sur les programmes qui ont été « publié » via le [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) interface.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
Le moteur de débogage (dé) implémente cette interface pour fournir des informations sur les programmes en cours de débogage. Cette interface est inscrit dans la section du Registre à l’aide de la métrique `metricProgramProvider`, comme décrit dans [aides SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
Appel de COM `CoCreateInstance` fonctionne avec le `CLSID` du fournisseur de programme qui est obtenu à partir du Registre. Consultez l’exemple.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable

|Méthode|Description|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Obtient des informations sur les programmes en cours d’exécution, filtré de façons différentes.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Obtient un nœud de programme, en fonction d’un ID de processus spécifique.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Établit un rappel pour surveiller les événements du fournisseur associés à des types spécifiques de processus.|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Établit les paramètres régionaux pour toutes les ressources linguistiques requises par l’Allemagne.|

## <a name="remarks"></a>Notes
Normalement, un processus utilise cette interface pour découvrir comment les programmes en cours d’exécution dans ce processus.

## <a name="requirements"></a>Configuration requise
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Exemple

```cpp
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugProgramProvider2 *pProvider = NULL;
    if (pDebugEngineGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetMetric(NULL,
                    metrictypeEngine,
                    *pDebugEngineGuid,
                    metricProgramProvider,
                    &clsidProvider,
                    strRegistrationRoot);
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugProgramProvider2> spProgramProvider;
            spProgramProvider.CoCreateInstance(clsidProvider);
            if (spProgramProvider != NULL) {
                pProvider = spProgramProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [Aides SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
