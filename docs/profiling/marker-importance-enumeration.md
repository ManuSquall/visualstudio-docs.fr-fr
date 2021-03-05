---
description: Représente le niveau d’importance d’un marqueur du visualiseur concurrentiel.
title: marker_importance, énumération | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_importance
helpviewer_keywords:
- Concurrency, diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2c2e7560c91882afe1ee2608bb2ae2fc105738dc
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223938"
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
- [espace de noms diagnostic](../profiling/diagnostic-namespace.md)
