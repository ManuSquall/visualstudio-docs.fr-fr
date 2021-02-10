---
title: Règles de performances de la surveillance des ressources | Microsoft Docs
description: Découvrez comment les messages de performance dans la catégorie d’analyse des ressources fournissent des données supplémentaires sur les performances de votre application.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1fc17bd86868a7b3e87c47ec44fd5caabf7a6cfd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950141"
---
# <a name="resource-monitoring-performance-rules"></a>Règles de performance de l'analyse de ressource
Les messages liés aux performances de la catégorie Surveillance des ressources fournissent des données supplémentaires sur les performances de votre application. Vous pouvez utiliser ces données pour analyser les problèmes de performances. Ces règles fournissent des informations et sont signalées pour chaque exécution du profilage.

|Règle|Description|
|-|-|
|[DA0501 : consommation processeur moyenne par le processus en cours de profilage.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|Ce message indique le temps, en pourcentage, pendant lequel un processeur a exécuté des instructions à partir de l’application. La valeur signalée correspond à la moyenne de tous les intervalles de mesure pendant lesquels le processus profilé était actif.|
|[DA0502 : Consommation CPU maximale par le processus en cours de profilage](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|Ce message indique le temps maximal, en pourcentage, pendant lequel un processeur a exécuté des instructions à partir de l’application. La valeur signalée correspond à la valeur maximale de tous les intervalles de mesure pendant lesquels le processus profilé était actif.|
|[DA0503 : Jeu de travail moyen en octets pour le processus en cours de profilage](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Ce message indique la quantité moyenne de mémoire physique, en octets, utilisée par le processus pendant que profilage était actif. Cette mesure de la mémoire physique est appelée la plage de travail.|
|[DA0504 : jeu de travail maximal en octets pour le processus en cours de profilage](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Ce message indique la quantité maximale de mémoire physique, en octets, utilisée par le processus pendant que profilage était actif.|
|[DA0505 : Octets privés alloués en moyenne au processus en cours de profilage](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Ce message indique la quantité moyenne de mémoire virtuelle, en octets, allouée par le processus pendant que profilage était actif. Cette mesure de la mémoire virtuelle est appelée *octets privés*. Les octets privés représentent les emplacements de mémoire virtuelle alloués par le processus et qui ne sont accessibles qu’aux threads actuellement exécutés dans le processus.|
|[DA0506 : Octets privés alloués au maximum au processus en cours de profilage](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Ce message indique la quantité maximale de mémoire virtuelle, en octets privés, allouée par le processus pendant que profilage était actif.|
