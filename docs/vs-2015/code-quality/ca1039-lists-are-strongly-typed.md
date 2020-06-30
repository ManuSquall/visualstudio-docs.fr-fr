---
title: 'CA1039 : les listes sont fortement typées | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4e485375c12564b5416c79bd3a41dedb1da76dc0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533443"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039 : Les listes sont fortement typées
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le type public ou protégé implémente, <xref:System.Collections.IList?displayProperty=fullName> mais ne fournit pas de méthode fortement typée pour un ou plusieurs des éléments suivants :

- IList. Item

- IList. Add

- IList. Contains

- IList. IndexOf

- IList. Insert

- IList. Remove

## <a name="rule-description"></a>Description de la règle
 Cette règle requiert <xref:System.Collections.IList> que les implémentations fournissent des membres fortement typés afin que les utilisateurs ne soient pas tenus d’effectuer un cast d’arguments en <xref:System.Object?displayProperty=fullName> type lorsqu’ils utilisent les fonctionnalités fournies par l’interface. L' <xref:System.Collections.IList> interface est implémentée par des collections d’objets accessibles par index. Cette règle suppose que le type qui implémente <xref:System.Collections.IList> effectue cela pour gérer une collection d’instances d’un type qui est plus fort que <xref:System.Object> .

 <xref:System.Collections.IList>implémente les <xref:System.Collections.ICollection?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName> interfaces et. Si vous implémentez <xref:System.Collections.IList> , vous devez fournir les membres fortement typés requis pour <xref:System.Collections.ICollection> . Si les objets de la collection étendent <xref:System.ValueType?displayProperty=fullName> , vous devez fournir un membre fortement typé pour <xref:System.Collections.IEnumerable.GetEnumerator%2A> afin d’éviter la diminution des performances provoquée par le boxing ; cela n’est pas nécessaire lorsque les objets de la collection sont un type référence.

 Pour se conformer à cette règle, implémentez les membres d’interface explicitement en utilisant des noms au format NomInterface. InterfaceMemberName, tels que <xref:System.Collections.IList.Add%2A> . Les membres d’interface explicites utilisent les types de données déclarés par l’interface. Implémentez les membres fortement typés à l’aide du nom de membre d’interface, tel que `Add` . Déclarez les membres fortement typés comme publics et déclarez les paramètres et les valeurs de retour comme étant du type fort géré par la collection. Les types forts remplacent les types plus faibles tels que <xref:System.Object> et <xref:System.Array> qui sont déclarés par l’interface.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, implémentez explicitement des <xref:System.Collections.IList> membres et fournissez des alternatives fortement typées pour les membres qui ont été notés précédemment. Pour le code qui implémente correctement l' <xref:System.Collections.IList> interface et fournit les membres fortement typés requis, consultez l’exemple suivant.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle quand vous implémentez une nouvelle collection basée sur un objet, telle qu’une liste liée, où les types qui étendent la nouvelle collection déterminent le type fort. Ces types doivent être conformes à cette règle et exposer des membres fortement typés.

## <a name="example"></a>Exemple
 Dans l’exemple suivant, le type s' `YourType` étend <xref:System.Collections.CollectionBase?displayProperty=fullName> , comme dans le cas de toutes les collections fortement typées. Notez que <xref:System.Collections.CollectionBase> fournit l’implémentation explicite de l' <xref:System.Collections.IList> interface pour vous. Par conséquent, vous devez fournir uniquement les membres fortement typés pour <xref:System.Collections.IList> et <xref:System.Collections.ICollection> .

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IListStrongTypes/cs/FxCop.Design.IListStrongTypes.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA1035 : Les implémentations ICollection possèdent des membres fortement typés](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038 : Les énumérateurs doivent être fortement typés](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.IList?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
