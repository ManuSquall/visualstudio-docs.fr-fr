---
title: 'CA1052 : Types de conteneurs statiques doivent être sealed'
ms.date: 11/09/2018
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0ec090fd11c122699bafb3d72ca1eeab13ecb830
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825943"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052 : Types de conteneurs statiques doivent être sealed

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un public ou protégé, non abstraite type contient uniquement des membres statiques et n’est pas déclaré avec le [sealed](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) modificateur.

## <a name="rule-description"></a>Description de la règle

CA1052 de règle suppose qu’un type qui contient uniquement des membres statiques n’est pas conçu pour être héritée, de le, car le type ne fournit pas toutes les fonctionnalités qui peuvent être substituées dans un type dérivé. Un type qui n’est pas destiné à être hérité doit être marqué avec le `sealed` ou `NotInheritable` modificateur d’empêcher son utilisation comme un type de base. Cette règle ne déclenche pas pour les classes abstraites.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, marquez le type comme `sealed` ou `NotInheritable`. Si vous ciblez .NET Framework 2.0 ou version ultérieure, une meilleure approche consiste à marquer le type en tant que `static` ou `Shared`. De cette manière, vous n’êtes pas obligé de déclarer un constructeur privé pour empêcher la création de la classe.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Supprimez un avertissement de cette règle uniquement si le type est conçu pour être hérité. L’absence de la `sealed` ou `NotInheritable` modificateur suggère que le type est utile comme type de base.

## <a name="example-of-a-violation"></a>Exemple de violation

L’exemple suivant montre un type qui viole la règle.

[!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
[!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
[!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Résoudre avec le modificateur static

L’exemple suivant montre comment la corriger une violation de cette règle en marquant le type avec le `static` modificateur dans C#.

[!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>Règles associées

[CA1053 : Types de conteneurs statiques ne doivent pas avoir de constructeurs](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)