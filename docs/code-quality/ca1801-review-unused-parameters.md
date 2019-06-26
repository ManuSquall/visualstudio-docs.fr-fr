---
title: 'CA1801 : Passez en revue les paramètres inutilisés'
ms.date: 06/24/2019
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9a0714082e0fce744fe74eaa4e4aefee5a41867
ms.sourcegitcommit: 01c3c9dcade5d913bde2c7efa8c931a7b04e6cd0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67365366"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801 : Passez en revue les paramètres inutilisés

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture - Si le membre n’est pas visible en dehors de l’assembly, quelle que soit la modification que vous apportez.<br /><br /> Sans rupture - Si vous modifiez le membre pour utiliser le paramètre dans son corps.<br /><br /> Avec rupture - Si vous supprimez le paramètre et il est visible en dehors de l’assembly.|

## <a name="cause"></a>Cause

Une signature de méthode inclut un paramètre qui n’est pas utilisé dans le corps de méthode.

Cette règle n’examine pas les types de méthodes suivants :

- Méthodes référencées par un délégué.

- Méthodes utilisées en tant que gestionnaires d’événements.

- Les méthodes déclarées avec le `abstract` (`MustOverride` en Visual Basic) modificateur.

- Les méthodes déclarées avec le `virtual` (`Overridable` en Visual Basic) modificateur.

- Les méthodes déclarées avec le `override` (`Overrides` en Visual Basic) modificateur.

- Les méthodes déclarées avec le `extern` (`Declare` instruction en Visual Basic) modificateur.

## <a name="rule-description"></a>Description de la règle

Passez en revue les paramètres dans les méthodes non virtuelles qui ne sont pas utilisés dans le corps de méthode pour vous assurer n’empêche existe autour d’y accéder. Les paramètres inutilisés impliquent des coûts de maintenance et de performances.

Parfois, une violation de cette règle peut pointer vers un bogue d’implémentation dans la méthode. Par exemple, le paramètre doit avoir été utilisé dans le corps de méthode. Supprimer les avertissements de cette règle si le paramètre doit se trouver en raison de la compatibilité descendante.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, supprimez le paramètre inutilisé (une modification avec rupture) ou utilisez le paramètre dans le corps de méthode (une modification sans rupture).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle :

- D’un code précédemment livré pour lequel le correctif constituerait une modification avec rupture.

- Pour le `this` paramètre dans une méthode d’extension personnalisée pour <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=nameWithType>. Les fonctions dans le <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> classe sont statiques, il est donc pas nécessaire pour accéder à la `this` paramètre dans le corps de méthode.

## <a name="example"></a>Exemple

L’exemple suivant montre deux méthodes. Une méthode viole la règle et l’autre méthode satisfait la règle.

[!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]

## <a name="related-rules"></a>Règles associées

[CA1811 : Évitez le recours à code privé non appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812 : Évitez les classes internes non instanciées](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1804 : Supprimez les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)