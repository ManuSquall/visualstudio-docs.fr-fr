---
title: 'CA1002 : Ne pas exposer de listes génériques'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdfee238bc6cb77f77d38151c1a604cf3f463e7f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002 : Ne pas exposer de listes génériques
|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type contient un membre extérieurement visible est un <xref:System.Collections.Generic.List%601?displayProperty=fullName> de type, retourne un <xref:System.Collections.Generic.List%601?displayProperty=fullName> type, ou dont la signature inclut un <xref:System.Collections.Generic.List%601?displayProperty=fullName> paramètre.

## <a name="rule-description"></a>Description de la règle
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> est une collection générique conçue pour des performances et non l’héritage. <xref:System.Collections.Generic.List%601?displayProperty=fullName> ne contient pas de membres virtuels qui le rendent plus facile de modifier le comportement d’une classe héritée. Les collections génériques suivantes sont conçues pour l’héritage et doivent être exposées à la place de <xref:System.Collections.Generic.List%601?displayProperty=fullName>.

-   <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

-   <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez le <xref:System.Collections.Generic.List%601?displayProperty=fullName> type à une des collections génériques qui est conçu pour l’héritage.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle, sauf si l’assembly qui déclenche cet avertissement ne doit pas être une bibliothèque réutilisable. Par exemple, il serait possible de supprimer cet avertissement dans une application de paramétrage des performances sans où un gain de performances a été acquise à partir de l’utilisation de listes génériques.

## <a name="related-rules"></a>Règles associées
 [CA1005 : Évitez trop de paramètres sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010 : Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000 : Ne déclarez pas de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003 : Utiliser les instances du gestionnaire d’événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007 : Utiliser des méthodes génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Voir aussi
 [Génériques](/dotnet/csharp/programming-guide/generics/index)