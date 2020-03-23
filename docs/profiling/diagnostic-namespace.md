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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62970081"
---
# <a name="diagnostic-namespace"></a>diagnostic, espace de noms
L’espace de noms `diagnostics` fournit des fonctionnalités permettant d’émettre des marqueurs du visualiseur concurrentiel.

## <a name="syntax"></a>Syntaxe

```cpp
namespace diagnostic;
```

## <a name="members"></a>Membres

### <a name="classes"></a>Classes

|Nom|Description|
|----------|-----------------|
|[Classe marker_series](../profiling/marker-series-class.md)|Représente un canal série d’événements générés par un fournisseur unique.|
|[span, classe](../profiling/span-class.md)|Définit une phase de l’application.|

### <a name="enumerations"></a>Énumérations

|Nom|Description|
|----------|-----------------|
|[marker_importance, énumération](../profiling/marker-importance-enumeration.md)|Représente le niveau d’importance d’un marqueur du visualiseur concurrentiel.|

## <a name="requirements"></a>Spécifications
 **En-tête :** *cvmarkersobj.h*

 **Espace de noms :** Concurrency

## <a name="see-also"></a>Voir aussi
- [Espace de nom de concurrency (Visuel de concurrency)](../profiling/concurrency-namespace-concurrency-visualizer.md)