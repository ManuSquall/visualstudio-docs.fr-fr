---
title: "CA1033 : Les méthodes d'interface doivent pouvoir être appelées par les types enfants"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10db644fe4cf65a7336ef8bd50dcf62e072e1c46
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922953"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033 : Les méthodes d'interface doivent pouvoir être appelées par les types enfants

|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Un type unsealed visible de l'extérieur fournit une implémentation de méthode explicite d'une interface publique mais ne fournit aucune méthode de substitution visible de l'extérieur de même nom.

## <a name="rule-description"></a>Description de la règle
Prenons l’exemple d’un type de base qui implémente explicitement une méthode d’interface publique. Un type qui dérive du type de base peut accéder à la méthode d’interface héritée uniquement par le biais d’une`this` référence C#à l’instance actuelle (dans) qui est castée en interface. Si le type dérivé réimplémente (explicitement) la méthode d’interface héritée, l’implémentation de base ne peut plus être accédée. L’appel via la référence d’instance actuelle appellera l’implémentation dérivée; Cela provoque une récurrence et un dépassement de capacité de la pile.

Cette règle ne signale pas de violation pour une implémentation explicite <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> de lorsqu’une méthode ou `Close()` `System.IDisposable.Dispose(Boolean)` une méthode visible de l’extérieur est fournie.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, implémentez une nouvelle méthode qui expose les mêmes fonctionnalités et qui est visible pour les types dérivés ou passez à une implémentation non explicite. Si une modification avec rupture est acceptable, une alternative consiste à rendre le type sealed.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle si une méthode visible de l’extérieur est fournie et a les mêmes fonctionnalités, mais avec un nom différent de celui de la méthode implémentée explicitement.

## <a name="example"></a>Exemple
L’exemple suivant illustre un type, `ViolatingBase`, qui enfreint la règle et un type, `FixedBase`, qui affiche un correctif pour la violation.

[!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]

## <a name="see-also"></a>Voir aussi
[Interfaces](/dotnet/csharp/programming-guide/interfaces/index)