---
title: "CA2226&#160;: Les op&#233;rateurs doivent contenir des surcharges sym&#233;triques | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OperatorsShouldHaveSymmetricalOverloads"
  - "CA2226"
helpviewer_keywords: 
  - "CA2226"
  - "OperatorsShouldHaveSymmetricalOverloads"
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2226&#160;: Les op&#233;rateurs doivent contenir des surcharges sym&#233;triques
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OperatorsShouldHaveSymmetricalOverloads|  
|CheckId|CA2226|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type implémente l'opérateur d'égalité ou d'inégalité et n'implémente pas l'opérateur opposé.  
  
## Description de la règle  
 Dans aucune circonstance l'égalité ou l'inégalité ne s'applique aux instances d'un type, et l'opérateur opposé est indéfini.  Les types implémentent en général l'opérateur d'inégalité en retournant la valeur de négation de l'opérateur d'égalité.  
  
 Le compilateur C\# émet une erreur pour les violations de cette règle.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, implémentez à la fois les opérateurs d'égalité et d'inégalité, ou supprimez celui qui est présent.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  Votre type ne fonctionnera pas de manière cohérente avec le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Règles connexes  
 [CA1046 : Ne pas surcharger l'opérateur égal à sur les types référence](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225 : Les surcharges d'opérateur offrent d'autres méthodes nommées](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2224 : Remplacez Equals au moment de surcharger l'opérateur égal](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218 : Remplacez GetHashCode au moment de remplacer Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231 : Surchargez l'opérateur égal \(equals\) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)