---
title: "CA1819&#160;: Les propri&#233;t&#233;s ne doivent pas retourner des tableaux | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PropertiesShouldNotReturnArrays"
  - "CA1819"
helpviewer_keywords: 
  - "PropertiesShouldNotReturnArrays"
  - "CA1819"
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 22
---
# CA1819&#160;: Les propri&#233;t&#233;s ne doivent pas retourner des tableaux
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertiesShouldNotReturnArrays|  
|CheckId|CA1819|  
|Catégorie|Microsoft.Performance|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une propriété publique ou protégée dans un type public retourne un tableau.  
  
## Description de la règle  
 Les tableaux retournés par les propriétés ne sont pas protégés en écriture, même si la propriété est en lecture seule.  Pour protéger le tableau de toute falsification, la propriété doit retourner une copie du tableau.  En général, les utilisateurs ne comprennent l'incidence négative en matière de performances de l'appel à une telle propriété.  Spécifiquement, ils peuvent utiliser la propriété en tant que propriété indexée.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez la propriété en une méthode ou modifiez\-la de sorte qu'elle retourne une collection.  
  
## Quand supprimer les avertissements  
 Les attributs peuvent contenir des propriétés qui retournent des tableaux, mais ne peuvent pas contenir des propriétés qui retournent des collections.  Vous pouvez supprimer un avertissement déclenché pour une propriété d'un attribut qui est dérivé de la classe [System.Attribute](assetId:///System.Attribute?qualifyHint=False&autoUpgrade=True).  Sinon, ne supprimez aucun avertissement de cette règle.  
  
## Exemple de violation  
  
### Description  
 L'exemple suivant présente un type qui enfreint cette règle.  
  
### Code  
 [!code-cs[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]  
  
### Commentaires  
 Pour corriger une violation de cette règle, modifiez la propriété en une méthode ou modifiez\-la de sorte qu'elle retourne une collection plutôt qu'un tableau.  
  
## Modifier la propriété en un exemple de méthode  
  
### Description  
 L'exemple suivant résout la violation en modifiant la propriété en une méthode.  
  
### Code  
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-cs[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]  
  
## Retourner un exemple de collection  
  
### Description  
 L'exemple suivant résout la violation en modifiant la propriété de sorte qu'elle retourne une  
  
 <xref:System.Collection.ObjectModel.ReadOnlyCollection?displayProperty=fullName>.  
  
### Code  
 [!code-cs[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]  
  
## Autoriser les utilisateurs à modifier une propriété  
  
### Description  
 Vous pouvez permettre au consommateur de la classe de modifier une propriété.  L'exemple suivant présente une propriété en lecture\/écriture qui enfreint cette règle.  
  
### Code  
 [!code-cs[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]  
  
### Commentaires  
 L'exemple suivant résout la violation en modifiant la propriété de sorte qu'elle retourne une <xref:System.Collection.ObjectModel.Collection?displayProperty=fullName>.  
  
### Code  
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-cs[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]  
  
## Règles connexes  
 [CA1024 : Utiliser les propriétés lorsque cela est approprié](../code-quality/ca1024-use-properties-where-appropriate.md)