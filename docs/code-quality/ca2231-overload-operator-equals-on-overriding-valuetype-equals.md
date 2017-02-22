---
title: "CA2231&#160;: Surchargez l&#39;op&#233;rateur &#233;gal (equals) en rempla&#231;ant ValueType.Equals | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OverloadOperatorEqualsOnOverridingValueTypeEquals"
  - "CA2231"
  - "OverrideOperatorEqualsOnOverridingValueTypeEquals"
helpviewer_keywords: 
  - "CA2231"
  - "OverloadOperatorEqualsOnOverridingValueTypeEquals"
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2231&#160;: Surchargez l&#39;op&#233;rateur &#233;gal (equals) en rempla&#231;ant ValueType.Equals
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|  
|CheckId|CA2231|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type valeur se substitue à <xref:System.Object.Equals%2A?displayProperty=fullName> mais n'implémente pas l'opérateur d'égalité.  
  
## Description de la règle  
 La plupart des langages de programmation n'ont aucune implémentation par défaut de l'opérateur d'égalité \(\=\=\) pour les types valeur.  Si votre langage de programmation prend en charge des surcharges d'opérateur, vous devez envisager d'implémenter l'opérateur d'égalité.  Son comportement doit être identique à celui de <xref:System.Object.Equals%2A>.  
  
 Vous ne pouvez pas utiliser l'opérateur d'égalité par défaut dans une implémentation surchargée de l'opérateur d'égalité.  Ce procédé provoque un dépassement de capacité de la pile.  Pour implémenter l'opérateur d'égalité, utilisez la méthode Object.Equals dans votre implémentation.  Par exemple :  
  
```vb  
If (Object.ReferenceEquals(left, Nothing)) Then  
    Return Object.ReferenceEquals(right, Nothing)  
Else  
    Return left.Equals(right)  
End If  
```  
  
```c#  
if (Object.ReferenceEquals(left, null))   
    return Object.ReferenceEquals(right, null);  
return left.Equals(right);  
```  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, implémentez l'opérateur d'égalité.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle ; toutefois, nous vous recommandons, si possible, de fournir l'opérateur d'égalité.  
  
## Exemple  
 L'exemple suivant définit un type qui enfreint cette règle.  
  
 [!CODE [FxCop.Usage.EqualsGetHashCode#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.EqualsGetHashCode#1)]  
  
## Règles connexes  
 [CA1046 : Ne pas surcharger l'opérateur égal à sur les types référence](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225 : Les surcharges d'opérateur offrent d'autres méthodes nommées](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2226 : Les opérateurs doivent contenir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224 : Remplacez Equals au moment de surcharger l'opérateur égal](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218 : Remplacez GetHashCode au moment de remplacer Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
## Voir aussi  
 <xref:System.Object.Equals%2A?displayProperty=fullName>