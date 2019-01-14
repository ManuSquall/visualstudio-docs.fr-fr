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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 330ba15fa62272bd2c2f7ea7b40d6b527ab237c3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841688"
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
 [diagnostic, espace de noms](../profiling/diagnostic-namespace.md)