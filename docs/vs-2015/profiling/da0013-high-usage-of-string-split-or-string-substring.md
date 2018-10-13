---
title: 'DA0013 : Utilisation intensive de String.Split ou de String.Substring | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
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
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06e738444b2a8e3e888da406097e94fbc9e10a28
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49198690"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013 : Utilisation intensive de String.Split/String.Substring
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id de règle | DA0013 |  
| Catégorie de |. Conseils d’utilisation de NET Framework |  
| Méthodes de profilage | Échantillonnage |  
| Message | Envisagez de réduire l’utilisation des fonctions String.Split et String.Substring. |  
| Type de règle | Avertissement |  
  
## <a name="cause"></a>Cause  
 Les appels aux méthodes System.String.Split ou System.String.Substring représentent une part importante des données de profilage. Utilisez System.String.IndexOf ou System.String.IndexOfAny si vous testez l’existence d’une sous-chaîne dans une chaîne.  
  
## <a name="rule-description"></a>Description de la règle  
 La méthode Split agit sur un objet String et retourne un nouveau tableau de chaînes qui contient les sous-chaînes des chaînes d’origine. La fonction alloue de la mémoire à l’objet tableau retourné et alloue un nouvel objet String à chaque élément de tableau qu’elle trouve. De même, la méthode Substr agit sur un objet String et retourne une nouvelle chaîne qui est équivalente à la sous-chaîne demandée.  
  
 Si la gestion des allocations de mémoire est critique pour votre application, utilisez des alternatives aux méthodes String.Split et String.Substr. Par exemple, vous pouvez utiliser la méthode IndexOf ou IndexOfAny pour trouver une sous-chaîne spécifique dans une chaîne de caractères, sans créer une nouvelle instance de la classe String.  
  
## <a name="how-to-investigate-a-warning"></a>Comment rechercher la cause d’un avertissement  
 Double-cliquez sur le message dans la fenêtre Liste d’erreurs pour accéder à la [vue Informations relatives à la fonction](../profiling/function-details-view.md) des données de profilage par échantillonnage. Examinez les fonctions appelantes pour rechercher les sections du programme qui utilisent le plus fréquemment les méthodes System.String.Split ou System.String.Substr. Si possible, utilisez la méthode IndexOf ou IndexOfAny pour trouver une sous-chaîne spécifique dans une chaîne de caractères, sans créer une nouvelle instance de la classe String.



