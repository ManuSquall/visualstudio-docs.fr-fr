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
ms.openlocfilehash: 875e0b4052cdc7287b264899620d4e083ac6b153
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443876"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715 : Les identificateurs doivent être dotés d'un préfixe correct

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|Category|Microsoft. Naming|
|Modification avec rupture|Avec rupture : lorsqu’elle est déclenchée sur les interfaces.<br /><br /> Sans rupture-en cas de déclenchement sur des paramètres de type générique.|

## <a name="cause"></a>Cause

Le nom d’une interface ne commence pas par un « I » majuscule.

ou

Le nom d’un [paramètre de type générique](/dotnet/csharp/programming-guide/generics/generic-type-parameters) sur un type ou une méthode ne commence pas par un « t » majuscule.

Par défaut, cette règle recherche uniquement les interfaces, les types et les méthodes visibles de l’extérieur, mais cela peut [être configuré](#configurability).

## <a name="rule-description"></a>Description de la règle

Par Convention, les noms de certains éléments de programmation commencent par un préfixe spécifique.

Les noms d’interface doivent commencer par un « I » majuscule suivi d’une autre lettre majuscule. Cette règle signale des violations pour les noms d’interface tels que « MyInterface » et « IsolatedInterface ».

Les noms de paramètre de type générique doivent commencer par un « t » majuscule et éventuellement être suivis par une autre lettre majuscule. Cette règle signale des violations pour les noms de paramètre de type générique tels que’V’et’type'.

Les conventions d’affectation de noms fournissent une recherche commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage requise pour les nouvelles bibliothèques logicielles et augmente la confiance des clients dans la mesure où la bibliothèque a été développée par une personne ayant une expertise dans le développement de code géré.

## <a name="configurability"></a>Configurabilité

Si vous exécutez cette règle à partir d' [analyseurs FxCop](install-fxcop-analyzers.md) (et non avec l’analyse héritée), vous pouvez configurer les parties de votre code analysées par cette règle. Pour plus d’informations, consultez [configurer les analyseurs FxCop](configure-fxcop-analyzers.md).

### <a name="single-character-type-parameters"></a>Paramètres de type à un seul caractère

Vous pouvez configurer s’il faut ou non exclure les paramètres de type à un seul caractère de cette règle. Par exemple, pour spécifier que cette règle ne *doit pas* analyser les paramètres de type à un seul caractère, ajoutez l’une des paires clé-valeur suivantes à un fichier. editorconfig dans votre projet :

```ini
# Package version 2.9.0 and later
dotnet_code_quality.CA1715.exclude_single_letter_type_parameters = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.allow_single_letter_type_parameters = true
```

> [!NOTE]
> Cette règle ne se déclenche jamais pour un paramètre de type nommé `T`, par exemple, `Collection<T>`.

### <a name="api-surface"></a>Surface de l’API

Vous pouvez configurer les parties de votre code base pour exécuter cette règle, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet :

```ini
dotnet_code_quality.ca1715.api_surface = private, internal
```

Vous pouvez configurer cette option uniquement pour cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (affectation de noms).

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Renommez l’identificateur afin qu’il soit correctement préfixé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle.

## <a name="interface-naming-example"></a>Exemple d’affectation de noms d’interface

L’extrait de code suivant montre une interface de nom incorrecte :

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

L’extrait de code suivant résout la violation précédente en préfixant l’interface par’I' :

[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="type-parameter-naming-example"></a>Exemple de nom de paramètre de type

L’extrait de code suivant montre un paramètre de type générique nommé de manière incorrecte :

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

L’extrait de code suivant résout la violation précédente en préfixant le paramètre de type générique avec’t' :

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>Règles associées

- [CA1722 : Les identificateurs ne doivent pas avoir un préfixe incorrect](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)
