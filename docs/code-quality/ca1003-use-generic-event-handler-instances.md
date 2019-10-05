---
title: "CA1003 : Utiliser les instances du gestionnaire d'événements génériques"
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c654da177e4a9cf820887cf74977a4c3da5a57b6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236646"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003 : Utiliser les instances du gestionnaire d'événements génériques

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un type contient un délégué qui retourne void et dont la signature contient deux paramètres (le premier objet et le second un type qui peut être assigné à EventArgs), et l’assembly conteneur cible .NET.

Par défaut, cette règle recherche uniquement les types visibles de l’extérieur, mais elle peut [être configurée](#configurability).

## <a name="rule-description"></a>Description de la règle

Avant .net, pour passer des informations personnalisées au gestionnaire d’événements, il fallait déclarer un nouveau délégué qui spécifiait une classe dérivée de la <xref:System.EventArgs?displayProperty=fullName> classe. Dans .net, le délégué <xref:System.EventHandler%601?displayProperty=fullName> générique permet l’utilisation d’une classe dérivée de <xref:System.EventArgs> pour être utilisée avec le gestionnaire d’événements.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, supprimez le délégué et remplacez son utilisation à l' <xref:System.EventHandler%601?displayProperty=fullName> aide du délégué.

Si le délégué est généré automatiquement par le compilateur Visual Basic, modifiez la syntaxe de la déclaration d’événement pour utiliser <xref:System.EventHandler%601?displayProperty=fullName> le délégué.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle.

## <a name="configurability"></a>Configurabilité

Si vous exécutez cette règle à partir d' [analyseurs FxCop](install-fxcop-analyzers.md) (et non avec l’analyse héritée), vous pouvez configurer les parties de votre code base sur lesquelles exécuter cette règle, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet :

```ini
dotnet_code_quality.ca1003.api_surface = private, internal
```

Vous pouvez configurer cette option uniquement pour cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [configurer les analyseurs FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un délégué qui enfreint la règle. Dans l’exemple Visual Basic, les commentaires décrivent comment modifier l’exemple pour satisfaire la règle. Pour l' C# exemple, voici un exemple qui montre le code modifié.

[!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
[!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

L’extrait de code suivant supprime la déclaration Delegate de l’exemple précédent, qui répond à la règle. Il remplace son utilisation dans les `ClassThatRaisesEvent` méthodes `ClassThatHandlesEvent` et à l’aide <xref:System.EventHandler%601?displayProperty=fullName> du délégué.

[!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Règles associées

- [CA1005 Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010 Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1000 Ne pas déclarer de membres statiques sur des types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002 Ne pas exposer les listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006 Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004 Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1007 Utiliser des génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Voir aussi

- [Génériques](/dotnet/csharp/programming-guide/generics/index)