---
title: DA0502-consommation processeur maximale par le processus en cours de profilage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 988e9576f7c5aacac4bc4335f06b08dd1176f847
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918109"
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502 : consommation UC maximale par le processus en cours de profilage

|Élément|Valeur|
|-|-|
|ID de règle|DA0502|
|Category|Analyse des ressources|
|Méthode de profilage|Tous|
|Message|Règle uniquement pour informations. Le compteur Processus()\\% temps processus mesure la consommation CPU du processus que vous profilez. La valeur signalée correspond à la valeur maximale observée dans l’ensemble des intervalles de mesure.|
|Type de règle|Informationnel|

 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.

## <a name="rule-description"></a>Description de la règle
 Ce message indique le temps maximal, en pourcentage, pendant lequel un processeur a exécuté des instructions à partir de l’application. La valeur signalée correspond à la valeur maximale de tous les intervalles de mesure pendant lesquels le processus profilé était actif. Cette valeur peut être supérieure à 100 % sur les ordinateurs qui comprennent plusieurs processeurs.

## <a name="how-to-use-the-rule-data"></a>Comment utiliser les données de règle
 Utilisez la valeur de la règle pour comparer les performances des différentes versions du programme ou pour comprendre les performances de l’application dans différents scénarios de profilage.
