---
title: 'DA0011 : Fonction CompareTo coûteuse'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4f6137c07ac6b920234a9772764b5ad758efdb1e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818846"
---
# <a name="da0011-expensive-compareto"></a>DA0011 : CompareTo coûteux

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