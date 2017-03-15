---
title: "CA1023&#160;: Les indexeurs ne doivent pas &#234;tre multidimensionnels | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IndexersShouldNotBeMultidimensional"
  - "CA1023"
helpviewer_keywords: 
  - "CA1023"
  - "IndexersShouldNotBeMultidimensional"
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1023&#160;: Les indexeurs ne doivent pas &#234;tre multidimensionnels
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IndexersShouldNotBeMultidimensional|  
|CheckId|CA1023|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type public ou protégé contient un indexeur public ou protégé qui utilise plusieurs index.  
  
## Description de la règle  
 Les indexeurs, c'est\-à\-dire les propriétés indexées, doivent utiliser un index unique.  Les indexeurs multidimensionnels peuvent considérablement diminuer la facilité d'utilisation de la bibliothèque.  Si le design nécessite plusieurs index, reconsidérez le fait que le type représente ou non un magasin de données logique.  Si ce n'est pas le cas, utilisez une méthode.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez le design pour utiliser un entier solitaire ou un index de chaîne, ou utilisez une méthode en lieu et place de l'indexeur.  
  
## Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle uniquement après avoir soigneusement envisagé la nécessité de l'indexeur non standard.  
  
## Exemple  
 L'exemple suivant présente un type, `DayOfWeek03`, doté d'un indexeur multidimensionnel qui viole la règle.  L'indexeur peut être envisagé comme un type de conversion et, par conséquent, se révèle exposé de manière plus adaptée en tant que méthode.  La conception du type est refondue en `RedesignedDayOfWeek03` pour satisfaire la règle.  
  
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-cs[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]  
  
## Règles connexes  
 [CA1043 : Utiliser un argument de chaîne ou intégral pour les indexeurs](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)  
  
 [CA1024 : Utiliser les propriétés lorsque cela est approprié](../code-quality/ca1024-use-properties-where-appropriate.md)