---
title: Règles de performances de l’utilisation du .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0706a5279a2ab338cc6e50cce25051b4fba7b366
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756140"
---
# <a name="net-framework-usage-performance-rules"></a>Règles de performance de l'utilisation du .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les règles de performances de la catégorie Utilisation du .NET Framework permettent d’identifier les méthodes qui peuvent être optimisées, ainsi que des modèles d’utilisation plus généraux, tels que le garbage collection et les conflits de verrou, qui peuvent être examinés pour comprendre les problèmes de performances.  
  
|||  
|-|-|  
|[DA0001 : Utilisez StringBuilder pour les concaténations](../profiling/da0001-use-stringbuilder-for-concatenations.md)|Les appels à <xref:System.String.Concat%28System.String%2CSystem.String%29?displayProperty=fullName> représentent une part importante des données de profilage. Envisagez l’utilisation de la classe <xref:System.Text.StringBuilder> pour construire des chaînes à partir de plusieurs segments.|  
|[DA0005 : Collections GC2 fréquentes](../profiling/da0005-frequent-gc2-collections.md)|Un nombre relativement élevé d’objets mémoire .NET est actuellement récupéré dans le cadre d’un garbage collection de génération 2. Si un trop grand nombre d’objets à courte durée de vie survivent au garbage collection de génération 1, le coût de la gestion de mémoire peut facilement devenir excessif.|  
|[DA0006 : Remplacez Equals() pour les types valeur](../profiling/da0006-override-equals-parens-for-value-types.md)|Les appels à la méthode `Equals` ou aux opérateurs d’égalité d’un type valeur public représentent une part importante des données de profilage. Implémentez une méthode plus efficace.|  
|[DA0007 : N’utilisez pas d’exceptions pour le flux de contrôle](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|Un taux élevé de gestionnaires d’exceptions .NET Framework ont été appelés dans les données de profilage. Utilisez une autre logique de flux de contrôle pour réduire le nombre d’exceptions levées.|  
|[DA0010 : GetHashCode coûteux](../profiling/da0010-expensive-gethashcode.md)|Les appels à la méthode `GetHashCode` du type représentent une part importante des données de profilage, ou la méthode `GetHashCode` alloue de la mémoire. Simplifiez la méthode.|  
|[DA0011 : CompareTo coûteux](../profiling/da0011-expensive-compareto.md)|La méthode `CompareTo` du type est coûteuse ou la méthode alloue de la mémoire. Simplifiez la méthode `CompareTo`.|  
|[DA0012 : Quantité importante de réflexion](../profiling/da0012-significant-amount-of-reflection.md)|Les appels aux méthodes <xref:System.Reflection?displayProperty=fullName>, comme <xref:System.Reflection.IReflect.InvokeMember%2A> et <xref:System.Reflection.IReflect.GetMember%2A>, ou à des méthodes de type comme <xref:System.Type.InvokeMember%2A>, représentent une part importante des données de profilage. Si possible, remplacez ces méthodes par une liaison anticipée aux méthodes des assemblys dépendants.|  
|[DA0013 : Utilisation intensive de String.Split ou de String.Substring](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|Les appels aux méthodes <xref:System.String.Split%2A?displayProperty=fullName> ou <xref:System.String.Substring%2A> représentent une part importante des données de profilage. Envisagez l’utilisation de <xref:System.String.IndexOf%2A> ou de <xref:System.String.IndexOfAny%2A> si vous testez l’existence d’une sous-chaîne dans une chaîne.|  
|[DA0018 : Application 32 bits s’exécutant aux limites de la mémoire managée du processus](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|Les données système collectées pendant le profilage indiquent que les tas de mémoire .NET Framework approchent de la taille maximale autorisée pour les tas managés d’un processus 32 bits. Effectuez un nouveau profilage à l’aide de la méthode de profilage de mémoire .NET et optimisez la manière dont l’application utilise les ressources managées.|  
|[DA0021 : Taux élevé de garbage collection Gen 1](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|Un nombre relativement élevé d’objets mémoire .NET est actuellement récupéré dans le cadre d’un garbage collection de génération 1. Si un trop grand nombre d’objets à courte durée de vie survivent au garbage collection de génération 0, le coût de la gestion de mémoire peut facilement devenir excessif.|  
|[DA0022 : taux élevé de garbage collection Gen 2](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|Un nombre élevé d’objets mémoire .NET est actuellement récupéré dans le cadre d’un garbage collection de génération 2. Si un trop grand nombre d’objets à courte durée de vie survivent au garbage collection de génération 1, le coût de la gestion de mémoire peut facilement devenir excessif. Cette règle se déclenche lorsque le taux de conflits de verrou dépasse le seuil défini par la règle DA0005.|  
|[DA0023 : temps processeur GC élevé](../profiling/da0023-high-gc-cpu-time.md)|Les données relatives aux performances système qui sont collectées pendant le profilage indiquent que le temps consacré au garbage collection est très important, par rapport au temps total de traitement de l’application.|  
|[DA0024 : Temps UC GC excessif](../profiling/da0024-excessive-gc-cpu-time.md)|Les données relatives aux performances système qui sont collectées pendant le profilage indiquent que le temps consacré au garbage collection est extrêmement important, par rapport au temps total de traitement de l’application. Cette règle se déclenche lorsque le temps consacré au garbage collection dépasse le seuil défini par la règle DA0023.|  
|[DA0038 : taux élevé de conflits de verrouillage](../profiling/da0038-high-rate-of-lock-contentions.md)|Les données relatives aux performances système qui sont collectées avec les données de profilage indiquent qu’un taux très élevé de conflits de verrouillage a été relevé lors de l’exécution de l’application. Effectuez un nouveau profilage à l’aide de la méthode de profilage d’accès concurrentiel pour rechercher la cause des conflits.|  
|[DA0039 : Taux très élevé de conflits de verrouillage](../profiling/da0039-very-high-rate-of-lock-contentions.md)|Les données relatives aux performances système qui sont collectées avec les données de profilage indiquent qu’un taux excessif de conflits de verrouillage a été relevé lors de l’exécution de l’application. Effectuez un nouveau profilage à l’aide de la méthode de profilage d’accès concurrentiel pour rechercher la cause des conflits. Cette règle se déclenche lorsque le taux de conflits de verrou dépasse le seuil défini par la règle DA0038.|



