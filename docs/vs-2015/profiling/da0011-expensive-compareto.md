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
ms.openlocfilehash: 86d41a2717eb3ef7bd49f8d34b85198a55e5101c
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59655749"
---
# <a name="da0011-expensive-compareto"></a>DA0011 : Fonction CompareTo coûteuse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la dernière documentation sur Visual Studio, consultez [DA0011 : CompareTo coûteux](https://docs.microsoft.com/visualstudio/profiling/da0011-expensive-compareto).  
  
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
