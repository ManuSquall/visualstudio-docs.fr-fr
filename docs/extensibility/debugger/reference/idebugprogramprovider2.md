---
description: Cette interface inscrite permet au gestionnaire de débogage de session (SDM) d’obtenir des informations sur les programmes qui ont été publiés par le biais de l’interface IDebugProgramPublisher2.
title: IDebugProgramProvider2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5bead60e23c708d8a23fcd382b4db0f3f9f7e4c1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065240"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Cette interface inscrite permet au gestionnaire de débogage de session (SDM) d’obtenir des informations sur les programmes qui ont été « publiés » par le biais de l’interface [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) .

## <a name="syntax"></a>Syntaxe

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
Le moteur DE débogage (DE) implémente cette interface pour fournir des informations sur les programmes en cours de débogage. Cette interface est inscrite dans la section de du Registre à l’aide de la métrique `metricProgramProvider` , comme décrit dans le [Kit de développement logiciel (SDK) pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="notes-for-callers"></a>Notes pour les appelants
Appelez la fonction de COM `CoCreateInstance` avec le `CLSID` du fournisseur de programme obtenu à partir du Registre. Consultez l’exemple.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre vtable

|Méthode|Description|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Obtient des informations sur les programmes en cours d’exécution, filtrés de différentes façons.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Obtient un nœud de programme, en fonction d’un ID de processus spécifique.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Établit un rappel pour surveiller les événements de fournisseur associés à des genres spécifiques de processus.|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Établit des paramètres régionaux pour toutes les ressources spécifiques à la langue requises par le.|

## <a name="remarks"></a>Notes
Normalement, un processus utilise cette interface pour rechercher les programmes en cours d’exécution dans ce processus.

## <a name="requirements"></a>Spécifications
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

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
- [Programmes d’assistance SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
