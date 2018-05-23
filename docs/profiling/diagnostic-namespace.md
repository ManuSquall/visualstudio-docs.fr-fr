---
title: Diagnostic, espace de noms | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3c3e6909bcb7299f4fd6d725334c26d2b59e0edb
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2018
---
# <a name="diagnostic-namespace"></a>diagnostic, espace de noms
L’espace de noms `diagnostics` fournit des fonctionnalités permettant d’émettre des marqueurs du visualiseur concurrentiel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
namespace diagnostic;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="classes"></a>Classes  
  
|Name|Description|  
|----------|-----------------|  
|[marker_series, classe](../profiling/marker-series-class.md)|Représente un canal série d’événements générés par un fournisseur unique.|  
|[span, classe](../profiling/span-class.md)|Définit une phase de l’application.|  
  
### <a name="enumerations"></a>Énumérations  
  
|Name|Description|  
|----------|-----------------|  
|[marker_importance, énumération](../profiling/marker-importance-enumeration.md)|Représente le niveau d’importance d’un marqueur du visualiseur concurrentiel.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête** : cvmarkersobj.h  
  
 **Espace de noms :** Concurrency  
  
## <a name="see-also"></a>Voir aussi  
 [Concurrency, espace de noms (visualiseur concurrentiel)](../profiling/concurrency-namespace-concurrency-visualizer.md)