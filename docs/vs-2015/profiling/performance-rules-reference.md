---
title: Informations de référence sur les règles de performance | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 48659a0b5981d545a706abfcaa7c3db24052cd20
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548406"
---
# <a name="performance-rules-reference"></a>Informations de référence sur les règles de performance
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les règles de performance des outils de profilage fournissent des avertissements et des informations supplémentaires concernant les performances de votre application. Elles analysent les données d’une exécution du profilage qui sont collectées à partir de sources telles que Windows et les compteurs de performance du processeur. Les messages de règle s’affichent dans la fenêtre Sortie d’erreur de l’environnement de développement intégré [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Les messages sont répertoriés avec l’un des niveaux de règle suivants :  
  
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
