---
description: Cette méthode obtient un nouvel objet pour le visualiseur.
title: 'IEEVisualizerDataProvider :: GetNewObjectForVisualizer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::GetNewObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::GetNewObjectForVisualizer method
ms.assetid: a898d549-4898-4fde-aad1-e8bb89129652
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af26455e37d0ecf881cd0bed898e1997f00a82ea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083347"
---
# <a name="ieevisualizerdataprovidergetnewobjectforvisualizer"></a>IEEVisualizerDataProvider::GetNewObjectForVisualizer
Cette méthode obtient un nouvel objet pour le visualiseur. Cette méthode crée toujours un nouvel objet à partir de l’objet existant.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetNewObjectForVisualizer(
   IDebugObject** ppObject
);
```

```csharp
int GetNewObjectForVisualizer(
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Paramètres
`ppObject`\
à Nouvel objet.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 `This method` réévalue l’objet qu’il représente actuellement et retourne le résultat sous la forme d’un nouvel objet. L’objet existant sera mis à jour à la suite de l’évaluation.

## <a name="see-also"></a>Voir aussi
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
