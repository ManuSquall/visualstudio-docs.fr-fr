---
title: 'DA0022 : Taux élevé de garbage collection Gen 2 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0022
- vs.performance.rules.DA0022
- vs.performance.22
ms.assetid: f871a547-0e6f-4b11-b2d7-174d30fc2ed8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be0c156cc4b47bc4ebedd169b099a538941f56d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936396"
---
# <a name="da0022-high-rate-of-gen-2-garbage-collections"></a>DA0022 : Taux élevé de garbage collection Gen 2

|||
|-|-|
|ID de règle|DA0022|
|Category|Utilisation du .NET Framework|
|Méthode de profilage|Tous|
|Message|Taux relativement élevé de garbage collection Gen 2. Si, par conception, la plupart des structures de données de votre programme sont allouées et persistent pour longtemps, cela ne pose pas de problème. Cependant, si ce comportement est involontaire, votre application peut épingler des objets. Si vous n’êtes pas sûr, vous pouvez regrouper les données d’allocation de mémoire .NET et les informations de durée de vie des objets afin de comprendre le modèle d’allocation de mémoire utilisé par votre application.|
|Type de règle|Warning|

 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.

## <a name="cause"></a>Cause
 Les données relatives aux performances système qui ont été collectées pendant le profilage indiquent qu’une importante quantité de mémoire allouée aux objets .NET Framework a été récupérée dans la génération 2 du garbage collection, par rapport aux garbage collections de génération 0 et 1.

## <a name="rule-description"></a>Description de la règle
 Le common language runtime (CLR) Microsoft .NET fournit un mécanisme de gestion automatique de la mémoire qui utilise un récupérateur de mémoire pour récupérer la mémoire des objets que l’application n’utilise plus. Le récupérateur de mémoire est orienté génération et repose sur l’hypothèse que de nombreuses allocations sont de courte durée. Les variables locales, par exemple, doivent avoir une durée de vie courte. Les objets récemment créés commencent à la génération 0 (gen 0), puis progressent jusqu’à la génération 1 lorsqu’ils survivent à l’exécution d’un garbage collection. Enfin, ils passent à la génération 2 si l’application les utilise toujours.

 Les objets de la génération 0 sont collectés fréquemment et généralement de manière très efficace. Les objets de la génération 1 sont collectés moins fréquemment et moins efficacement. Enfin, les objets à longue durée de vie de la génération 2 doivent être collectés encore moins fréquemment. Le garbage collection de génération 2, qui correspond à un garbage collection complet, constitue l’option la plus coûteuse.

 Cette règle est déclenchée lorsque, proportionnellement, un trop grand nombre de garbage collections de génération 2 se sont produits. Les applications .NET Framework au comportement normal auront 5 fois plus de garbage collections de génération 1 que de garbage collections de génération 2 (un facteur 10x est probablement idéal).

## <a name="how-to-investigate-a-warning"></a>Comment rechercher la cause d’un avertissement
 Double-cliquez sur le message dans la fenêtre Liste d’erreurs pour accéder à la [vue Marques](../profiling/marks-view.md) des données de profilage. Accédez aux colonnes **Mémoire CLR .NET\\Nombre de collections de la génération 0** et **Mémoire CLR .NET\\Nombre de collections de la génération 1**. Déterminez s’il existe des phases spécifiques de l’exécution du programme durant lesquelles les garbage collections sont plus fréquents. Comparez ces valeurs à celles de la colonne **% temps dans le GC** pour voir si le modèle des allocations de mémoire managée provoque une charge excessive de gestion de la mémoire.

 Une proportion élevée de garbage collections de génération 2 ne constitue pas toujours un problème. Cela peut être dû à la conception. Cette règle peut être déclenchée lorsqu’une application alloue des structures de données volumineuses qui doivent rester actives pendant de longues périodes au cours de l’exécution. Lorsque la mémoire d’une telle application est sous pression, celle-ci peut être forcée d’effectuer des garbage collections fréquents. Si les garbage collections de génération 0 et de génération 1, qui sont moins coûteux, ne peuvent récupérer qu’une petite quantité de la mémoire managée, des garbage collections de génération 2 plus fréquents seront planifiés.

 La vue Marques comprend d’autres colonnes Mémoire CLR .NET qui peuvent vous aider à identifier les problèmes de garbage collection. La colonne **% temps dans le GC** vous permet d’évaluer le niveau de surcharge de la gestion de mémoire. Si, en général, votre application utilise peu d’objets volumineux et persistants, les fréquents garbage collections de génération 2 ne doivent pas consommer de quantités excessives du temps processeur. Si la mémoire de l’application est sous pression en raison d’un besoin accru en mémoire physique (RAM), les règles associées qui évaluent les valeurs de la colonne **Mémoire\Pages/s** peuvent également être déclenchées.

 Pour comprendre la façon dont l’application utilise la mémoire managée, profilez-la de nouveau en exécutant un profil d’allocation de mémoire .NET et sélectionnez l’option de profilage Durée de vie des objets.

 Pour plus d’informations sur l’amélioration des performances du garbage collection, consultez [Garbage Collector Basics and Performance Hints](http://go.microsoft.com/fwlink/?LinkId=148226) sur le site de Microsoft. Pour plus d’informations sur la surcharge du garbage collection automatique, consultez [Le tas des objets volumineux dévoilé](http://go.microsoft.com/fwlink/?LinkId=177836).