---
title: "DA0013 : Utilisation intensive de String.Split ou de String.Substring | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1101457388b5ba54752f47014c9c389fcb2cb073
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013 : Utilisation intensive de String.Split ou de String.Substring
|||  
|-|-|  
|ID de règle|DA0013|  
|Catégorie|Conseils d’utilisation du .NET Framework|  
|Méthodes de profilage|Échantillonnage|  
|Message|Limitez l'utilisation des fonctions String.Split et String.Substring.|  
|Type de règle|Warning|  
  
## <a name="cause"></a>Cause  
 Les appels aux méthodes System.String.Split ou System.String.Substring représentent une part importante des données de profilage. Utilisez System.String.IndexOf ou System.String.IndexOfAny si vous testez l’existence d’une sous-chaîne dans une chaîne.  
  
## <a name="rule-description"></a>Description de la règle  
 La méthode Split agit sur un objet String et retourne un nouveau tableau de chaînes qui contient les sous-chaînes des chaînes d’origine. La fonction alloue de la mémoire à l’objet tableau retourné et alloue un nouvel objet String à chaque élément de tableau qu’elle trouve. De même, la méthode Substr agit sur un objet String et retourne une nouvelle chaîne qui est équivalente à la sous-chaîne demandée.  
  
 Si la gestion des allocations de mémoire est critique pour votre application, utilisez des alternatives aux méthodes String.Split et String.Substr. Par exemple, vous pouvez utiliser la méthode IndexOf ou IndexOfAny pour trouver une sous-chaîne spécifique dans une chaîne de caractères, sans créer une nouvelle instance de la classe String.  
  
## <a name="how-to-investigate-a-warning"></a>Comment rechercher la cause d’un avertissement  
 Double-cliquez sur le message dans la fenêtre Liste d’erreurs pour accéder à la [vue Informations relatives à la fonction](../profiling/function-details-view.md) des données de profilage par échantillonnage. Examinez les fonctions appelantes pour rechercher les sections du programme qui utilisent le plus fréquemment les méthodes System.String.Split ou System.String.Substr. Si possible, utilisez la méthode IndexOf ou IndexOfAny pour trouver une sous-chaîne spécifique dans une chaîne de caractères, sans créer une nouvelle instance de la classe String.