---
title: 'CA1000 : Ne pas déclarer de membres statiques sur les types génériques'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f10433330642ee06dd7f705cdd8e35333cd8a79d
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547923"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000 : Ne pas déclarer de membres statiques sur les types génériques

|||
|-|-|
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|
|CheckId|CA1000|
|Catégorie|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un type générique contient un `static` membre`Shared` (dans Visual Basic).

Par défaut, cette règle recherche uniquement les types visibles de l’extérieur, mais elle peut [être configurée](#configurability).

## <a name="rule-description"></a>Description de la règle

Lorsqu’un `static` membre d’un type générique est appelé, l’argument de type doit être spécifié pour le type. Lorsqu’un membre d’instance générique qui ne prend pas en charge l’inférence est appelé, l’argument de type doit être spécifié pour le membre. La syntaxe permettant de spécifier l’argument de type dans ces deux cas est différente et facilement confondue, comme le montrent les appels suivants:

```vb
' Shared method in a generic type.
GenericType(Of Integer).SharedMethod()

' Generic instance method that does not support inference.
someObject.GenericMethod(Of Integer)()
```

```csharp
// Static method in a generic type.
GenericType<int>.StaticMethod();

// Generic instance method that does not support inference.
someObject.GenericMethod<int>();
```

En règle générale, les deux déclarations précédentes doivent être évitées afin qu’il ne soit pas nécessaire de spécifier l’argument de type lorsque le membre est appelé. Cela aboutit à une syntaxe pour appeler des membres dans des génériques qui n’est pas différent de la syntaxe pour les non génériques. Pour plus d’informations, [consultez CA1004: Les méthodes génériques doivent fournir un](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)paramètre de type.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, supprimez le membre statique ou remplacez-le par un membre d’instance.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle. La fourniture de génériques dans une syntaxe facile à comprendre et à utiliser réduit le temps nécessaire à l’apprentissage et à l’augmentation du taux d’adoption de nouvelles bibliothèques.

## <a name="configurability"></a>Configurabilité

Si vous exécutez cette règle à partir d' [analyseurs FxCop](install-fxcop-analyzers.md) (et non avec l’analyse héritée), vous pouvez configurer les parties de votre code base sur lesquelles exécuter cette règle, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet:

```ini
dotnet_code_quality.ca1000.api_surface = private, internal
```

Vous pouvez configurer cette option uniquement pour cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [configurer les analyseurs FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Règles associées

- [CA1005 Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010 Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1002 Ne pas exposer les listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006 Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004 Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003 Utiliser les instances du gestionnaire d’événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007 Utiliser des génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Voir aussi

- [Génériques](/dotnet/csharp/programming-guide/generics/index)