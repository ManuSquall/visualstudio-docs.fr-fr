---
title: "CA1039 : Les listes sont fortement typées | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 358ae06a2913f7b89338027c79f81c298253d23b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039 : Les listes sont fortement typées
|||  
|-|-|  
|TypeName|ListsAreStronglyTyped|  
|CheckId|CA1039|  
|Category|Microsoft.Design|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 La valeur public ou protégé implémente de type <xref:System.Collections.IList?displayProperty=fullName> mais ne fournit pas de méthode fortement typée pour un ou plusieurs des opérations suivantes :  
  
-   IList.Item  
  
-   IList.Add  
  
-   IList.Contains.  
  
-   IList.IndexOf.  
  
-   IList.Insert  
  
-   IList.Remove  
  
## <a name="rule-description"></a>Description de la règle  
 Cette règle requiert <xref:System.Collections.IList> fournir fortement les implémentations des membres typés afin que les utilisateurs ne doivent pas effectuer un cast d’arguments à la <xref:System.Object?displayProperty=fullName> lorsqu’ils utilisent les fonctionnalités fournies par l’interface de type. Le <xref:System.Collections.IList> interface est implémentée par des collections d’objets qui sont accessibles par index. Cette règle suppose que le type qui implémente <xref:System.Collections.IList> procède ainsi pour gérer une collection d’instances d’un type plus fort que <xref:System.Object>.  
  
 <xref:System.Collections.IList>implémente le <xref:System.Collections.ICollection?displayProperty=fullName> et <xref:System.Collections.IEnumerable?displayProperty=fullName> interfaces. Si vous implémentez <xref:System.Collections.IList>, vous devez fournir les membres fortement typés requis pour <xref:System.Collections.ICollection>. Si les objets dans la collection étendent <xref:System.ValueType?displayProperty=fullName>, vous devez fournir un membre fortement typé pour <xref:System.Collections.IEnumerable.GetEnumerator%2A> afin d’éviter la baisse de performances qui est provoquée par une opération boxing ; cela n’est pas nécessaire lorsque les objets de la collection sont un type référence.  
  
 Pour se conformer à cette règle, implémentez les membres d’interface explicitement à l’aide de noms dans le formulaire InterfaceName.InterfaceMemberName, tels que <xref:System.Collections.IList.Add%2A>. Les membres d’interface explicites utilisent les types de données qui sont déclarés par l’interface. Implémenter des membres fortement typés à l’aide du nom de membre d’interface, tel que `Add`. Déclarer des membres fortement typés comme publics et déclarer des paramètres et retournent des valeurs de type fort géré par la collection. Les types forts remplacent les types plus faibles telles que <xref:System.Object> et <xref:System.Array> qui sont déclarés par l’interface.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, implémentez explicitement <xref:System.Collections.IList> membres et fournir des alternatives fortement typés pour les membres qui ont été précédemment. Pour le code qui implémente correctement la <xref:System.Collections.IList> de l’interface et fournit les membres fortement typés, consultez l’exemple suivant.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Supprimer un avertissement de cette règle lorsque vous implémentez une nouvelle collection orientée objet, telle qu’une liste liée, où des types qui étendent la nouvelle collection déterminent le type fort. Ces types doivent être compatible avec cette règle et exposer des membres fortement typés.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, le type `YourType` étend <xref:System.Collections.CollectionBase?displayProperty=fullName>, comme toutes les collections fortement typées. Notez que <xref:System.Collections.CollectionBase> fournit l’implémentation explicite de la <xref:System.Collections.IList> interface pour vous. Par conséquent, vous devez fournir uniquement des membres fortement typés pour <xref:System.Collections.IList> et <xref:System.Collections.ICollection>.  
  
 [!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1035 : Les implémentations ICollection ont des membres fortement typés](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1038 : Les énumérateurs doivent être fortement typés](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.IList?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>