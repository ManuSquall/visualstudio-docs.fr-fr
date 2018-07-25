---
title: marker_importance, énumération | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 6541ddecceff6d9e7867dd5feead3457b2248b45
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844116"
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
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** *cvmarkersobj.h*  
  
 **Espace de noms** : Concurrency::diagnostic  
  
## <a name="see-also"></a>Voir aussi  
 [diagnostic, espace de noms](../profiling/diagnostic-namespace.md)