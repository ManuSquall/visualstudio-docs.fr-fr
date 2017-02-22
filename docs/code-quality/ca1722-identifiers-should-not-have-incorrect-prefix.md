---
title: "CA1722&#160;: Les identificateurs ne doivent pas porter un pr&#233;fixe incorrect | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldNotHaveIncorrectPrefix"
  - "CA1722"
helpviewer_keywords: 
  - "CA1722"
  - "IdentifiersShouldNotHaveIncorrectPrefix"
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1722&#160;: Les identificateurs ne doivent pas porter un pr&#233;fixe incorrect
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|  
|CheckId|CA1722|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Oui|  
  
## Cause  
 Le préfixe d'un identificateur est inexact.  
  
## Description de la règle  
 Par convention, seuls certains éléments de programmation présentent des noms qui commencent par un préfixe spécifique.  
  
 Les noms de types n'ont pas de préfixe spécifique et ne doivent pas avoir un 'C' pour préfixe.  Cette règle rapporte des violations pour les noms de types tels que 'CMyClass', et n'en rapporte pas pour les noms de types tels que 'Cache'.  
  
 Les conventions d'affectation des noms confèrent un aspect commun aux bibliothèques qui ciblent le Common Language Runtime.  Elles réduisent ainsi la durée de l'apprentissage requis par les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.  
  
## Comment corriger les violations  
 Supprimez le préfixe de l'identificateur.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Règles connexes  
 [CA1715 : Les identificateurs doivent être dotés d'un préfixe correct](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)