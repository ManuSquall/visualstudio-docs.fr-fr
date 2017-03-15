---
title: "CA1715 : Les identificateurs doivent &#234;tre dot&#233;s d&#39;un pr&#233;fixe correct | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1715"
  - "IdentifiersShouldHaveCorrectPrefix"
helpviewer_keywords: 
  - "IdentifiersShouldHaveCorrectPrefix"
  - "CA1715"
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 30
---
# CA1715 : Les identificateurs doivent &#234;tre dot&#233;s d&#39;un pr&#233;fixe correct
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldHaveCorrectPrefix|  
|CheckId|CA1715|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Avec rupture \- lorsque déclenchée sur des interfaces.<br /><br /> Sans rupture \- lorsque déclenchée sur des paramètres de type générique.|  
  
## Cause  
 Le nom d'une interface visible à l'extérieur ne commence pas par un "I" majuscule.  
  
 ou  
  
 Le nom d'un paramètre de type générique sur un type ou une méthode extérieurement visible ne commence pas par un 'T' majuscule.  
  
## Description de la règle  
 Par convention, les noms de certains éléments de programmation commencent par un préfixe spécifique.  
  
 Les noms d'interfaces doivent commencer par un "I" majuscule suivi d'une autre lettre majuscule.  Cette règle rapporte des violations pour les noms d'interfaces tels que 'MyInterface' et 'IsolatedInterface'.  
  
 Les noms de paramètre de type générique doivent commencer par un 'T' majuscule, suivi éventuellement d'une autre lettre majuscule.  Cette règle rapporte les violations pour les noms de paramètres de type générique, tels que ''V' et 'Type'.  
  
 Les conventions d'affectation des noms confèrent un aspect commun aux bibliothèques qui ciblent le Common Language Runtime.  Elles réduisent ainsi la durée de l'apprentissage requis par les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.  
  
## Comment corriger les violations  
 Renommez l'identificateur de sorte que son préfixe soit correct.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 **L'exemple suivant présente une interface incorrectement nommée.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]  
  
## Exemple  
 **L'exemple suivant résout la violation précédente en faisant précéder le nom de l'interface par un 'I'.**  
  
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]  
  
## Exemple  
 **L'exemple suivant présente un paramètre de type générique incorrectement nommé.**  
  
 [!CODE [FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1)]  
  
## Exemple  
 **L'exemple suivant résout la violation précédente en faisant précéder le paramètre de type générique par un 'T'.**  
  
 [!CODE [FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1)]  
  
## Règles connexes  
 [CA1722 : Les identificateurs ne doivent pas porter un préfixe incorrect](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)