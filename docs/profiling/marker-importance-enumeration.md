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
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613893"
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