---
title: Informations de référence sur les règles de performance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5280226aaba40de42052d72e58928a53af53f631
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543635"
---
# <a name="performance-rules-reference"></a>Informations de référence sur les règles de performance
Les règles de performance des outils de profilage fournissent des avertissements et des informations supplémentaires concernant les performances de votre application. Elles analysent les données d’une exécution du profilage qui sont collectées à partir de sources telles que Windows et les compteurs de performance du processeur. Les messages de règle s’affichent dans la fenêtre Sortie d’erreur de l’environnement de développement intégré [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Les messages sont répertoriés avec l’un des niveaux de règle suivants :

|Category|Description|
|-|-|
|**Error**|Peu de règles génèrent des messages d’erreur, car la plupart des problèmes de performances ne sont pas des erreurs franches. Un message d’erreur peut indiquer un échec de collecte des données de profilage.|
|**Avertissement**|Les avertissements indiquent une zone de votre application qui peut potentiellement être une source de problèmes de performances ou qui pourrait tirer profit d’optimisations.|
|**Informations**|Les messages d’information indiquent que l’analyse d’une condition de règle n’a pas atteint le seuil de génération d’un message d’erreur, ou que les informations contenues dans le message sont utiles mais ne reflètent pas un problème de performances.|

## <a name="in-this-section"></a>Dans cette section

[Règles de performance par ID](../profiling/performance-rules-by-id.md)

Les règles de performance des outils de profilage sont organisées en quatre catégories :

|Category|Description|
|-|-|
|[Règles de performance de l’utilisation de .NET Framework](../profiling/dotnet-framework-usage-performance-rules.md)|Règles qui vous aident à utiliser .NET Framework de manière efficace.|
|[Règles de performance de mémoire et de pagination](../profiling/memory-and-paging-performance-rules.md)|Règles qui analysent la mémoire managée et le comportement de pagination de votre application.|
|[Règles d’utilisation de Outils de profilage](../profiling/profiling-tools-usage-rules.md)|Règles qui vous aident à utiliser les outils de profilage de manière efficace.|
|[Règles de performances d’analyse des ressources](../profiling/resource-monitoring-performance-rules.md)|Messages d’information concernant l’utilisation du processeur et de la mémoire dans une exécution du profilage.|
