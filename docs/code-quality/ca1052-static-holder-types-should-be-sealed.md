---
title: 'CA1052 : Les types de conteneurs statiques doivent être sealed'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 46a8c9a4e22c7a54a4b2b68f95bb2b81f3a0888e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778591"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052 : Les types de conteneurs statiques doivent être sealed

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un type non abstrait contient uniquement des membres statiques et n’est pas déclaré avec le [sealed](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) modificateur.

Par défaut, cette règle examine uniquement les types visibles de l’extérieur, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

CA1052 de règle suppose qu’un type qui contient uniquement des membres statiques n’est pas conçu pour être héritée, de le, car le type ne fournit pas toutes les fonctionnalités qui peuvent être substituées dans un type dérivé. Un type qui n’est pas destiné à être hérité doit être marqué avec le `sealed` ou `NotInheritable` modificateur d’empêcher son utilisation comme un type de base. Cette règle ne déclenche pas pour les classes abstraites.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, marquez le type comme `sealed` ou `NotInheritable`. Si vous ciblez .NET Framework 2.0 ou version ultérieure, une meilleure approche consiste à marquer le type en tant que `static` ou `Shared`. De cette manière, vous n’êtes pas obligé de déclarer un constructeur privé pour empêcher la création de la classe.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Supprimez un avertissement de cette règle uniquement si le type est conçu pour être hérité. L’absence de la `sealed` ou `NotInheritable` modificateur suggère que le type est utile comme type de base.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```
dotnet_code_quality.ca1052.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Exemple de violation

L’exemple suivant montre un type qui viole la règle :

[!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
[!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
[!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Résoudre avec le modificateur static

L’exemple suivant montre comment la corriger une violation de cette règle en marquant le type avec le `static` modificateur dans C#:

[!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>Règles associées

- [CA1053 : Types de conteneurs statiques ne doivent pas avoir de constructeurs](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)