---
title: 'IEEVisualizerService :: GetCustomViewerList | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ba63a1f27e043ca114a3b954adfe403b60283ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907806"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
Cette méthode retourne une liste des visualiseurs de types que ce service connaît.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCustomViewerList(
   ULONG                celtSkip,
   ULONG                celtRequested,
   DEBUG_CUSTOM_VIEWER* rgViewers,
   ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
   uint                  celtSkip,
   uint                  celtRequested,
   DEBUG_CUSTOM_VIEWER[] rgViewers,
   out uint              pceltFetched
);
```

## <a name="parameters"></a>Paramètres
`celtSkip`\
dans Nombre de visualiseurs à ignorer.

`celRequested`\
dans Nombre de visualiseurs à récupérer (spécifie également la taille du `rgViewers` tableau).

`rgViewers`\
[in, out] Tableau de structures de [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) à remplir.

`pceltFetched`\
à Nombre de visualiseurs réellement récupérés.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) transmet la requête à cette méthode dans le cadre de sa prise en charge des visualiseurs de type. Si l’évaluateur d’expression fournit également des visionneuses personnalisées pour le même type, il peut ajouter à la liste des structures [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) remplies de manière appropriée pour ces visionneuses personnalisées. Assurez-vous que [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) reflète ces visionneuses supplémentaires.

 Pour plus d’informations sur les différences entre les visualiseurs et les visionneuses, consultez [visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) .

## <a name="see-also"></a>Voir aussi
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
- [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
