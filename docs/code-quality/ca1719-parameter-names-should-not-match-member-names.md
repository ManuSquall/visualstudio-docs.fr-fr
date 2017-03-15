---
title: "CA1719&#160;: Les noms des param&#232;tres ne doivent pas &#234;tre identiques aux noms des membres | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ParameterNamesShouldNotMatchMemberNames"
  - "CA1719"
helpviewer_keywords: 
  - "CA1719"
  - "ParameterNamesShouldNotMatchMemberNames"
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1719&#160;: Les noms des param&#232;tres ne doivent pas &#234;tre identiques aux noms des membres
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ParameterNamesShouldNotMatchMemberNames|  
|CheckId|CA1719|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Oui|  
  
## Cause  
 Le nom d'un membre visible de l'extérieur correspond, dans une comparaison qui ne respecte pas la casse, au nom de l'un de ses paramètres.  
  
## Description de la règle  
 Un nom de paramètre doit véhiculer la signification du paramètre et un nom de membre celle du membre.  Un design où ceux\-ci sont identiques est rare.  Donner à un paramètre le même que son membre n'est pas une méthode intuitive et rend la bibliothèque difficile à utiliser.  
  
## Comment corriger les violations  
 Sélectionnez un nom de paramètre qui ne correspond pas au nom du membre.  
  
## Quand supprimer les avertissements  
 Dans le cas d'un nouveau développement, aucun scénario connu n'oblige à supprimer un avertissement de cette règle.  En cas de livraison de bibliothèques, vous pouvez être amené à supprimer un avertissement de cette règle.  
  
## Règles connexes  
 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708 : Les identificateurs ne doivent pas différer que par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)