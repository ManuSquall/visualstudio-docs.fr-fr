---
title: 'CA1502 : Éviter l’excès de complexité'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 21b623041bdf599439fd51f99354f206eb25c433
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893154"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502 : Éviter l’excès de complexité

|||
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|Category|Microsoft.Maintainability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une méthode a une complexité cyclomatique excessive.

## <a name="rule-description"></a>Description de la règle

*Complexité cyclomatique* mesure le nombre de chemins linéairement indépendants dans la méthode, qui est déterminé par le nombre et la complexité des branches conditionnelles. Une complexité cyclomatique faible indique généralement une méthode facile à comprendre, à tester et à gérer. La complexité cyclomatique est calculée à partir d’un graphique de flux de contrôle de la méthode et est fournie comme suit :

complexité cyclomatique = nombre de bords - le nombre de nœuds + 1

où un nœud représente un point de branchement logique et un bord représente une ligne entre les nœuds.

La règle signale une violation lorsque la complexité cyclomatique est supérieure à 25.

Plus d’informations sur la métrique du code à [mesure la complexité et la facilité de maintenance du Code managé](../code-quality/code-metrics-values.md),

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, refactorisez la méthode pour réduire sa complexité cyclomatique.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle si la complexité ne peut pas facilement être réduite et la méthode est facile à comprendre, à tester et à gérer. En particulier, une méthode qui contient un grand `switch` (`Select` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) instruction est un candidat pour l’exclusion. Le risque de déstabiliser le code base dans le cycle de développement ou d’introduire un changement inattendu dans le comportement d’exécution dans le code précédemment expédié peut compenser les avantages de la facilité de maintenance de refactoriser le code.

## <a name="how-cyclomatic-complexity-is-calculated"></a>Mode de calcul de complexité cyclomatique

La complexité cyclomatique est calculée en ajoutant 1 à ce qui suit :

- Nombre de branches (tel que `if`, `while`, et `do`)

- Nombre de `case` instructions dans un `switch`

## <a name="example"></a>Exemple

Les exemples suivants montrent des méthodes qui ont différentes complexité cyclomatique.

**Complexité cyclomatique 1**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]

## <a name="example"></a>Exemple

**Complexité cyclomatique de 2**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]

## <a name="example"></a>Exemple

**Complexité cyclomatique de 3**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]

## <a name="example"></a>Exemple

**Complexité cyclomatique de 8**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]

## <a name="related-rules"></a>Règles associées

[CA1501 : Éviter l’excès d’héritage](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>Voir aussi

- [Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/code-metrics-values.md)