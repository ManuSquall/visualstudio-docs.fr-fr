---
title: "CA1013&#160;: Surchargez l&#39;op&#233;rateur &#233;gal lors de la surcharge de l&#39;op&#233;rateur d&#39;addition et de soustraction | Microsoft Docs"
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
  - "OverrideOperatorEqualsOnOverridingAddAndSubtract"
  - "OverrideOperatorEqualsOnOverloadingAddAndSubtract"
  - "CA1013"
  - "OverloadOperatorEqualsOnOverloadingAddAndSubtract"
helpviewer_keywords: 
  - "OverrideOperatorEqualsOnOverloadingAddAndSubtract"
  - "OverrideOperatorEqualsOnOverridingAddAndSubtract"
  - "CA1013"
  - "OverloadOperatorEqualsOnOverloadingAddAndSubtract"
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1013&#160;: Surchargez l&#39;op&#233;rateur &#233;gal lors de la surcharge de l&#39;op&#233;rateur d&#39;addition et de soustraction
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|  
|CheckId|CA1013|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type public ou protégé implémente les opérateurs d'addition ou de soustraction sans implémenter l'opérateur d'égalité.  
  
## Description de la règle  
 Lorsque des instances d'un type peuvent être combinées à l'aide d'opérations telles que l'addition et la soustraction, vous devez presque systématiquement définir l'égalité de sorte qu'elle retourne une valeur `true` pour toute paire d'instances affichant les mêmes valeurs constituantes.  
  
 Vous ne pouvez pas utiliser l'opérateur d'égalité par défaut dans une implémentation surchargée de l'opérateur d'égalité.  Ce procédé provoque un dépassement de capacité de la pile.  Pour implémenter l'opérateur d'égalité, utilisez la méthode Object.Equals dans votre implémentation.  Voir l'exemple suivant.  
  
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
 Pour corriger une violation de cette règle, implémentez l'opérateur d'égalité afin qu'il soit mathématiquement cohérent avec les opérateurs d'addition et de soustraction.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle lorsque l'implémentation par défaut de l'opérateur d'égalité fournit le comportement correct pour le type.  
  
## Exemple  
 L'exemple suivant définit un type qui enfreint cette règle \(`BadAddableType`\).  Ce type doit implémenter l'opérateur d'égalité pour que toute paire d'instances dotées des mêmes valeurs de champ teste son égalité au moyen d'une valeur `true`.  Le type `GoodAddableType` affiche l'implémentation corrigée.  Notez que ce type implémente également l'opérateur d'inégalité et se substitue à <xref:System.Object.Equals%2A> pour satisfaire d'autres règles.  Une implémentation complète implémenterait également <xref:System.Object.GetHashCode%2A>.  
  
 [!code-cs[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]  
  
## Exemple  
 L'exemple suivant teste l'égalité au moyen d'instances des types précédemment définis dans cette rubrique, pour illustrer le comportement par défaut et correct de l'opérateur d'égalité.  
  
 [!code-cs[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]  
  
 Cet exemple génère la sortie suivante.  
  
  **Type incorrect :  {2,2} {2,2} sont égaux ?  Non**  
**Good type: {3,3} {3,3} are equal?  Oui**  
**Good type: {3,3} {3,3} are \=\= ?   Oui**  
**Type incorrect :  {2,2} {9,9} sont égaux ?  Non**  
**Good type: {3,3} {9,9} are \=\= ?   Non**    
## Voir aussi  
 [Opérateurs d'égalité](../Topic/Equality%20Operators.md)