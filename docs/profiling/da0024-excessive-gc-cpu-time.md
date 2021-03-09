---
title: DA0024-temps processeur GC excessif | Microsoft Docs
description: Les données relatives aux performances système qui sont collectées pendant le profilage indiquent que le temps consacré au garbage collection est extrêmement important, par rapport au temps total de traitement de l’application.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0024
- vs.performance.24
- vs.performance.rules.DA0024
ms.assetid: 228872da-77d0-4da5-b455-ac57fb1867c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5de3d2e65707e9f6451c60b1a6210cb25c0b6902
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465970"
---
# <a name="da0024-excessive-gc-cpu-time"></a>DA0024 : temps processeur GC excessif

|Élément|Valeur|
|-|-|
|ID de règle|DA0024|
|Category|Utilisation du .NET Framework|
|Méthode de profilage|Tous|
|Message|% de temps dans GC très élevé. % de temps dans GC très élevé. Volume de surcharge de garbage collection trop élevé.|
|Type de règle|Avertissement|

 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.

## <a name="cause"></a>Cause
 Les données relatives aux performances système qui sont collectées pendant le profilage indiquent que le temps consacré au garbage collection est extrêmement important, par rapport au temps total de traitement de l’application.

## <a name="rule-description"></a>Description de la règle
 Le common language runtime (CLR) Microsoft .NET fournit un mécanisme de gestion automatique de la mémoire qui utilise un récupérateur de mémoire pour récupérer la mémoire des objets que l’application n’utilise plus. Le récupérateur de mémoire est orienté génération et repose sur l’hypothèse que de nombreuses allocations sont de courte durée. Les variables locales, par exemple, doivent avoir une durée de vie courte. Les objets récemment créés commencent à la génération 0 (gen 0), puis progressent jusqu’à la génération 1 lorsqu’ils survivent à l’exécution d’un garbage collection. Enfin, ils passent à la génération 2 si l’application les utilise toujours.

 Les objets de la génération 0 sont collectés fréquemment et généralement de manière très efficace. Les objets de la génération 1 sont collectés moins fréquemment et moins efficacement. Enfin, les objets à longue durée de vie de la génération 2 doivent être collectés encore moins fréquemment. Le garbage collection de génération 2, qui correspond à un garbage collection complet, constitue l’option la plus coûteuse.

 Cette règle se déclenche lorsque le temps consacré au garbage collection est extrêmement important, par rapport au temps total de traitement de l’application.

> [!NOTE]
> Lorsque le temps consacré au garbage collection est important, mais pas excessif par rapport au temps total de traitement de l’application, l’avertissement [DA0023 : Temps CPU GC élevé](../profiling/da0023-high-gc-cpu-time.md) est déclenché à la place de cette règle.

## <a name="how-to-investigate-a-warning"></a>Comment rechercher la cause d’un avertissement
 Double-cliquez sur le message dans la fenêtre Liste d’erreurs pour accéder à la [vue Marques](../profiling/marks-view.md) des données de profilage. Accédez à la colonne **Mémoire CLR .NET\\% temps dans le GC**. Déterminez s’il existe des phases spécifiques de l’exécution du programme durant lesquelles la surcharge du garbage collection de mémoire managée est plus importante. Comparez les valeurs de la colonne % temps dans le GC au taux du garbage collection des colonnes **Nombre de collections de la génération 0**, **Nombre de collections de la génération 1** et **Nombre de collections de la génération 2**.

 La colonne % temps dans le GC contient le pourcentage de temps qu’une application a consacré au garbage collection, proportionnellement au temps total de traitement. Sachez que dans certaines circonstances, la valeur % temps dans le GC peut indiquer une valeur élevée sans qu’un garbage collection excessif en soit la cause. Pour plus d’informations sur la façon dont la valeur% temps dans le GC est calculée, consultez la [différence entre les données de performances signalées par différents outils-4](https://devblogs.microsoft.com/maoni/archive/difference-between-perf-data-reported-by-different-tools-4.aspx) entrée du **Weblog de maoni** sur MSDN. Si des défauts de page se produisent ou si l’application est préemptée par d’autres travaux prioritaires sur la machine pendant le garbage collection, le compteur % temps dans le GC reflète ces retards supplémentaires.
