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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20b25e2974f4b0e4a6bbf6cf02c411fde3f3de1a
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686543"
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

 **Espace de noms :** Concurrency

## <a name="see-also"></a>Voir aussi
- [Concurrency, espace de noms (visualiseur concurrentiel)](../profiling/concurrency-namespace-concurrency-visualizer.md)