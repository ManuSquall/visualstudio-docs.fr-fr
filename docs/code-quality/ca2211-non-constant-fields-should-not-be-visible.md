---
title: "CA2211&#160;: Les champs non constants ne doivent pas &#234;tre visibles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2211"
  - "NonConstantFieldsShouldNotBeVisible"
helpviewer_keywords: 
  - "CA2211"
  - "NonConstantFieldsShouldNotBeVisible"
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2211&#160;: Les champs non constants ne doivent pas &#234;tre visibles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NonConstantFieldsShouldNotBeVisible|  
|CheckId|CA2211|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un champ statique public ou protégé n'est ni constant ni en lecture seule.  
  
## Description de la règle  
 Les champs statiques qui ne sont ni constants ni en lecture seule ne sont pas thread\-safe.  L'accès à un tel champ doit être scrupuleusement contrôlé et requiert des techniques de programmation évoluées pour synchroniser l'accès à l'objet de classe.  Sachant que ces compétences sont difficiles à apprendre et à maîtriser, et que le test d'un tel objet pose ses propres difficultés, les champs statiques trouvent leur meilleure utilisation dans le stockage de données qui ne changent pas.  Cette règle s'applique aux bibliothèques ; les applications ne doivent exposer aucun champ.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, rendez le champ statique constant ou en lecture seule.  Si ce n'est pas possible, refondez le design du type pour utiliser un mécanisme de substitution tel qu'une propriété thread\-safe qui gère l'accès thread\-safe au champ sous\-jacent.  Vous devez comprendre que des problèmes tels que le conflit de verrous et les interblocages peuvent affecter les performances et le comportement de la bibliothèque.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si vous développez une application, et par conséquent, disposez d'un contrôle total sur l'accès au type qui contient le champ statique.  Les concepteurs de bibliothèque ne doivent supprimer aucun avertissement de cette règle ; l'utilisation de champs statiques non constants peut rendre une utilisation correcte de la bibliothèque difficile pour les développeurs.  
  
## Exemple  
 L'exemple suivant affiche un type qui ne respecte pas cette règle.  
  
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-cs[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]