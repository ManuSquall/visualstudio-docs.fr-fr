---
title: 'CA1026 : Les paramètres par défaut ne doivent pas être utilisés'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 173a9a62ea6a3106c50fd18f37180b583e0bb42c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026 : Les paramètres par défaut ne doivent pas être utilisés
|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type visible de l’extérieur contient une méthode extérieurement visible qui utilise un paramètre par défaut.

## <a name="rule-description"></a>Description de la règle
 Les méthodes qui utilisent les paramètres par défaut sont autorisées sous le Common Language Specification (CLS) ; Toutefois, cette spécification permet aux compilateurs d’ignorer les valeurs assignées à ces paramètres. Code qui est écrit pour les compilateurs qui ignorent les valeurs de paramètre par défaut doit fournir explicitement des arguments pour chaque paramètre par défaut. Pour préserver le comportement souhaité entre les langages de programmation, les méthodes qui utilisent les paramètres par défaut doivent être remplacées par les surcharges de méthode qui fournissent les paramètres par défaut.

 Le compilateur ignore les valeurs de paramètres par défaut pour les extensions managées pour C++ lorsqu’il accède à du code managé. Le compilateur Visual Basic prend en charge les méthodes qui ont des paramètres par défaut qui utilisent le [facultatif](/dotnet/visual-basic/language-reference/modifiers/optional) (mot clé).

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez la méthode qui utilise les paramètres par défaut avec des surcharges de méthode qui fournissent les paramètres par défaut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui utilise les paramètres par défaut et les méthodes surchargées qui offrent une fonctionnalité équivalente.

 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]

## <a name="related-rules"></a>Règles associées
 [CA1025 : Remplacez les arguments répétitifs par un tableau params](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Voir aussi
 [Indépendance du langage et composants indépendants du langage](/dotnet/standard/language-independence-and-language-independent-components)