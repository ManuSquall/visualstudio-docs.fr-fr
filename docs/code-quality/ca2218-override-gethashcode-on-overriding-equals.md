---
title: "CA2218&#160;: Remplacez GetHashCode au moment de remplacer Equals | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2218"
  - "OverrideGetHashCodeOnOverridingEquals"
helpviewer_keywords: 
  - "CA2218"
  - "OverrideGetHashCodeOnOverridingEquals"
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2218&#160;: Remplacez GetHashCode au moment de remplacer Equals
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideGetHashCodeOnOverridingEquals|  
|CheckId|CA2218|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type public substitue <xref:System.Object.Equals%2A?displayProperty=fullName> mais ne substitue pas <xref:System.Object.GetHashCode%2A?displayProperty=fullName>.  
  
## Description de la règle  
 <xref:System.Object.GetHashCode%2A> retourne une valeur fondée sur l'instance actuelle adaptée aux algorithmes de hachage et aux structures de données telles qu'une table de hachage.  Deux objets de même type et égaux doivent retourner le même code de hachage pour garantir le bon fonctionnement des types suivants :  
  
-   <xref:System.Collections.HashTable?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Dictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortList?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.HybredDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>  
  
-   Types qui implémentent <xref:System.Collections.Generic.IEqualityComparer?displayProperty=fullName>  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, fournissez une implémentation d' <xref:System.Object.GetHashCode%2A>.  Pour une paire d'objets de même type, vous devez garantir que l'implémentation retourne la même valeur si votre implémentation de <xref:System.Object.Equals%2A> retourne `true` pour la paire.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple de classe  
  
### Description  
 L'exemple suivant indique une classe \(type référence\) qui enfreint cette règle.  
  
### Code  
 [!code-cs[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]  
  
### Commentaires  
 L'exemple suivant résout la violation en substituant <xref:System.Object.GetHashCode>.  
  
### Code  
 [!CODE [FxCop.Usage.GetHashCodeFixedClass#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedClass#1)]  
  
## Exemple de structure  
  
### Description  
 L'exemple suivant indique une structure \(type valeur\) qui enfreint cette règle.  
  
### Code  
 [!code-cs[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]  
  
### Commentaires  
 L'exemple suivant résout la violation en substituant <xref:System.Object.GetHashCode>.  
  
### Code  
 [!code-cs[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]  
  
## Règles connexes  
 [CA1046 : Ne pas surcharger l'opérateur égal à sur les types référence](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225 : Les surcharges d'opérateur offrent d'autres méthodes nommées](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2226 : Les opérateurs doivent contenir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224 : Remplacez Equals au moment de surcharger l'opérateur égal](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231 : Surchargez l'opérateur égal \(equals\) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
## Voir aussi  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>   
 <xref:System.Collections.HashTable?displayProperty=fullName>   
 [Opérateurs d'égalité](../Topic/Equality%20Operators.md)