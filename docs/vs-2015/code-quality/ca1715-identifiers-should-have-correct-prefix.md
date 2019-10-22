---
title: 'CA1715 : les identificateurs doivent avoir un préfixe correct | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5988d472317540ca1b1a7f91acd75a48fa9743b4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669117"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715 : Les identificateurs doivent être dotés d'un préfixe correct
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la documentation la plus récente sur Visual Studio, consultez [CA1715 : les identificateurs doivent avoir un préfixe correct](https://docs.microsoft.com/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix).

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|Category|Microsoft. Naming|
|Modification avec rupture|Avec rupture : lorsqu’elle est déclenchée sur les interfaces.<br /><br /> Sans rupture-en cas de déclenchement sur des paramètres de type générique.|

## <a name="cause"></a>Cause
 Le nom d’une interface extérieurement visible ne commence pas par un « I » majuscule.

 ou

 Le nom d’un paramètre de type générique sur un type ou une méthode extérieurement visible ne commence pas par un « t » majuscule.

## <a name="rule-description"></a>Description de la règle
 Par Convention, les noms de certains éléments de programmation commencent par un préfixe spécifique.

 Les noms d’interface doivent commencer par un « I » majuscule suivi d’une autre lettre majuscule. Cette règle signale des violations pour les noms d’interface tels que « MyInterface » et « IsolatedInterface ».

 Les noms de paramètre de type générique doivent commencer par un « t » majuscule et éventuellement être suivis par une autre lettre majuscule. Cette règle signale des violations pour les noms de paramètre de type générique tels que’V’et’type'.

 Les conventions d’affectation de noms fournissent une recherche commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage requise pour les nouvelles bibliothèques logicielles et augmente la confiance des clients dans la mesure où la bibliothèque a été développée par une personne ayant une expertise dans le développement de code géré.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Renommez l’identificateur afin qu’il soit correctement préfixé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 **L’exemple suivant montre une interface nommée de manière incorrecte.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix.vb#1)]

## <a name="example"></a>Exemple
 **L’exemple suivant résout la violation précédente en préfixant l’interface par’I'.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2.vb#1)]

## <a name="example"></a>Exemple
 **L’exemple suivant montre un paramètre de type générique nommé de manière incorrecte.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3.vb#1)]

## <a name="example"></a>Exemple
 **L’exemple suivant résout la violation précédente en préfixant le paramètre de type générique avec’t'.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1722 : Les identificateurs ne doivent pas avoir un préfixe incorrect](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)
