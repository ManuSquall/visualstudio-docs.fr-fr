---
title: "DA0013&#160;: Utilisation intensive de String.Split/String.Substring | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.13"
  - "vs.performance.rules.DAAvoidStringSubstr"
  - "vs.performance.DA0013"
  - "vs.performance.rules.DA0013"
helpviewer_keywords: 
  - "vs.performance.13"
  - "vs.performance.rules.DA0013"
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0013&#160;: Utilisation intensive de String.Split/String.Substring
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0013|  
|Catégorie|Recommandation pour l'utilisation du .NET Framework|  
|Méthodes de profilage|Échantillonnage|  
|Message|Limitez l'utilisation des fonctions String.Split et String.Substring.|  
|Type de règle|Avertissement|  
  
## Cause  
 Les appels aux méthodes System.String.Split ou System.String.Substring représentent une partie significative des données de profilage.  Utilisez System.String.IndexOf ou System.String.IndexOfAny si vous testez l'existence d'une sous\-chaîne dans une chaîne.  
  
## Description de la règle  
 La méthode Split fonctionne sur un objet String et retourne un nouveau tableau de chaînes qui contient les sous\-chaînes de l'original.  La fonction alloue la mémoire pour l'objet tableau retourné et alloue un nouvel objet String pour chaque élément de tableau trouvé.  De la même façon, la méthode Substr fonctionne sur un objet String et retourne une nouvelle chaîne qui est équivalente à la sous\-chaîne demandée.  
  
 Si la gestion des allocations de mémoire est critique dans votre application, envisagez d'utiliser des alternatives aux méthodes String.Split et String.Substr.  Par exemple, vous pouvez utiliser la méthode IndexOf ou IndexOfAny pour trouver une sous\-chaîne spécifique dans une Chaîne de caractères sans créer une nouvelle instance de la classe String.  
  
## Comment examiner un avertissement  
 Double\-cliquez sur le message dans la fenêtre Liste d'erreurs pour naviguer jusqu'à la [Vue Informations relatives à la fonction](../profiling/function-details-view.md) des données de profil d'échantillonnage.  Examinez les fonctions d'appel pour rechercher les sections du programme qui utilisent le plus les méthodes System.String.Split ou System.String.Substr.  Si c'est possible, utilisez la méthode IndexOf ou IndexOfAny pour trouver une sous\-chaîne spécifique dans une Chaîne de caractères sans créer une nouvelle instance de la classe String.