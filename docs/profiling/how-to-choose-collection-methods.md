---
title: 'Procédure : Choisir une méthode de collecte | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43759d33c776e7ca4a6bdd8269df4bee0f882a53
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982934"
---
# <a name="how-to-choose-collection-methods"></a>Procédure : Choisir des méthodes de collecte

Les Outils de profilage de Visual Studio prennent en charge trois méthodes de collecte des données de performances : l’échantillonnage, l’instrumentation et la concurrence. Vous pouvez également utiliser les méthodes d’instrumentation et d’échantillonnage pour collecter des données de durée de vie et d’allocation de la mémoire .NET.

Vous pouvez utiliser la propriété **Method** de session de performance pour spécifier la méthode de collecte la plus appropriée pour votre application. Vous pouvez définir la méthode de collecte à partir de l’Assistant Performance, de l’Explorateur de performances ou des pages de propriétés d’une session de performance. Pour plus d’informations sur l’utilisation des outils en ligne de commande, consultez [Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md).

## <a name="performance-wizard"></a>Assistant Performance

### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>Pour sélectionner une méthode de collecte à l’aide de l’Assistant Performance

- Dans la première page de l’Assistant, sélectionnez l’une des options suivantes :

| Option | Description |
|----------------------------| - |
| **Échantillonnage de l’UC** | Collecte les statistiques d’application qui sont utiles pour l’analyse initiale et l’analyse des problèmes d’utilisation du processeur. |
| **Instrumentation** | Collecte des données de minutage détaillées utiles pour une analyse approfondie et pour l’analyse des problèmes de performances d’E/S. |
| **Allocation de mémoire .NET** | Collecte les données d’allocation de mémoire [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] à l’aide de la méthode de profilage par échantillonnage. |
| **Concurrence** | Collecte des données numériques concernant les conflits de ressources. |

## <a name="performance-explorer"></a>Explorateur de performances

### <a name="to-select-a-collection-method-using-performance-explorer"></a>Pour sélectionner une méthode de collecte à l’aide de l’Exploration de performances

1. Dans la barre d’outils **Explorateur de performances**, cliquez sur la flèche située à côté de la liste déroulante **Méthode**.

2. Cliquez sur la méthode de collecte de votre choix.

## <a name="performance-session-property-pages"></a>Pages de propriétés d’une session de performance

### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>Pour sélectionner la méthode d’échantillonnage ou d’instrumentation à l’aide des propriétés de session de performance

1. Dans l’**Explorateur de performances**, sélectionnez la session de performance.

     Un nom de fichier de session de performance a une extension .*psess*.

2. Cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.

3. Dans **Pages de propriétés**, cliquez sur **Général**.

4. Cliquez sur la méthode de collecte de votre choix.

    - Pour plus d’informations sur les autres options disponibles lorsque vous collectez des données d’échantillonnage, consultez [Collecte de statistiques de performances à l’aide de l’échantillonnage](../profiling/collecting-performance-statistics-by-using-sampling.md)

    - Pour plus d’informations sur les autres options disponibles lorsque vous collectez des données d’échantillonnage, consultez [Collecte de données de minutage détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).

### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>Pour sélectionner la collecte de données de mémoire .NET à l’aide des propriétés de session de performance

1. Dans l’**Explorateur de performances**, sélectionnez la session de performance.

     Le nom des fichiers de session de performance se termine par l’extension .psess.

2. Cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.

3. Dans **Pages de propriétés**, cliquez sur **Général**.

4. Cliquez sur **Échantillonnage** ou **Instrumentation**.

5. Cliquez sur **Collecter les informations d’allocation d’objets .NET** pour collecter le nombre d’allocations d’objets [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], ainsi que leur taille.

6. (Facultatif) Cliquez sur **Collecter aussi les informations de durée de vie des objets .NET** pour collecter des données sur les générations de garbage collection dans lesquelles la mémoire d’objets a été récupérée.

     Pour plus d’informations sur les autres options disponibles quand vous collectez des données de mémoire .NET, consultez [Collecter les données liées à l’allocation et à la durée de vie de la mémoire .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).

### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>Pour sélectionner la collecte de données d’accès concurrentiel à l’aide des propriétés de session de performance

1. Dans l’ **Explorateur de performances**, cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.

2. Dans **Pages de propriétés**, cliquez sur **Général**.

3. Cliquez sur **Concurrence**.

## <a name="see-also"></a>Voir aussi

[Configurer des sessions de performances](../profiling/configuring-performance-sessions.md)  
[Fonctionnement des valeurs de données d’échantillonnage](../profiling/understanding-sampling-data-values.md)  
[Propriétés d’une session de performance](../profiling/performance-session-properties.md)