---
title: DA0004-utilisation intensive du processeur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b3a067ae9e884ca7f6a4592dbd827eb0c028876a
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332052"
---
# <a name="da0004-high-processor-usage"></a>DA0004 : Utilisation intensive du processeur

|||
|-|-|
|ID de règle|DA0004|
|Category|Utilisation des outils de profilage|
|Méthodes de profilage|Instrumentation<br /><br /> échantillonnage|
|Message|L’utilisation de votre processeur est supérieure à 75 %. Utilisez le mode d’échantillonnage pour les applications utilisant le processeur de façon intensive.|
|Type de règle|Information|

 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.

## <a name="cause"></a>Cause
 L’utilisation du processeur (UC) était élevée dans les données de profilage qui ont été collectées à l’aide de la méthode d’instrumentation. Utilisez la méthode de profilage par échantillonnage lorsque vous profilez une application utilisant le processeur de manière intensive.

## <a name="rule-description"></a>Description de la règle
 Pendant cette exécution de profilage, le ou les processeurs étaient constamment occupés. Une utilisation élevée du processeur peut indiquer qu’une application utilise le processeur de manière intensive. Les profils instrumentés ne sont pas les plus efficaces pour étudier les scénarios d’utilisation du processeur. L’échantillonnage est plus efficace lorsque vous profilez des applications qui consacrent beaucoup de temps à exécuter des instructions dans le processeur.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Profilez votre application à l’aide de la méthode d’échantillonnage au lieu de la méthode d’instrumentation, sauf si vous avez besoin de minutage de fonctions ou si vous êtes plus intéressé par les E/S que par les goulots d’étranglement du processeur.
