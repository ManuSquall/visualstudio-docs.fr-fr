---
title: Diagnostic, espace de noms | Microsoft Docs
description: Utilisez l’espace de noms diagnostic pour émettre des marqueurs du visualiseur concurrentiel. L’espace de noms diagnostic est membre de l’espace de noms d’accès concurrentiel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic
helpviewer_keywords:
- Concurrency, diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22224e375c1d1f463f1c07d41ca5a03efa5cabdb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923740"
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
|[marker_series, classe](../profiling/marker-series-class.md)|Représente un canal série d’événements générés par un fournisseur unique.|
|[span, classe](../profiling/span-class.md)|Définit une phase de l’application.|

### <a name="enumerations"></a>Énumérations

|Nom|Description|
|----------|-----------------|
|[marker_importance, énumération](../profiling/marker-importance-enumeration.md)|Représente le niveau d’importance d’un marqueur du visualiseur concurrentiel.|

## <a name="requirements"></a>Configuration requise
 **En-tête :** *cvmarkersobj.h*

 **Espace de noms :** Concurrency

## <a name="see-also"></a>Voir aussi
- [Concurrency, espace de noms (visualiseur concurrentiel)](../profiling/concurrency-namespace-concurrency-visualizer.md)