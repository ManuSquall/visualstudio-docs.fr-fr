---
description: Cette méthode retourne un service demandé.
title: 'IDebugBinder3 :: GetEEService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ccc4d28a06d87d7c17d16470e10f259657083cc9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094300"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Cette méthode retourne un service demandé.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetEEService(
   [in] GUID        vendor,
   [in] GUID        language,
   [in] GUID        iid,
   [out] IUnknown** ppService
);
```

```csharp
Int GetEEService(
   Guid       vendor,
   Guid       language,
   Guid       iid,
   out object ppService
);
```

## <a name="parameters"></a>Paramètres
`vendor`\
[in] `GUID` d’un fournisseur (une valeur null est acceptable).

`language`\
[in] `GUID` d’un langage (une valeur null est acceptable).

`iid`\
[in] `IID` du service à obtenir.

`ppService`\
à Interface avec le service demandé.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Transmettez le `IID` pour l’interface [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) ( `IID_IEEVisualizerServiceProvider` ) afin de déterminer si le service du visualiseur de type est disponible. Dans ce cas, l’évaluateur d’expression peut obtenir l’interface [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) pour prendre en charge les visualiseurs de type. Pour plus d’informations [, consultez visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)
