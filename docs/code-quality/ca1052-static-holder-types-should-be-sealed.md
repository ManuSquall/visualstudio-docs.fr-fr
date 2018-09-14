---
title: 'CA1052 : Les types de conteneurs statiques doivent être sealed'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: bc264b9e47fe9169c0b1ad9d3257323c437620f7
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550425"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052 : Les types de conteneurs statiques doivent être sealed

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé contient uniquement des membres statiques et n’est pas déclaré avec le [sealed](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) modificateur.

## <a name="rule-description"></a>Description de la règle
 Cette règle suppose qu’un type qui contient uniquement des membres statiques n’est pas conçu pour être héritée, de le, car le type ne fournit pas toutes les fonctionnalités qui peuvent être substituées dans un type dérivé. Un type qui n’est pas destiné à être hérité doit être marqué avec le `sealed` modificateur d’empêcher son utilisation comme un type de base.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, marquez le type comme `sealed`. Si vous ciblez [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 ou version ultérieure, une meilleure approche consiste à marquer le type comme `static`. De cette manière, vous évitez d’avoir à déclarer un constructeur privé pour empêcher la création de la classe.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle uniquement si le type est conçu pour être hérité. L’absence de la `sealed` modificateur suggère que le type est utile comme type de base.

## <a name="example-of-a-violation"></a>Exemple de Violation

### <a name="description"></a>Description
 L’exemple suivant montre un type qui viole la règle.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Résoudre avec le modificateur Static

### <a name="description"></a>Description
 L’exemple suivant montre comment la corriger une violation de cette règle en marquant le type avec le `static` modificateur.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>Règles associées
 [CA1053 : Les types de conteneurs statiques ne doivent pas comporter de constructeur](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
