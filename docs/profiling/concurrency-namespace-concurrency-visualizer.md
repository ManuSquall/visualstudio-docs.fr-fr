---
title: Concurrency, espace de noms (visualiseur concurrentiel) | Microsoft Docs
description: Pour écrire des programmes simultanés en C++, utilisez l’espace de noms d’accès concurrentiel, qui permet d’accéder au runtime d’accès concurrentiel, une infrastructure d’accès concurrentiel pour C++.
custom.ms: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: 001fbfce-a278-4502-aa27-26d65dd61453
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bdb9f2cee62c126f7a8b91fb7be57f558c9a7e5c
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533431"
---
# <a name="concurrency-namespace-concurrency-visualizer"></a>Concurrency, espace de noms (visualiseur concurrentiel)
L'espace de noms `Concurrency` fournit des classes et des fonctions qui vous donnent accès au runtime d'accès concurrentiel, infrastructure de programmation simultanée pour C++. Pour plus d'informations, consultez [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime).

## <a name="syntax"></a>Syntaxe

```cpp
namespace Concurrency;
```

## <a name="members"></a>Membres

### <a name="namespaces"></a>Espaces de noms

|Nom|Description|
|----------|-----------------|
|[Espace de noms diagnostic](../profiling/diagnostic-namespace.md)|L’espace de noms `diagnostics` fournit des fonctionnalités permettant d’émettre des marqueurs du visualiseur concurrentiel.|

## <a name="requirements"></a>Configuration requise
 **En-tête** : cvmarkersobj.h

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur la bibliothèque C](../profiling/c-library-reference.md)