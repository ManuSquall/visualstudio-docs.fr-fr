---
title: "CA1046&#160;: Ne pas surcharger l&#39;op&#233;rateur &#233;gal &#224; sur les types r&#233;f&#233;rence | Microsoft Docs"
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
  - "DoNotOverloadOperatorEqualsOnReferenceTypes"
  - "CA1046"
helpviewer_keywords: 
  - "CA1046"
  - "DoNotOverloadOperatorEqualsOnReferenceTypes"
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1046&#160;: Ne pas surcharger l&#39;op&#233;rateur &#233;gal &#224; sur les types r&#233;f&#233;rence
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|  
|CheckId|CA1046|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type référence public ou public imbriqué surcharge l'opérateur d'égalité.  
  
## Description de la règle  
 Pour les types référence, l'implémentation par défaut de l'opérateur d'égalité est presque toujours correcte.  Par défaut, deux références sont égales uniquement si elles pointent sur le même objet.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez l'implémentation de l'opérateur d'égalité.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle quand le type référence se comporte comme un type valeur intégré.  Si appliquer des additions ou des soustractions à des instances du type est pertinent, il est probablement correct d'implémenter l'opérateur d'égalité et de supprimer la violation.  
  
## Exemple  
 L'exemple suivant montre le comportement par défaut lors de la comparaison de deux références.  
  
 [!code-cs[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]  
  
## Exemple  
 L'application suivante compare des références.  
  
 [!code-cs[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]  
  
 Cet exemple génère la sortie suivante.  
  
  **a \= nouveau \(2,2\) et b \= nouveau \(2,2\) sont égaux ?**  
 **Aucun c et a ne sont égaux ?**  
 **Oui b et a sont \=\= ?**  
 **Aucun c et a ne sont \=\= ?**  
 **Oui**   
## Règles connexes  
 [CA1013 : Surchargez l'opérateur égal lors de la surcharge de l'opérateur d'addition et de soustraction](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## Voir aussi  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Opérateurs d'égalité](../Topic/Equality%20Operators.md)