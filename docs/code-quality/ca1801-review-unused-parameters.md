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
ms.openlocfilehash: 6de48bf273a5c93afcd14e7bab2c5d4c4c4b5a7c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233823"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801 : Passez en revue les paramètres inutilisés

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|Catégorie|Microsoft.Usage|
|Modification avec rupture|Sans rupture : si le membre n’est pas visible à l’extérieur de l’assembly, quelle que soit la modification que vous apportez.<br /><br /> Sans rupture : Si vous modifiez le membre pour utiliser le paramètre dans son corps.<br /><br /> Avec rupture : Si vous supprimez le paramètre et qu’il est visible à l’extérieur de l’assembly.|

## <a name="cause"></a>Cause

Une signature de méthode comprend un paramètre qui n’est pas utilisé dans le corps de la méthode.

Cette règle n’examine pas les types de méthodes suivants :

- Méthodes référencées par un délégué.

- Méthodes utilisées comme gestionnaires d’événements.

- Méthodes déclarées avec `abstract` le`MustOverride` modificateur (en Visual Basic).

- Méthodes déclarées avec `virtual` le`Overridable` modificateur (en Visual Basic).

- Méthodes déclarées avec `override` le`Overrides` modificateur (en Visual Basic).

- Les méthodes déclarées `extern` avec`Declare` le modificateur (instruction dans Visual Basic).

Si vous utilisez les [analyseurs FxCop](install-fxcop-analyzers.md), cette règle ne signale pas les paramètres nommés avec le symbole de [rejet](/dotnet/csharp/discards), par exemple, `_`, `_1` et `_2`. Cela réduit le bruit d’avertissement sur les paramètres requis pour les spécifications de signature, par exemple, une méthode utilisée comme délégué, un paramètre avec des attributs spéciaux ou un paramètre dont la valeur est implicitement accessible au moment de l’exécution par un Framework, mais n’est pas référencée dans code.

## <a name="rule-description"></a>Description de la règle

Passez en revue les paramètres des méthodes non virtuelles qui ne sont pas utilisées dans le corps de la méthode pour vous assurer qu’il n’existe pas d’inexactitude pour y accéder. Les paramètres inutilisés entraînent des coûts de maintenance et de performances.

Parfois, une violation de cette règle peut pointer vers un bogue d’implémentation dans la méthode. Par exemple, le paramètre doit avoir été utilisé dans le corps de la méthode. Supprimer les avertissements de cette règle si le paramètre doit exister en raison d’une compatibilité descendante.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, supprimez le paramètre inutilisé (une modification avec rupture) ou utilisez le paramètre dans le corps de la méthode (modification sans rupture).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle :

- Dans le code précédemment envoyé pour lequel le correctif serait une modification avec rupture.

- Pour le `this` paramètre dans une méthode d’extension personnalisée <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=nameWithType>pour. Les fonctions de la <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> classe étant statiques, il n’est pas nécessaire d’accéder `this` au paramètre dans le corps de la méthode.

## <a name="example"></a>Exemple

L’exemple suivant illustre deux méthodes. Une méthode viole la règle et l’autre méthode remplit la règle.

[!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]

## <a name="related-rules"></a>Règles associées

[CA1811 Éviter le code privé qui n’a pas été appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812 Évitez les classes internes non instanciées](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1804 Supprimer les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)
