---
title: 'DA0005 : Collections GC2 fréquentes | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0005
- vs.performance.rules.DAManyGC2Collections
- vs.performance.5
- vs.performance.rules.DA0005
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5e3038f873895e38cf162e67316bc08f2fc007b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849370"
---
# <a name="da0005-frequent-gc2-collections"></a>DA0005 : Collections GC2 fréquentes

|||  
|-|-|  
|RuleId|DA0005|  
|Category|Utilisation du .NET Framework|  
|Méthode de profilage|Mémoire .NET|  
|Message|Bon nombre de vos objets sont collectés dans un garbage collection de génération 2.|  
|Type de message|Warning|  

## <a name="cause"></a>Cause  
 Un nombre élevé d’objets mémoire .NET est actuellement récupéré dans le cadre d’un garbage collection de génération 2.  

## <a name="rule-description"></a>Description de la règle  
 Le common language runtime (CLR) Microsoft .NET fournit un mécanisme de gestion automatique de la mémoire qui utilise un récupérateur de mémoire pour récupérer la mémoire des objets que l’application n’utilise plus. Le récupérateur de mémoire est orienté génération et repose sur l’hypothèse que de nombreuses allocations sont de courte durée. Les variables locales, par exemple, doivent avoir une durée de vie courte. Les objets récemment créés commencent à la génération 0 (gen 0), puis progressent jusqu’à la génération 1 lorsqu’ils survivent à l’exécution d’un garbage collection. Enfin, ils passent à la génération 2 si l’application les utilise toujours.  

 Les objets de la génération 0 sont collectés fréquemment et généralement de manière très efficace. Les objets de la génération 1 sont collectés moins fréquemment et moins efficacement. Enfin, les objets à longue durée de vie de la génération 2 doivent être collectés encore moins fréquemment. Le garbage collection de génération 2, qui correspond à un garbage collection complet, constitue l’option la plus coûteuse.  

 Cette règle est déclenchée lorsque, proportionnellement, un trop grand nombre de garbage collections de génération 2 se sont produits. Si trop d’objets dont la durée de vie est relativement courte survivent au garbage collection de génération 1, mais qu’ils peuvent ensuite être collectés lors d’un garbage collection de génération 2, le coût de la gestion de la mémoire peut aisément devenir excessif. Pour plus d’informations, consultez [Mid-life crisis](http://go.microsoft.com/fwlink/?LinkId=177835) sur le blog Performance Tidbits de Rico Mariani sur le site MSDN.  

## <a name="how-to-investigate-a-warning"></a>Comment rechercher la cause d’un avertissement  
 Consultez les rapports [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md) pour comprendre le modèle d’allocation de mémoire de l’application. Consultez la [vue Durée de vie des objets](../profiling/object-lifetime-view.md) pour déterminer quels objets de données du programme passent d’une génération 2 à une autre, puis sont récupérés. Consultez la [vue Allocations](../profiling/dotnet-memory-allocations-view.md) pour connaître le chemin d’exécution qui a entraîné ces allocations.  

 Pour plus d’informations sur l’amélioration des performances du garbage collection, consultez [Garbage Collector Basics and Performance Hints](http://go.microsoft.com/fwlink/?LinkId=148226) sur le site de Microsoft. Pour plus d’informations sur la surcharge du garbage collection automatique, consultez [Le tas des objets volumineux dévoilé](http://go.microsoft.com/fwlink/?LinkId=177836).