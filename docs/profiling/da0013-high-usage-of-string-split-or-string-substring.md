---
title: DA0013-utilisation intensive de String. Split ou String. Substring | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 49c403c401a3a60213519d0b01131e811f5105dd
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328091"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013 : Utilisation intensive de String.Split ou de String.Substring

|||
|-|-|
|ID de règle|DA0013|
|Category|Conseils d’utilisation du .NET Framework|
|Méthodes de profilage|échantillonnage|
|Message|Limitez l'utilisation des fonctions String.Split et String.Substring.|
|Type de règle|Avertissement|

## <a name="cause"></a>Cause
 Les appels aux méthodes System.String.Split ou System.String.Substring représentent une part importante des données de profilage. Utilisez System.String.IndexOf ou System.String.IndexOfAny si vous testez l’existence d’une sous-chaîne dans une chaîne.

## <a name="rule-description"></a>Description de la règle
 La méthode Split agit sur un objet String et retourne un nouveau tableau de chaînes qui présente les sous-chaînes des chaînes d’origine. La fonction alloue de la mémoire à l’objet tableau retourné et alloue un nouvel objet String à chaque élément de tableau qu’elle trouve. De même, la méthode Substr agit sur un objet String et retourne une nouvelle chaîne qui est équivalente à la sous-chaîne demandée.

 Si la gestion des allocations de mémoire est critique pour votre application, utilisez des alternatives aux méthodes String.Split et String.Substr. Par exemple, vous pouvez utiliser la méthode IndexOf ou IndexOfAny pour trouver une sous-chaîne spécifique dans une chaîne de caractères, sans créer une nouvelle instance de la classe String.

## <a name="how-to-investigate-a-warning"></a>Comment rechercher la cause d’un avertissement
 Double-cliquez sur le message dans la fenêtre **Liste d’erreurs** pour accéder à la vue [Informations relatives à la fonction](../profiling/function-details-view.md) des données de profilage par échantillonnage. Examinez les fonctions appelantes pour rechercher les sections du programme qui utilisent le plus fréquemment les méthodes System.String.Split ou System.String.Substr. Si possible, utilisez la méthode IndexOf ou IndexOfAny pour trouver une sous-chaîne spécifique dans une chaîne de caractères, sans créer une nouvelle instance de la classe String.
