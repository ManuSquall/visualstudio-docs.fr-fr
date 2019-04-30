---
title: 'CA1007 : Utiliser des classes génériques lorsque cela est approprié'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f1cf2939f0484c6defb76b88fb072fcd4b51849b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779711"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007 : Utiliser des classes génériques lorsque cela est approprié

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode extérieurement visible contient un paramètre de référence de type <xref:System.Object?displayProperty=fullName>et l’assembly conteneur cible [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="rule-description"></a>Description de la règle
 Un paramètre de référence est un paramètre qui est modifié à l’aide de la `ref` (`ByRef` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) mot clé. Le type d’argument fourni pour un paramètre de référence doit correspondre exactement au type de paramètre de référence. Pour utiliser un type qui est dérivé du type de paramètre de référence, le type doit tout d’abord être converti et assigné à une variable du type de paramètre de référence. Utilisation d’une méthode générique autorise tous les types, soumis aux contraintes, doivent être passés à la méthode sans cast préalable du type pour le type de paramètre de référence.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, rendez la méthode générique et remplacez le <xref:System.Object> paramètre à l’aide d’un paramètre de type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre une routine de permutation à usage général qui est implémentée en tant que méthodes génériques et non. Notez comment efficacement les chaînes sont permutées à l’aide de la méthode générique par rapport à la méthode non générique.

 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>Règles associées
 [CA1005 : Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010 : Collections doivent implémenter l’interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000 : Ne déclarez pas de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002 : N’exposez pas de listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003 : Utiliser des instances du Gestionnaire d’événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>Voir aussi
 [Génériques](/dotnet/csharp/programming-guide/generics/index)