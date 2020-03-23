---
title: marker_importance, énumération | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3f5cfb583ec4fceb9fb7428b08c00f6ca8e26b6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62999961"
---
# <a name="marker_importance-enumeration"></a>marker_importance, énumération
Représente le niveau d’importance d’un marqueur du visualiseur concurrentiel.

## <a name="syntax"></a>Syntaxe

```cpp
enum marker_importance;
```

## <a name="members"></a>Membres

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`critical_importance`|Spécifie que le marqueur a une importance critique.|
|`high_importance`|Spécifie que le marqueur a une importance haute.|
|`low_importance`|Spécifie que le marqueur a une importance basse.|
|`normal_importance`|Spécifie que le marqueur a une importance normale.|

## <a name="requirements"></a>Spécifications
 **En-tête :** *cvmarkersobj.h*

 **Espace de noms** : Concurrency::diagnostic

## <a name="see-also"></a>Voir aussi
- [espace de nom de diagnostic](../profiling/diagnostic-namespace.md)