---
description: Cette méthode détermine si le visualiseur peut avoir l’objet de données qu’il représente mis à jour.
title: 'IEEVisualizerDataProvider :: CanSetObjectForVisualizer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer method
ms.assetid: 70fd3c6f-2f82-43a3-993b-c1dc8aa080bf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a0a7f69ea57e14e7a1960712631f03a3becc8b80
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222937"
---
# <a name="ieevisualizerdataprovidercansetobjectforvisualizer"></a>IEEVisualizerDataProvider::CanSetObjectForVisualizer
Cette méthode détermine si le visualiseur peut avoir l’objet de données qu’il représente mis à jour.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CanSetObjectForVisualizer(
   BOOL* b
);
```

```csharp
int CanSetObjectForVisualizer(
   out int b
);
```

## <a name="parameters"></a>Paramètres
`b`\
à Différent de zéro ( `TRUE` ) si l’objet sur le visualiseur peut être mis à jour, zéro ( `FALSE` ) si ce n’est pas le cas.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Un objet peut ne pas être modifiable s’il est lié à la mémoire en lecture seule, par exemple.

## <a name="see-also"></a>Voir aussi
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
