---
title: 'DA0010 : Fonction GetHashCode coûteuse | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 111e3204224f1124476ab2a324df7be2b6ef2525
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58354828"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010 : GetHashCode coûteux
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la dernière documentation sur Visual Studio, consultez [DA0010 : GetHashCode coûteux](https://docs.microsoft.com/visualstudio/profiling/da0010-expensive-gethashcode) sur docs.microsoft.com.  

  

|||  
|-|-|  
|ID de règle|DA0010|  
|Category|Utilisation du .NET Framework|  
|Méthodes de profilage|Échantillonnage<br /><br /> Mémoire .NET|  
|Message|Les fonctions GetHashCode doivent être peu coûteuses et n’allouer aucune mémoire. Réduisez si possible la complexité de la fonction de code de hachage.|  
|Type de message|Warning|  
  
## <a name="cause"></a>Cause  
 Les appels à la méthode GetHashCode du type représentent une part importante des données de profilage, ou la méthode alloue de la mémoire.  
  
## <a name="rule-description"></a>Description de la règle  
 Le hachage est une technique pour localiser rapidement un élément particulier dans une collection de grande taille. Comme les tables de hachage peuvent être très grandes et avoir à supporter des accès à des débits très élevés, elles doivent être extrêmement efficaces. Une conséquence de cette nécessité est que les méthodes GetHashCode dans le .NET Framework ne doivent pas allouer de mémoire. L’allocation de mémoire augmente la charge sur le récupérateur de mémoire et expose la méthode à des délais potentiels s’il devient nécessaire d’exécuter la garbage collection suite à la demande d’allocation.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Simplifiez la méthode.
