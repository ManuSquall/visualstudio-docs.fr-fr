---
title: DA0011-CompareTo coûteux | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: e3b21745454a74d0251dad547ab45e845190f06d
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328182"
---
# <a name="da0011-expensive-compareto"></a>DA0011 : Fonction CompareTo coûteuse

|||
|-|-|
|ID de règle|DA0011|
|Category|Utilisation du .NET Framework|
|Méthodes de profilage|échantillonnage<br /><br /> Mémoire .NET|
|Message|Les fonctions CompareTo doivent être peu coûteuses et n’allouer aucune mémoire. Réduisez si possible la complexité de la fonction CompareTo.|
|Type de règle|Avertissement|

## <a name="cause"></a>Cause
 La méthode CompareTo du type est coûteuse ou alloue de la mémoire.

## <a name="rule-description"></a>Description de la règle
 Les méthodes CompareTo doivent être efficaces et ne doivent pas allouer de mémoire.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Réduisez la complexité de la méthode CompareTo.
