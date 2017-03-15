---
title: "CA1724&#160;: les noms de types ne doivent pas &#234;tre identiques aux espaces de noms | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
helpviewer_keywords: 
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1724&#160;: les noms de types ne doivent pas &#234;tre identiques aux espaces de noms
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypeNamesShouldNotMatchNamespaces|  
|CheckId|CA1724|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un nom de type correspond à un nom d'espace de noms [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] dans une comparaison qui ne respecte pas la casse.  
  
## Description de la règle  
 Les noms de types ne doivent pas correspondre aux noms d'espaces de noms définis dans la bibliothèque de classes [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Enfreindre cette règle peut réduire la facilité d'utilisation de la bibliothèque.  
  
## Comment corriger les violations  
 Sélectionnez un nom de type qui ne correspond pas au nom d'un espace de noms de la bibliothèque de classes du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Quand supprimer les avertissements  
 Dans le cas d'un nouveau développement, aucun scénario connu n'oblige à supprimer un avertissement de cette règle.  Avant de pouvoir supprimer l'avertissement, prenez bien en compte la façon dont les utilisateurs de votre bibliothèque pourraient confondre le nom correspondant.  En cas de livraison de bibliothèques, vous pouvez être amené à supprimer un avertissement de cette règle.