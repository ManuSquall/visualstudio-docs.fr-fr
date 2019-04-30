---
title: 'CA1038 : Les énumérateurs doivent être fortement typés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 84b6ae6ef0c63870ad9dc593fd0cf2e166e65397
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62559827"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038 : Les énumérateurs doivent être fortement typés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé implémente <xref:System.Collections.IEnumerator?displayProperty=fullName> mais ne fournit ne pas une version fortement typée de la <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> propriété. Les types qui sont dérivés des types suivants sont exemptés de cette règle :

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Description de la règle
 Cette règle requiert <xref:System.Collections.IEnumerator> implémentations fournissent également une version fortement typée de la <xref:System.Collections.IEnumerator.Current%2A> propriété afin que les utilisateurs ne soient pas tenus d’effectuer un cast de la valeur de retour vers le type fort lorsqu’ils utilisent les fonctionnalités fournies par l’interface. Cette règle suppose que le type qui implémente <xref:System.Collections.IEnumerator> contient une collection d’instances d’un type plus fort que <xref:System.Object>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, implémentez la propriété d’interface explicitement (déclarez-le en tant que `IEnumerator.Current`). Ajouter une version publique fortement typée de la propriété déclarée comme `Current`, et qu’il renvoie un objet fortement typé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimer un avertissement de cette règle lorsque vous implémentez un énumérateur basée sur un objet pour une utilisation avec une collection basée sur un objet, comme un arbre binaire. Les types qui étendent la nouvelle collection définissent l’énumérateur fortement typé et exposent la propriété fortement typée.

## <a name="example"></a>Exemple
 L’exemple suivant montre comment implémenter fortement typé <xref:System.Collections.IEnumerator> type.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA1035 : Les implémentations ICollection ont des membres fortement typés](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039 : Les listes sont fortement typées](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
