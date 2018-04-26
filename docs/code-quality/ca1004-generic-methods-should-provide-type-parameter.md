---
title: 'CA1004 : Les méthodes génériques doivent fournir un paramètre de type'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1004
- GenericMethodsShouldProvideTypeParameter
helpviewer_keywords:
- GenericMethodsShouldProvideTypeParameter
- CA1004
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c7f4616f86cdab54d1946203c46b294bea1d7aff
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004 : Les méthodes génériques doivent fournir un paramètre de type
|||
|-|-|
|TypeName|GenericMethodsShouldProvideTypeParameter|
|CheckId|CA1004|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 La signature de paramètre d’une méthode générique visible de l’extérieur ne contient pas de types qui correspondent à tous les paramètres de type de la méthode.

## <a name="rule-description"></a>Description de la règle
 L’inférence désigne la manière dont l’argument de type d’une méthode générique est déterminé par le type d’argument passé à la méthode, au lieu d’utiliser la spécification explicite de l’argument de type. Pour activer l’inférence, la signature de paramètre d’une méthode générique doit contenir un paramètre du même type que le paramètre de type de la méthode. Dans ce cas, il n’est pas nécessaire de spécifier l’argument de type. Lorsque vous utilisez l’inférence pour tous les paramètres de type, la syntaxe d’appel des méthodes d’instance génériques et non génériques est identique. Cela simplifie l’utilisation des méthodes génériques.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez la conception afin que la signature de paramètre contienne le même type pour chaque paramètre de type de la méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Fourniture de génériques dans une syntaxe facile à comprendre et à utiliser réduit le temps nécessaire pour en savoir plus et augmente le taux d’adoption de nouvelles bibliothèques.

## <a name="example"></a>Exemple
 L’exemple suivant montre la syntaxe d’appel des deux méthodes génériques. L’argument de type pour `InferredTypeArgument` est déduit et l’argument de type pour `NotInferredTypeArgument` doit être spécifié explicitement.

 [!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
 [!code-csharp[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]

## <a name="related-rules"></a>Règles associées
 [CA1005 : Évitez trop de paramètres sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010 : Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000 : Ne déclarez pas de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002 : N’exposez pas de listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1003 : Utiliser les instances du gestionnaire d’événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007 : Utiliser des méthodes génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Voir aussi
 [Génériques](/dotnet/csharp/programming-guide/generics/index)