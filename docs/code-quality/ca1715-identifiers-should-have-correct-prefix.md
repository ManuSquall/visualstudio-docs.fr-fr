---
title: "CA1715 : Les identificateurs doivent être dotés d'un préfixe correct"
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b794eb7c7a258a843763b2c68902000031c17eb3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62807145"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715 : Les identificateurs doivent être dotés d'un préfixe correct

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|Category|Microsoft.Naming|
|Modification avec rupture|Avec rupture - lorsque déclenchée sur les interfaces.<br /><br /> Sans rupture - lorsque déclenchée sur les paramètres de type générique.|

## <a name="cause"></a>Cause

Le nom d’une interface ne commence pas par un « I » majuscule.

- ou -

Le nom d’un [paramètre de type générique](/dotnet/csharp/programming-guide/generics/generic-type-parameters) sur un type ou une méthode ne commence pas par une majuscule ' t ».

Par défaut, cette règle examine uniquement les interfaces extérieurement visibles, les types et méthodes, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

Par convention, les noms de certains éléments de programmation commencent par un préfixe spécifique.

Noms d’interface doivent commencer par une majuscule « I » suivie d’une autre lettre majuscule. Cette règle signale les violations pour les noms d’interface tels que 'MyInterface' et 'IsolatedInterface'.

Les noms de paramètre de type générique doivent commencer par une majuscule ' t » et éventuellement peut être suivie d’une autre lettre majuscule. Cette règle signale les violations pour les noms de paramètre de type générique comme « V » et « Type ».

Les conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage qui est requis pour les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer cette règle analyse les quelles parties de votre code. Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).

### <a name="single-character-type-parameters"></a>Paramètres de type de caractère unique

Vous pouvez configurer s’il faut exclure les paramètres de type de caractère unique de cette règle. Par exemple, pour spécifier que cette règle *ne doivent pas* analyser les paramètres de type de caractère unique, ajoutez un des paires clé-valeur suivantes dans un fichier .editorconfig dans votre projet :

```
# Package version 2.9.0 and later
dotnet_code_quality.CA1715.exclude_single_letter_type_parameters = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.allow_single_letter_type_parameters = true
```

> [!NOTE]
> Cette règle se déclenche jamais pour un paramètre de type nommé `T`, par exemple, `Collection<T>`.

### <a name="api-surface"></a>Surface d’API

Vous pouvez configurer les parties de votre base de code pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```
dotnet_code_quality.ca1715.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (d’affectation de noms).

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Renommez l’identificateur afin qu’il est correctement ajouté.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle.

## <a name="interface-naming-example"></a>Exemple d’affectation de noms d’interface

L’extrait de code suivant montre une interface incorrectement nommée :

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

L’extrait de code suivant corrige la violation précédente en préfixant l’interface avec 'I' :

[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="type-parameter-naming-example"></a>Exemple d’affectation de noms de paramètre de type

L’extrait de code suivant illustre un paramètre de type générique incorrectement nommé :

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

L’extrait de code suivant résout la violation précédente en faisant précéder le paramètre de type générique avec l ' :

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>Règles associées

- [CA1722 : Les identificateurs ne doivent pas porter un préfixe incorrect](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)