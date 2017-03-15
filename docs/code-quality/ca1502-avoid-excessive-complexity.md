---
title: "CA1502&#160;: &#201;viter l&#39;exc&#232;s de complexit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidExcessiveComplexity"
  - "CA1502"
helpviewer_keywords: 
  - "CA1502"
  - "AvoidExcessiveComplexity"
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 30
---
# CA1502&#160;: &#201;viter l&#39;exc&#232;s de complexit&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveComplexity|  
|CheckId|CA1502|  
|Catégorie|Microsoft.Maintainability|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une méthode affiche une complexité cyclomatic excessive.  
  
## Description de la règle  
 La *complexité cyclomatic* mesure le nombre de chemins linéairement indépendants à travers la méthode, déterminé par le nombre et la complexité des branches conditionnelles.  Une complexité cyclomatic basse indique généralement une méthode facile de comprendre, à tester et à gérer.  La complexité cyclomatic est calculée à partir d'un graphique de flux de contrôle de la méthode et est fournie comme suit :  
  
 complexité cyclomatic \= nombre de bords \- nombre de nœuds \+ 1  
  
 où un nœud représente un point de branche logique et un bord une ligne entre des nœuds.  
  
 La règle signale une violation quand la complexité cyclomatic est supérieure à 25.  
  
 Vous pouvez en apprendre plus sur les métriques du code grâce à [Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md),  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, refactorisez la méthode pour diminuer sa complexité cyclomatic.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si la complexité est difficile à réduire et si la méthode est facile à comprendre, à tester et à gérer.  En particulier, une méthode qui contient une instruction `switch` \(`Select` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) de grande envergure est candidate à l'exclusion.  Le risque de déstabiliser la base de code à un point avancé du cycle de développement ou d'introduire un changement inattendu dans le comportement au moment de l'exécution d'un code précédemment expédié peut compenser les avantages conférés en termes de facilité de maintenance par la refactorisation du code.  
  
## Mode de calcul de la complexité cyclomatic  
 La complexité cyclomatic est calculée en ajoutant 1 aux éléments suivants :  
  
-   Nombre de branches \(par exemple `if`, `while` et `do`\)  
  
-   Nombre d'instructions `case` dans une instruction `switch`  
  
 Les exemples suivants affichent des méthodes avec diverses complexités cyclomatic.  
  
## Exemple  
 **Complexité cyclomatic 1**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]  
  
## Exemple  
 **Complexité cyclomatic 2**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]  
  
## Exemple  
 **Complexité cyclomatic 3**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]  
  
## Exemple  
 **Complexité cyclomatic 8**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]  
  
## Règles connexes  
 [CA1501 : Éviter l'excès d'héritage](../code-quality/ca1501-avoid-excessive-inheritance.md)  
  
## Voir aussi  
 [Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)