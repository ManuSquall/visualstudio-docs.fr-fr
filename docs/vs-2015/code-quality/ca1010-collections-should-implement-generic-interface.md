---
title: 'Ca1010 : les collections doivent implémenter l’interface générique | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 20238a844b45221207ca952d90d172ac720136ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655250"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010 : Les collections doivent implémenter une interface générique
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type visible de l’extérieur implémente l’interface <xref:System.Collections.IEnumerable?displayProperty=fullName> mais n’implémente pas l’interface <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>, et l’assembly conteneur cible [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]. Cette règle ignore les types qui implémentent <xref:System.Collections.IDictionary?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 Pour étendre la facilité d’utilisation d’une collection, implémentez l’une des interfaces de collection génériques. La collection peut ensuite être utilisée pour remplir des types de collections génériques, tels que les suivants :

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, implémentez l’une des interfaces de collection génériques suivantes :

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle ; Toutefois, la collection aura une utilisation plus limitée.

## <a name="example-violation"></a>Exemple de violation

### <a name="description"></a>Description
 L’exemple suivant montre une classe (type référence) qui dérive de la classe non générique `CollectionBase`, qui viole cette règle.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericViolation/cs/FxCop.Design.CollectionsGenericViolation.cs#1)]

### <a name="comments"></a>Comments
 Pour corriger une violation de cette violation, vous devez implémenter les interfaces génériques ou modifier la classe de base en un type qui implémente déjà à la fois les interfaces génériques et non génériques, telles que la classe `Collection<T>`.

## <a name="fix-by-base-class-change"></a>Corriger par modification de la classe de base

### <a name="description"></a>Description
 L’exemple suivant résout la violation en modifiant la classe de base de la collection de la classe de `CollectionBase` non générique à la classe générique `Collection<T>` (`Collection(Of T)` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericBase/cs/FxCop.Design.CollectionsGenericBase.cs#1)]

### <a name="comments"></a>Comments
 La modification de la classe de base d’une classe déjà publiée est considérée comme une modification avec rupture apportée aux consommateurs existants.

## <a name="fix-by-interface-implementation"></a>Corriger par l’implémentation de l’interface

### <a name="description"></a>Description
 L’exemple suivant résout la violation en implémentant ces interfaces génériques : `IEnumerable<T>`, `ICollection<T>` et `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)` et `IList(Of T)` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericInterface/cs/FxCop.Design.CollectionsGenericInterface.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA1005 : Évitez trop de paramètres sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000 : Ne déclarez pas de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002 : N’exposez pas de listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003 : Utiliser les instances du gestionnaire d’événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007 : Utiliser des méthodes génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Voir aussi
 [Génériques](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
