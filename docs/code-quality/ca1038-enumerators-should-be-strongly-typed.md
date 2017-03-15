---
title: "CA1038&#160;: Les &#233;num&#233;rateurs doivent &#234;tre fortement typ&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EnumeratorsShouldBeStronglyTyped"
  - "CA1038"
helpviewer_keywords: 
  - "CA1038"
  - "EnumeratorsShouldBeStronglyTyped"
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1038&#160;: Les &#233;num&#233;rateurs doivent &#234;tre fortement typ&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumeratorsShouldBeStronglyTyped|  
|CheckId|CA1038|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type public ou protégé implémente <xref:System.Collections.IEnumerator?displayProperty=fullName> mais ne fournit pas de version fortement typée de la propriété <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName>.  Les types dérivés des types suivants ne sont pas soumis à cette règle :  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
## Description de la règle  
 Cette règle requiert que les implémentations <xref:System.Collections.IEnumerator> fournissent également une version fortement typée de la propriété <xref:System.Collections.IEnumerator.Current%2A> afin que les utilisateurs ne soient pas tenus d'effectuer un cast de la valeur de retour en type fort lorsqu'ils utilisent les fonctionnalités fournies par l'interface.  Cette règle considère que le type qui implémente <xref:System.Collections.IEnumerator> contient une collection d'instances d'un type plus fort que <xref:System.Object>.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, implémentez la propriété d'interface explicitement \(déclarez\-la en tant que `IEnumerator.Current`\).  Ajoutez une version publique fortement typée de la propriété, déclarée en tant que `Current`, et faites en sorte qu'elle retourne un objet fortement typé.  
  
## Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle lors de l'implémentation d'un énumérateur fondé sur des objets à utiliser avec une collection fondée sur des objets, notamment un arbre binaire.  Les types qui étendent la nouvelle collection définissent l'énumérateur fortement typé et exposent la propriété fortement typée.  
  
## Exemple  
 L'exemple suivant montre la manière correcte d'implémenter un type <xref:System.Collections.IEnumerator> fortement typé.  
  
 [!CODE [FxCop.Design.IEnumeratorStrongTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes#1)]  
  
## Règles connexes  
 [CA1035 : Les implémentations ICollection possèdent des membres fortement typés](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1039 : Les listes sont fortement typées](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## Voir aussi  
 <xref:System.Collections.IEnumerator?displayProperty=fullName>   
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>