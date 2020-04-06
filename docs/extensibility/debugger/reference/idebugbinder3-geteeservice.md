---
title: IDebugBinder3:GetEEService ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c08d7df4a6b05be489f6b9ab06569c085f3b1f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735828"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Cette méthode renvoie un service demandé.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetEEService(
   [in] GUID        vendor,
   [in] GUID        language,
   [in] GUID        iid,
   [out] IUnknown** ppService
);
```

```csharp
Int GetEEService(
   Guid       vendor,
   Guid       language,
   Guid       iid,
   out object ppService
);
```

## <a name="parameters"></a>Paramètres
`vendor`\
[dans] `GUID` d’un fournisseur (une valeur nulle est acceptable).

`language`\
[dans] `GUID` d’une langue (une valeur nulle est acceptable).

`iid`\
[dans] `IID` du service à obtenir.

`ppService`\
[out] Une interface au service demandé.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Laissez passer `IID` le pour [l’interface IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) (`IID_IEEVisualizerServiceProvider`) pour voir si le service de visualisation de type est disponible. Si c’est le cas, l’évaluateur d’expression peut obtenir [l’interface IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) pour prendre en charge les visualisateurs de type. Voir [Visualizing and Viewing Data](../../../extensibility/debugger/visualizing-and-viewing-data.md) pour plus de détails.

## <a name="see-also"></a>Voir aussi
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)
