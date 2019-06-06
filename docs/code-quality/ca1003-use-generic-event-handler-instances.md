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
ms.openlocfilehash: 66bb2b2229608c1a7710b7c5c71cbc0d701234e3
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714376"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003 : Utiliser les instances du gestionnaire d'événements génériques

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un type contient un délégué qui retourne void et dont la signature contient deux paramètres (le premier est un objet et le second est un type pouvant être assigné à EventArgs) et assembly cibles .NET qui le contient.

Par défaut, cette règle examine uniquement les types visibles de l’extérieur, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

Avant .NET, afin de passer des informations personnalisées au gestionnaire d’événements, un nouveau délégué devait être déclaré qui a spécifié une classe qui était dérivée de la <xref:System.EventArgs?displayProperty=fullName> classe. Dans .NET, le modèle générique <xref:System.EventHandler%601?displayProperty=fullName> délégué permet de n’importe quelle classe dérivée de <xref:System.EventArgs> pour être utilisée avec le Gestionnaire d’événements.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, supprimez le délégué et remplacez son utilisation à l’aide de la <xref:System.EventHandler%601?displayProperty=fullName> déléguer.

Si le délégué est généré automatiquement par le compilateur Visual Basic, modifiez la syntaxe de la déclaration d’événement à utiliser le <xref:System.EventHandler%601?displayProperty=fullName> déléguer.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```ini
dotnet_code_quality.ca1003.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un délégué qui enfreint la règle. Dans l’exemple Visual Basic, les commentaires expliquent comment modifier l’exemple pour satisfaire à la règle. Pour l’exemple c#, un exemple qui suit présente le code modifié.

[!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
[!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

L’extrait de code suivant supprime la déclaration du délégué de l’exemple précédent, ce qui satisfait la règle. Il remplace son utilisation dans le `ClassThatRaisesEvent` et `ClassThatHandlesEvent` méthodes aide le <xref:System.EventHandler%601?displayProperty=fullName> déléguer.

[!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Règles associées

- [CA1005 : Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010 : Collections doivent implémenter l’interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1000 : Ne déclarez pas de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002 : N’exposez pas de listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1007 : Utiliser des classes génériques le cas échéant](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Voir aussi

- [Génériques](/dotnet/csharp/programming-guide/generics/index)