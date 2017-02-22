---
title: "CA1039&#160;: Les listes sont fortement typ&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1039"
  - "ListsAreStronglyTyped"
helpviewer_keywords: 
  - "CA1039"
  - "ListsAreStronglyTyped"
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1039&#160;: Les listes sont fortement typ&#233;es
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ListsAreStronglyTyped|  
|CheckId|CA1039|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Le type public ou protégé implémente <xref:System.Collections.IList?displayProperty=fullName> mais ne fournit aucune méthode fortement typée pour l'un ou plusieurs des éléments suivants :  
  
-   IList.Item  
  
-   IList.Add  
  
-   IList.Contains  
  
-   IList.IndexOf  
  
-   IList.Insert  
  
-   IList.Remove  
  
## Description de la règle  
 Cette règle requiert que les implémentations <xref:System.Collections.IList> fournissent des membres fortement typés afin que les utilisateurs ne soient pas tenus d'effectuer un cast d'arguments en type <xref:System.Object?displayProperty=fullName> lorsqu'ils utilisent les fonctionnalités fournies par l'interface.  L'interface <xref:System.Collections.IList> est implémentée par des collections des objets accessibles par index.  Cette règle suppose que le type qui implémente <xref:System.Collections.IList> le fasse pour gérer une collection d'instances d'un type plus fort que <xref:System.Object>.  
  
 <xref:System.Collections.IList> implémente les interfaces <xref:System.Collections.ICollection?displayProperty=fullName> et <xref:System.Collections.IEnumerable?displayProperty=fullName>.  Si vous implémentez <xref:System.Collections.IList>, vous devez fournir les membres fortement typés requis pour <xref:System.Collections.ICollection>.  Si les objets de la collection étendent <xref:System.ValueType?displayProperty=fullName>, vous devez fournir un membre fortement typé pour <xref:System.Collections.IEnumerable.GetEnumerator%2A> pour éviter la baisse de performances provoquée par une opération boxing ; celle\-ci n'est pas requise si les objets de la collection constituent un type référence.  
  
 Pour vous conformer à cette règle, implémentez explicitement les membres d'interface à l'aide de noms figurant dans le formulaire InterfaceName.InterfaceMemberName, tels que <xref:System.Collections.IList.Add%2A>.  Les membres d'interface explicites utilisent les types de données déclarés par l'interface.  Implémentez les membres fortement typés à l'aide du nom de membre d'interface, tel que `Add`.  Déclarez les membres fortement typés comme publics et déclarez des paramètres et des valeurs de retour de sorte qu'ils soient du type fort géré par la collection.  Les types forts remplacent les types plus faibles, tels que <xref:System.Object> et <xref:System.Array>, déclarés par l'interface.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, implémentez explicitement des membres <xref:System.Collections.IList> et fournissez des substituts fortement typés pour les membres notés précédemment.  Pour le code qui implémente correctement l'interface <xref:System.Collections.IList> et fournit les membres fortement typés requis, consultez l'exemple suivant.  
  
## Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle lorsque vous implémentez une nouvelle collection fondée sur des objets, telle qu'une liste liée, où des types qui étendent la nouvelle collection déterminent le type fort.  Ces types doivent se conformer à cette règle et exposer des membres fortement typés.  
  
## Exemple  
 Dans l'exemple suivant, le type `YourType` étend <xref:System.Collections.CollectionBase?displayProperty=fullName>, comme le doivent toutes les collections fortement typées.  Notez que <xref:System.Collections.CollectionBase> vous fournit l'implémentation explicite de l'interface <xref:System.Collections.IList>.  Par conséquent, vous devez fournir uniquement les membres fortement typés pour <xref:System.Collections.IList> et <xref:System.Collections.ICollection>.  
  
 [!code-cs[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]  
  
## Règles connexes  
 [CA1035 : Les implémentations ICollection possèdent des membres fortement typés](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1038 : Les énumérateurs doivent être fortement typés](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
## Voir aussi  
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.IList?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>