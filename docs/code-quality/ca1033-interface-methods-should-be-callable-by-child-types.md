---
title: "CA1033 : Les méthodes d'interface doivent pouvoir être appelées par les types enfants"
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c41b19d9d4a82e25223a9cf7b04034b37c3f45fb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
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
 Envisagez d’un type de base qui implémente explicitement une méthode d’interface publique. Un type qui dérive du type de base peut accéder à la méthode d’interface héritée uniquement par le biais d’une référence à l’instance actuelle (`this` dans c#) qui est effectué à l’interface. Si le type dérivé ré-implémente (explicitement) la méthode d’interface héritée, l’implémentation de base n’est plus est accessible. L’appel de la référence d’instance actuelle appelle l’implémentation dérivée ; Cela provoque la récursivité et un dépassement de capacité de pile.

 Cette règle ne signale pas d’une violation d’une implémentation explicite de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> lorsqu’elle est visible de l’extérieur `Close()` ou `System.IDisposable.Dispose(Boolean)` méthode est fournie.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, implémentez une nouvelle méthode qui expose les mêmes fonctionnalités et qui est visible par les types dérivés ou modifiez une implémentation non explicites. Si une modification avec rupture est acceptable, une alternative consiste à rendre le type sealed.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si une méthode extérieurement visible est la condition qui a les mêmes fonctionnalités mais un nom différent de la méthode implémentée explicitement.

## <a name="example"></a>Exemple
 L’exemple suivant présente un type, `ViolatingBase`, qui enfreint la règle et un type, `FixedBase`, qui illustre un correctif pour la violation.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]

## <a name="see-also"></a>Voir aussi
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)