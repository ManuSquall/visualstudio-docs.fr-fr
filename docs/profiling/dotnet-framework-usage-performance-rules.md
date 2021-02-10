---
title: Règles de performances de l’utilisation du .NET Framework | Microsoft Docs
description: Comprendre les règles de performance dans la catégorie utilisation .NET Framework. Identifiez des méthodes spécifiques qui peuvent être optimisées et identifier des modèles d’utilisation plus généraux.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f8ec2756353ac56b3b5d44e2a50c4d4f5b1c7ebf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955383"
---
# <a name="net-framework-usage-performance-rules"></a>Règles de performance de l’utilisation du .NET Framework
Les règles de performances de la catégorie Utilisation du .NET Framework permettent d’identifier les méthodes qui peuvent être optimisées, ainsi que des modèles d’utilisation plus généraux, tels que le garbage collection et les conflits de verrou, qui peuvent être examinés pour comprendre les problèmes de performances.

|Règle|Description|
|-|-|
|[DA0001 : Utiliser StringBuilder pour les concaténations](../profiling/da0001-use-stringbuilder-for-concatenations.md)|Les appels à <xref:System.String.Concat(System.String,System.String)?displayProperty=fullName> représentent une part importante des données de profilage. Envisagez l’utilisation de la classe <xref:System.Text.StringBuilder> pour construire des chaînes à partir de plusieurs segments.|
|[DA0005 : Collections GC2 fréquentes](../profiling/da0005-frequent-gc2-collections.md)|Un nombre relativement élevé d’objets mémoire .NET est actuellement récupéré dans le cadre d’un garbage collection de génération 2. Si un trop grand nombre d’objets à courte durée de vie survivent au garbage collection de génération 1, le coût de la gestion de mémoire peut facilement devenir excessif.|
|[DA0006 : Remplacer Equals() pour les types valeur](../profiling/da0006-override-equals-parens-for-value-types.md)|Les appels à la méthode `Equals` ou aux opérateurs d’égalité d’un type valeur public représentent une part importante des données de profilage. Implémentez une méthode plus efficace.|
|[DA0007 : Ne pas utiliser d’exceptions pour le flux de contrôle](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|Un taux élevé de gestionnaires d’exceptions .NET Framework ont été appelés dans les données de profilage. Utilisez une autre logique de flux de contrôle pour réduire le nombre d’exceptions levées.|
|[DA0010 : Fonction GetHashCode coûteuse](../profiling/da0010-expensive-gethashcode.md)|Les appels à la méthode `GetHashCode` du type représentent une part importante des données de profilage, ou la méthode `GetHashCode` alloue de la mémoire. Simplifiez la méthode.|
|[DA0011 : Fonction CompareTo coûteuse](../profiling/da0011-expensive-compareto.md)|La méthode `CompareTo` du type est coûteuse ou la méthode alloue de la mémoire. Simplifiez la méthode `CompareTo`.|
|[DA0012 : Quantité importante de réflexion](../profiling/da0012-significant-amount-of-reflection.md)|Les appels aux méthodes <xref:System.Reflection?displayProperty=fullName>, comme <xref:System.Reflection.IReflect.InvokeMember%2A> et <xref:System.Reflection.IReflect.GetMember%2A>, ou à des méthodes de type comme <xref:System.Type.InvokeMember%2A>, représentent une part importante des données de profilage. Si possible, remplacez ces méthodes par une liaison anticipée aux méthodes des assemblys dépendants.|
|[DA0013 : Utilisation intensive de String.Split ou de String.Substring](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|Les appels aux méthodes <xref:System.String.Split%2A?displayProperty=fullName> ou <xref:System.String.Substring%2A> représentent une part importante des données de profilage. Envisagez l’utilisation de <xref:System.String.IndexOf%2A> ou de <xref:System.String.IndexOfAny%2A> si vous testez l’existence d’une sous-chaîne dans une chaîne.|
|[DA0018 : Application 32 bits s’exécutant aux limites de la mémoire managée du processus](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|Les données système collectées pendant le profilage indiquent que les tas de mémoire .NET Framework approchent de la taille maximale autorisée pour les tas managés d’un processus 32 bits. Effectuez un nouveau profilage à l’aide de la méthode de profilage de mémoire .NET et optimisez la manière dont l’application utilise les ressources managées.|
|[DA0021 : Taux élevé de garbage collection Gen 1](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|Un nombre relativement élevé d’objets mémoire .NET est actuellement récupéré dans le cadre d’un garbage collection de génération 1. Si un trop grand nombre d’objets à courte durée de vie survivent au garbage collection de génération 0, le coût de la gestion de mémoire peut facilement devenir excessif.|
|[DA0022 : Taux élevé de garbage collection Gen 2](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|Un nombre élevé d’objets mémoire .NET est actuellement récupéré dans le cadre d’un garbage collection de génération 2. Si un trop grand nombre d’objets à courte durée de vie survivent au garbage collection de génération 1, le coût de la gestion de mémoire peut facilement devenir excessif. Cette règle se déclenche lorsque le taux de conflits de verrou dépasse le seuil défini par la règle DA0005.|
|[DA0023 : Temps processeur GC élevé](../profiling/da0023-high-gc-cpu-time.md)|Les données relatives aux performances système qui sont collectées pendant le profilage indiquent que le temps consacré au garbage collection est très important, par rapport au temps total de traitement de l’application.|
|[DA0024 : temps processeur GC excessif](../profiling/da0024-excessive-gc-cpu-time.md)|Les données relatives aux performances système qui sont collectées pendant le profilage indiquent que le temps consacré au garbage collection est extrêmement important, par rapport au temps total de traitement de l’application. Cette règle se déclenche lorsque le temps consacré au garbage collection dépasse le seuil défini par la règle DA0023.|
|[DA0038 : taux élevé de conflits de verrouillage](../profiling/da0038-high-rate-of-lock-contentions.md)|Les données relatives aux performances système qui sont collectées avec les données de profilage indiquent qu’un taux très élevé de conflits de verrouillage a été relevé lors de l’exécution de l’application. Effectuez un nouveau profilage à l’aide de la méthode de profilage d’accès concurrentiel pour rechercher la cause des conflits.|
|[DA0039 : taux très élevé de conflits de verrouillage](../profiling/da0039-very-high-rate-of-lock-contentions.md)|Les données relatives aux performances système qui sont collectées avec les données de profilage indiquent qu’un taux excessif de conflits de verrouillage a été relevé lors de l’exécution de l’application. Effectuez un nouveau profilage à l’aide de la méthode de profilage d’accès concurrentiel pour rechercher la cause des conflits. Cette règle se déclenche lorsque le taux de conflits de verrou dépasse le seuil défini par la règle DA0038.|
