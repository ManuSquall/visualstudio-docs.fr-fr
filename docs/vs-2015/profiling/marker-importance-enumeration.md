---
title: marker_importance, énumération | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 853b31ddec99587c9c649e3ee10d77a6f4b4803e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49179450"
---
# <a name="markerimportance-enumeration"></a>marker_importance, énumération
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Représente le niveau d’importance d’un marqueur du visualiseur concurrentiel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
## <a name="requirements"></a>Configuration requise  
 **En-tête** : cvmarkersobj.h  
  
 **Espace de noms** : Concurrency::diagnostic  
  
## <a name="see-also"></a>Voir aussi  
 [diagnostic, espace de noms](../profiling/diagnostic-namespace.md)



