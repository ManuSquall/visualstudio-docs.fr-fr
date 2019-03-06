---
title: Diagnostic, espace de noms | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03671f314dca3c016f9524bcb246b74e0eb1f837
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56600671"
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

## <a name="requirements"></a>Spécifications
 **En-tête :** *cvmarkersobj.h*

 **Espace de noms :** Concurrence

## <a name="see-also"></a>Voir aussi
- [Concurrency, espace de noms (visualiseur concurrentiel)](../profiling/concurrency-namespace-concurrency-visualizer.md)