---
title: 'DA0011 : Fonction CompareTo coûteuse'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d0eb4566fd4c8a513b1492cecffc16cb94a1fd83
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779426"
---
# <a name="da0011-expensive-compareto"></a>DA0011 : CompareTo coûteux

|||
|-|-|
|ID de règle|DA0011|
|Category|Utilisation du .NET Framework|
|Méthodes de profilage|échantillonnage<br /><br /> Mémoire .NET|
|Message|Les fonctions CompareTo doivent être peu coûteuses et n’allouer aucune mémoire. Réduisez si possible la complexité de la fonction CompareTo.|
|Type de règle|Avertissement|

## <a name="cause"></a>Cause :
 La méthode CompareTo du type est coûteuse ou alloue de la mémoire.

## <a name="rule-description"></a>Description de la règle
 Les méthodes CompareTo doivent être efficaces et ne doivent pas allouer de mémoire.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Réduisez la complexité de la méthode CompareTo.
