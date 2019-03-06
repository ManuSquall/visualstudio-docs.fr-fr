---
title: 'DA0011 : Fonction CompareTo coûteuse | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 06e723fc30bfde69344218beaca4e1c0b3c5d742
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804161"
---
# <a name="da0011-expensive-compareto"></a>DA0011 : Fonction CompareTo coûteuse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la dernière documentation sur Visual Studio 2017, consultez [DA0011 : CompareTo coûteux](https://docs.microsoft.com/visualstudio/profiling/da0011-expensive-compareto) sur docs.microsoft.com.  
  
|||  
|-|-|  
|ID de règle|DA0011|  
|Category|Utilisation du .NET Framework|  
|Méthodes de profilage|Échantillonnage<br /><br /> Mémoire .NET|  
|Message|Les fonctions CompareTo doivent être peu coûteuses et n’allouer aucune mémoire. Réduisez si possible la complexité de la fonction CompareTo.|  
|Type de règle|Warning|  
  
## <a name="cause"></a>Cause  
 La méthode CompareTo du type est coûteuse ou alloue de la mémoire.  
  
## <a name="rule-description"></a>Description de la règle  
 Les méthodes CompareTo doivent être efficaces et ne doivent pas allouer de mémoire.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Réduisez la complexité de la méthode CompareTo.
