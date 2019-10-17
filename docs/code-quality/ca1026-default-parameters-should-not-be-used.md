---
title: 'CA1026 : Les paramètres par défaut ne doivent pas être utilisés'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7bf388af2b39c9a10b58645f274a03739d60f23e
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449291"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026 : Les paramètres par défaut ne doivent pas être utilisés

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Un type visible de l’extérieur contient une méthode visible de l’extérieur qui utilise un paramètre par défaut.

## <a name="rule-description"></a>Description de la règle
Les méthodes qui utilisent des paramètres par défaut sont autorisées sous le Common Language Specification (CLS); Toutefois, la spécification CLS permet aux compilateurs d’ignorer les valeurs assignées à ces paramètres. Le code écrit pour les compilateurs qui ignorent les valeurs de paramètres par défaut doit fournir explicitement des arguments pour chaque paramètre par défaut. Pour conserver le comportement que vous souhaitez dans les langages de programmation, les méthodes qui utilisent des paramètres par défaut doivent être remplacées par des surcharges de méthode qui fournissent les paramètres par défaut.

Le compilateur ignore les valeurs des paramètres par défaut pour l’extension C++ managée pour lorsqu’il accède au code managé. Le compilateur Visual Basic prend en charge les méthodes qui ont des paramètres par défaut qui utilisent le mot clé [facultatif](/dotnet/visual-basic/language-reference/modifiers/optional) .

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, remplacez la méthode qui utilise des paramètres par défaut par des surcharges de méthode qui fournissent les paramètres par défaut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
L’exemple suivant montre une méthode qui utilise des paramètres par défaut et les méthodes surchargées qui fournissent une fonctionnalité équivalente.

[!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]

## <a name="related-rules"></a>Règles associées
[CA1025 : Remplacez les arguments répétitifs par un tableau params](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Voir aussi
[Indépendance du langage et composants indépendants du langage](/dotnet/standard/language-independence-and-language-independent-components)
