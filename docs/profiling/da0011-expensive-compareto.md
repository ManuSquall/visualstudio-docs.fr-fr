---
title: 'DA0011 : Fonction CompareTo coûteuse | Microsoft Docs'
ms.date: 11/04/2016
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
ms.openlocfilehash: e3a1d51f66050837c05f81315f4f368749cea1b4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872432"
---
# <a name="da0011-expensive-compareto"></a>DA0011 : Fonction CompareTo coûteuse

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