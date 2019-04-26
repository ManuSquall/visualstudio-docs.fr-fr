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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62999961"
---
# <a name="markerimportance-enumeration"></a>marker_importance, énumération
Représente le niveau d’importance d’un marqueur du visualiseur concurrentiel.

## <a name="syntax"></a>Syntaxe

```cpp
enum marker_importance;
```

## <a name="members"></a>Membres

### <a name="values"></a>Valeurs

|Name|Description|
|----------|-----------------|
|`critical_importance`|Spécifie que le marqueur a une importance critique.|
|`high_importance`|Spécifie que le marqueur a une importance haute.|
|`low_importance`|Spécifie que le marqueur a une importance basse.|
|`normal_importance`|Spécifie que le marqueur a une importance normale.|

## <a name="requirements"></a>Spécifications
 **En-tête :** *cvmarkersobj.h*

 **Espace de noms :** Concurrency::diagnostic

## <a name="see-also"></a>Voir aussi
- [diagnostic, espace de noms](../profiling/diagnostic-namespace.md)