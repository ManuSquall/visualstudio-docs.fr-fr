---
title: "CA1820&#160;: V&#233;rifiez la pr&#233;sence de cha&#238;nes vides par la longueur de cha&#238;ne | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TestForEmptyStringsUsingStringLength"
  - "CA1820"
helpviewer_keywords: 
  - "TestForEmptyStringsUsingStringLength"
  - "CA1820"
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1820&#160;: V&#233;rifiez la pr&#233;sence de cha&#238;nes vides par la longueur de cha&#238;ne
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TestForEmptyStringsUsingStringLength|  
|CheckId|CA1820|  
|Catégorie|Microsoft.Performance|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une chaîne est comparée à la chaîne vide à l'aide de <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
## Description de la règle  
 Comparer des chaînes au moyen de la propriété <xref:System.String.Length%2A?displayProperty=fullName> ou de la méthode <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> est considérablement plus rapide qu'au moyen de <xref:System.Object.Equals%2A>.  En effet, <xref:System.Object.Equals%2A> exécute un nombre d'instructions MSIL très supérieur à <xref:System.String.IsNullOrEmpty%2A> ou au nombre d'instructions exécutées pour récupérer la valeur de propriété <xref:System.String.Length%2A> et pour la comparer à zéro.  
  
 Vous devez comprendre que <xref:System.Object.Equals%2A> et <xref:System.String.Length%2A> \=\= 0 se comportent différemment pour les chaînes null.  Si vous essayez d'obtenir la valeur de la propriété <xref:System.String.Length%2A> sur une chaîne null, le Common Language Runtime lève un <xref:System.NullReferenceException?displayProperty=fullName>.  Si vous effectuez une comparaison entre une chaîne null et la chaîne vide, le Common Language Runtime ne lève aucune exception ; la comparaison retourne la valeur `false`.  Tester les valeurs null n'affecte pas considérablement les performances relatives de ces deux approches.  Lorsque le [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] est ciblé, utilisez la méthode <xref:System.String.IsNullOrEmpty%2A>.  Sinon, utilisez la comparaison <xref:System.String.Length%2A> \=\= dès que possible.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez la comparaison pour utiliser la propriété <xref:System.String.Length%2A> et tester la chaîne null.  Si le [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] est ciblé, utilisez la méthode <xref:System.String.IsNullOrEmpty%2A>.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si les performances ne constituent pas un problème.  
  
## Exemple  
 L'exemple suivant illustre les différentes techniques utilisées pour rechercher une chaîne vide.  
  
 [!CODE [FxCop.Performance.StringTest#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest#1)]