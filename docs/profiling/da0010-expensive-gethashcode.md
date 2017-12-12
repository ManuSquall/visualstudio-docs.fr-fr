---
title: "DA0010 : Fonction GetHashCode coûteuse | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9209d5f02d543cba3dd0dcec8f5492e2f64b9cef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="da0010-expensive-gethashcode"></a>DA0010 : GetHashCode coûteux
|||  
|-|-|  
|ID de règle|DA0010|  
|Catégorie|Utilisation du .NET Framework|  
|Méthodes de profilage|Échantillonnage<br /><br /> Mémoire .NET|  
|Message|Les fonctions GetHashCode doivent être peu coûteuses et n’allouer aucune mémoire. Réduisez si possible la complexité de la fonction de code de hachage.|  
|Type de message|Warning|  
  
## <a name="cause"></a>Cause  
 Les appels à la méthode GetHashCode du type représentent une part importante des données de profilage, ou la méthode alloue de la mémoire.  
  
## <a name="rule-description"></a>Description de la règle  
 Le hachage est une technique pour localiser rapidement un élément particulier dans une collection de grande taille. Comme les tables de hachage peuvent être très grandes et avoir à supporter des accès à des débits très élevés, elles doivent être extrêmement efficaces. Une conséquence de cette nécessité est que les méthodes GetHashCode dans le .NET Framework ne doivent pas allouer de mémoire. L’allocation de mémoire augmente la charge sur le récupérateur de mémoire et expose la méthode à des délais potentiels s’il devient nécessaire d’exécuter la garbage collection suite à la demande d’allocation.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Simplifiez la méthode.