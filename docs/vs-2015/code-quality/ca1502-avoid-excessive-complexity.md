---
title: 'CA1502 : éviter une complexité excessive | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f7b830e9d3a045bb54394a91d94e036613af7d1f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607872"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502 : Éviter l'excès de complexité
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|Category|Microsoft. maintenabilité|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode a une complexité cyclomatic excessive.

## <a name="rule-description"></a>Description de la règle
 La *complexité cyclomatic* mesure le nombre de chemins d’accès linéairement indépendants via la méthode, qui est déterminée par le nombre et la complexité des branches conditionnelles. Une complexité cyclomatic faible indique généralement une méthode facile à comprendre, à tester et à entretenir. La complexité cyclomatic est calculée à partir d’un graphique de workflow de contrôle de la méthode et est donnée comme suit :

 complexité cyclomatic = nombre de bords-nombre de nœuds + 1

 Lorsqu’un nœud représente un point de branche logique et qu’un bord représente une ligne entre des nœuds.

 La règle signale une violation lorsque la complexité cyclomatic est supérieure à 25.

 Vous pouvez en savoir plus sur les métriques [du code pour mesurer la complexité et la maintenabilité du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md),

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, refactorisez la méthode pour réduire sa complexité cyclomatic.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si la complexité ne peut pas être facilement réduite et que la méthode est facile à comprendre, à tester et à entretenir. En particulier, une méthode qui contient une instruction `switch` (`Select` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) de grande taille est candidate pour l’exclusion. Le risque de déstabiliser la base de code en retard dans le cycle de développement ou d’introduire une modification inattendue du comportement de l’exécution dans le code précédemment fourni peut avoir un surplus de l’intérêt de la facilité de maintenance de la refactorisation du code.

## <a name="how-cyclomatic-complexity-is-calculated"></a>Mode de calcul de la complexité cyclomatic
 La complexité cyclomatic est calculée en ajoutant 1 à l’exemple suivant :

- Nombre de branches (par exemple, `if`, `while` et `do`)

- Nombre d’instructions `case` dans une `switch`

  Les exemples suivants illustrent des méthodes qui ont des complexités cyclomatic variables.

## <a name="example"></a>Exemple
 **Complexité cyclomatic 1**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#1)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#1)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#1)]

## <a name="example"></a>Exemple
 **Complexité cyclomatic 2**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#2)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#2)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#2)]

## <a name="example"></a>Exemple
 **Complexité cyclomatic 3**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#3)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#3)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#3)]

## <a name="example"></a>Exemple
 **Complexité cyclomatic 8**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#4)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#4)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#4)]

## <a name="related-rules"></a>Règles associées
 [CA1501 : Évitez l’excès d’héritage](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>Voir aussi
 [Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
