---
title: 'DA0005 : Collections GC2 fréquentes | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0005
- vs.performance.rules.DAManyGC2Collections
- vs.performance.5
- vs.performance.rules.DA0005
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31a59bf1f53e2757aa5b26019c36f578cbc3f3c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500997"
---
# <a name="da0005-frequent-gc2-collections"></a>DA0005 : Collections GC2 fréquentes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [DA0005 : collections GC2 fréquentes](https://docs.microsoft.com/visualstudio/profiling/da0005-frequent-gc2-collections).  
  
ID de la règle | DA0005 |  
| Catégorie de |. Utilisation de NET Framework |  
| Méthode de profilage |. Mémoire .NET |  
| Message | De nombreux objets sont collectés dans un garbage collection de génération 2. |  
| Type de message | Avertissement |  
  
## <a name="cause"></a>Cause  
 Un nombre élevé d’objets mémoire .NET est actuellement récupéré dans le cadre d’un garbage collection de génération 2.  
  
## <a name="rule-description"></a>Description de la règle  
 Le common language runtime (CLR) Microsoft .NET fournit un mécanisme de gestion automatique de la mémoire qui utilise un récupérateur de mémoire pour récupérer la mémoire des objets que l’application n’utilise plus. Le récupérateur de mémoire est orienté génération et repose sur l’hypothèse que de nombreuses allocations sont de courte durée. Les variables locales, par exemple, doivent avoir une durée de vie courte. Les objets récemment créés commencent à la génération 0 (gen 0), puis progressent jusqu’à la génération 1 lorsqu’ils survivent à l’exécution d’un garbage collection. Enfin, ils passent à la génération 2 si l’application les utilise toujours.  
  
 Les objets de la génération 0 sont collectés fréquemment et généralement de manière très efficace. Les objets de la génération 1 sont collectés moins fréquemment et moins efficacement. Enfin, les objets à longue durée de vie de la génération 2 doivent être collectés encore moins fréquemment. Le garbage collection de génération 2, qui correspond à un garbage collection complet, constitue l’option la plus coûteuse.  
  
 Cette règle est déclenchée lorsque, proportionnellement, un trop grand nombre de garbage collections de génération 2 se sont produits. Si trop d’objets dont la durée de vie est relativement courte survivent au garbage collection de génération 1, mais qu’ils peuvent ensuite être collectés lors d’un garbage collection de génération 2, le coût de la gestion de la mémoire peut aisément devenir excessif. Pour plus d’informations, consultez [Mid-life crisis](http://go.microsoft.com/fwlink/?LinkId=177835) sur le blog Performance Tidbits de Rico Mariani sur le site MSDN.  
  
## <a name="how-to-investigate-a-warning"></a>Comment rechercher la cause d’un avertissement  
 Consultez les rapports [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md) pour comprendre le modèle d’allocation de mémoire de l’application. Utilisez le [vue durée de vie de l’objet](../profiling/object-lifetime-view.md) pour déterminer quels objets sont survivent dans la génération 2 et puis sont récupérés à partir de là de données du programme. Consultez la [vue Allocations](../profiling/dotnet-memory-allocations-view.md) pour connaître le chemin d’exécution qui a entraîné ces allocations.  
  
 Pour plus d’informations sur l’amélioration des performances du garbage collection, consultez [Garbage Collector Basics and Performance Hints](http://go.microsoft.com/fwlink/?LinkId=148226) sur le site de Microsoft. Pour plus d’informations sur la surcharge du garbage collection automatique, consultez [Le tas des objets volumineux dévoilé](http://go.microsoft.com/fwlink/?LinkId=177836).



