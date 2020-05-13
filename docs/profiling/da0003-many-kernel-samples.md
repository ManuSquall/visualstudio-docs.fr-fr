---
title: 'DA0003 : Nombreux échantillons de noyau | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 69cd81943641e4e0585a67127c70d35a601a5396
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777736"
---
# <a name="da0003-many-kernel-samples"></a>DA0003 : Nombreux échantillons de noyau

|||
|-|-|
|ID de règle|DA0003|
|Category|Utilisation des outils de profilage|
|Méthodes de profilage|échantillonnage|
|Message|Vous avez une proportion élevée d’échantillons en mode noyau. Ceci peut indiquer un volume élevé d’activité d’E/S ou un taux élevé de changements de contexte. Envisagez de reprofiler votre application avec le mode Instrumentation.|
|Type de règle|Information|

## <a name="cause"></a>Cause :
 Une proportion importante des échantillons de pile des appels qui ont été collectés pour l’application s’exécutaient en mode noyau. Envisagez de profiler votre application avec une autre méthode de profilage.

## <a name="rule-description"></a>Description de la règle
 Dans Windows, le code peut être exécuté en mode noyau ou en mode utilisateur. (Le mode Kernel est également appelé mode privilégié.) Seul le code système de bas niveau, tel qu’un pilote d’appareil, fonctionne en mode noyau. Une application en mode utilisateur peut passer en mode noyau pour effectuer des opérations d’E/S, pour attendre des primitives de synchronisation de thread ou de processus, ou pour effectuer des appels système.

 L’échantillonnage est plus efficace quand vous profilez des applications qui passent la majeure partie de leur temps à travailler en mode utilisateur. Le nombre d’échantillons qui ont été recueillis quand l’application s’exécutait en mode noyau peut indiquer des opérations d’E/S fréquentes ou que des changements de contexte se produisent. Aucune de ces opérations ne peut être examinée avec la méthode d’échantillonnage. Si trop grand nombre d’échantillons en mode noyau sont pris, les données d’échantillonnage peuvent ne pas contenir suffisamment d’échantillons en mode utilisateur pour être statistiquement significatives.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Envisagez de reprofiler votre application avec une des options suivantes :

- Profilez avec la méthode d’instrumentation.

- Augmentez le taux d’échantillonnage pour essayer de collecter plus d’échantillons en mode utilisateur.
