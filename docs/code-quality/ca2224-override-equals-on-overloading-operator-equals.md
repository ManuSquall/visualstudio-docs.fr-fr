---
title: "CA2224&#160;: Remplacez Equals au moment de surcharger l&#39;op&#233;rateur &#233;gal | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2224"
  - "OverrideEqualsOnOverloadingOperatorEquals"
  - "OverrideEqualsOnOverridingOperatorEquals"
helpviewer_keywords: 
  - "CA2224"
  - "OverrideEqualsOnOverloadingOperatorEquals"
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA2224&#160;: Remplacez Equals au moment de surcharger l&#39;op&#233;rateur &#233;gal
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|  
|CheckId|CA2224|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type public implémente l'opérateur d'égalité, mais ne se substitue pas à <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
## Description de la règle  
 L'opérateur d'égalité est destiné à fournir un accès syntaxique pratique aux fonctionnalités de la méthode <xref:System.Object.Equals%2A>.  Si vous implémentez l'opérateur d'égalité, sa logique doit être identique à celle de <xref:System.Object.Equals%2A>.  
  
 Le compilateur C\# émet un avertissement si votre code enfreint cette règle.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, vous devez supprimer l'implémentation de l'opérateur d'égalité ou substituer <xref:System.Object.Equals%2A> et faire en sorte que les deux méthodes retournent les mêmes valeurs.  Si l'opérateur d'égalité n'introduit aucun comportement incohérent, vous pouvez corriger la violation en fournissant une implémentation de <xref:System.Object.Equals%2A> qui appelle la méthode <xref:System.Object.Equals%2A> dans la classe de base.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si l'opérateur d'égalité retourne la même valeur que l'implémentation héritée de <xref:System.Object.Equals%2A>.  La section Exemple inclut un type qui pourrait supprimer sans risque un avertissement de cette règle.  
  
## Exemples de définitions d'égalité incohérentes  
  
### Description  
 L'exemple suivant montre un type avec des définitions d'égalité incohérentes.  `BadPoint` modifie la signification d'égalité en fournissant une implémentation personnalisée de l'opérateur d'égalité, mais ne substitue pas <xref:System.Object.Equals%2A> afin qu'il se comporte de la même manière.  
  
### Code  
 [!code-cs[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]  
  
## Exemple  
 Le code suivant teste le comportement de `BadPoint`.  
  
 [!code-cs[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]  
  
 Cet exemple génère la sortie suivante.  
  
  **a \= \(\[0\] 1,1\) et b \= \(\[1\] 2,2\) sont\-ils égaux ?**  
 **Aucun a \=\= b ?**  
 **Aucun a1 et a sont égaux ?**  
 **Oui a1 \=\= a ?**  
 **Oui b et bcopy sont égaux ?**  
 **Aucun b \=\= bcopy ?**  
 **Oui**   
## Exemple  
 L'exemple suivant présente un type qui techniquement viole cette règle, mais ne se comporte pas de façon incohérente.  
  
 [!code-cs[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]  
  
## Exemple  
 Le code suivant teste le comportement de `GoodPoint`.  
  
 [!code-cs[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]  
  
 Cet exemple génère la sortie suivante.  
  
  **a \= \(1,1\) et b \= \(2,2\) sont\-ils égaux ?**  
 **Non a \=\= b ?**  
 **Non a1 et a sont\-ils égaux ?**  
 **Oui a1 \=\= a ?**  
 **Oui b et bcop sont\-ils égaux ?**  
 **Oui b \=\= bcopy ?**  
 **Oui**   
## Exemple de classe  
  
### Description  
 L'exemple suivant indique une classe \(type référence\) qui enfreint cette règle.  
  
### Code  
 [!code-cs[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]  
  
## Exemple  
 L'exemple suivant résout la violation en substituant <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
 [!code-cs[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]  
  
## Exemple de structure  
  
### Description  
 L'exemple suivant indique une structure \(type valeur\) qui enfreint cette règle.  
  
### Code  
 [!code-cs[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]  
  
## Exemple  
 L'exemple suivant résout la violation en substituant <xref:System.ValueType.Equals%2A?displayProperty=fullName>.  
  
 [!code-cs[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]  
  
## Règles connexes  
 [CA1046 : Ne pas surcharger l'opérateur égal à sur les types référence](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225 : Les surcharges d'opérateur offrent d'autres méthodes nommées](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2226 : Les opérateurs doivent contenir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2218 : Remplacez GetHashCode au moment de remplacer Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231 : Surchargez l'opérateur égal \(equals\) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)