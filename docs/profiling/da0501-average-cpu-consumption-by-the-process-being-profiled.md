---
title: DA0501-consommation processeur moyenne par le processus en cours de profilage. | Microsoft Docs
description: Ce message indique le temps, en pourcentage, pendant lequel un processeur a exécuté des instructions à partir de l’application.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 242a3ff10042a53997b17f662af145440df2e95a
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465827"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501 : consommation UC moyenne par le processus en cours de profilage.

|Élément|Valeur|
|-|-|
|ID de règle|DA501|
|Category|Analyse des ressources|
|Méthode de profilage|Tous|
|Message|Consommation UC moyenne par le processus en cours de profilage.|
|Type de règle|Information|

 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.

## <a name="rule-description"></a>Description de la règle
 Ce message indique le temps, en pourcentage, pendant lequel un processeur a exécuté des instructions à partir de l’application. La valeur signalée correspond à la moyenne de tous les intervalles de mesure pendant lesquels le processus profilé était actif. Cette valeur peut être supérieure à 100 % sur les ordinateurs qui comprennent plusieurs processeurs.

## <a name="how-to-use-rule-data"></a>Comment utiliser les données de règle
 Utilisez la valeur de la règle pour comparer les performances des différentes versions du programme ou pour comprendre les performances de l’application dans différents scénarios de test.
