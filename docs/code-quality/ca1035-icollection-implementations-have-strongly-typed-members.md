---
title: "CA1035&#160;: Les impl&#233;mentations ICollection poss&#232;dent des membres fortement typ&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICollectionImplementationsHaveStronglyTypedMembers"
  - "CA1035"
helpviewer_keywords: 
  - "CA1035"
  - "ICollectionImplementationsHaveStronglyTypedMembers"
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1035&#160;: Les impl&#233;mentations ICollection poss&#232;dent des membres fortement typ&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|  
|CheckId|CA1035|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type public ou protégé implémente <xref:System.Collections.ICollection?displayProperty=fullName> mais ne fournit pas de méthode fortement typée pour <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>.  La version fortement typée de <xref:System.Collections.ICollection.CopyTo%2A> doit accepter deux paramètres et ne peut pas avoir un <xref:System.Array?displayProperty=fullName> ou un tableau de <xref:System.Object?displayProperty=fullName> en tant que premier paramètre.  
  
## Description de la règle  
 Cette règle requiert que les implémentations <xref:System.Collections.ICollection> fournissent des membres fortement typés afin que les utilisateurs ne soient pas tenus d'effectuer un cast d'arguments en type <xref:System.Object> lorsqu'ils utilisent les fonctionnalités fournies par l'interface.  Cette règle suppose que le type qui implémente <xref:System.Collections.ICollection> le fasse pour gérer une collection d'instances d'un type plus fort que <xref:System.Object>.  
  
 <xref:System.Collections.ICollection> implémente l'interface <xref:System.Collections.IEnumerable?displayProperty=fullName>.  Si les objets dans la collection étendent <xref:System.ValueType?displayProperty=fullName>, vous devez fournir un membre fortement typé pour que <xref:System.Collections.IEnumerable.GetEnumerator%2A> évite la baisse des performances provoquée par le boxing.  Ceci n'est pas requis quand les objets de la collection sont un type référence.  
  
 Pour implémenter une version fortement typée d'un membre d'interface, implémentez explicitement les membres d'interface à l'aide de noms dans le formulaire `InterfaceName.InterfaceMemberName`, tels que <xref:System.Collections.ICollection.CopyTo%2A>.  Les membres d'interface explicites utilisent les types de données déclarés par l'interface.  Implémentez les membres fortement typés à l'aide du nom de membre d'interface, tel que <xref:System.Collections.ICollection.CopyTo%2A>.  Déclarez les membres fortement typés comme publics et déclarez des paramètres et des valeurs de retour de sorte qu'ils soient du type fort géré par la collection.  Les types forts remplacent les types plus faibles, tels que <xref:System.Object> et <xref:System.Array>, déclarés par l'interface.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, implémentez le membre d'interface explicitement \(déclarez\-le en tant que <xref:System.Collections.ICollection.CopyTo%2A>\).  Ajoutez le membre fortement typé public, déclaré comme `CopyTo`, et faites\-lui accepter un tableau fortement typé en tant que premier paramètre.  
  
## Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle si vous implémentez une nouvelle collection fondée sur des objets, telle qu'une arborescence binaire, où des types qui étendent la nouvelle collection déterminent le type fort.  Ces types doivent se conformer à cette règle et exposer des membres fortement typés.  
  
## Exemple  
 L'exemple suivant présente la façon correcte d'implémenter <xref:System.Collections.ICollection>.  
  
 [!code-cs[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]  
  
## Règles connexes  
 [CA1038 : Les énumérateurs doivent être fortement typés](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
 [CA1039 : Les listes sont fortement typées](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## Voir aussi  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>