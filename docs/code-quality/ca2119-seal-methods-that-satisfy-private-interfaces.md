---
title: 'CA2119 : Scellez les méthodes qui satisfont les interfaces privées'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4c019e98e7f1311b6521dff563cb8e7bb0a2356e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62544014"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119 : Scellez les méthodes qui satisfont les interfaces privées

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public pouvant être hérité fournit une implémentation de méthode substituable d’une `internal` (`Friend` en Visual Basic) interface.

## <a name="rule-description"></a>Description de la règle
 Méthodes d’interface ont une accessibilité publique, qui ne peut pas être modifiée par le type d’implémentation. Une interface interne crée un contrat qui n’est pas destiné à être implémentée en dehors de l’assembly qui définit l’interface. Un type public qui implémente une méthode d’une interface interne à l’aide de la `virtual` (`Overridable` en Visual Basic) modificateur permet à la méthode être substituée par un type dérivé qui est en dehors de l’assembly. Si un deuxième type dans l’assembly de définition appelle la méthode et attend un contrat interne uniquement, le comportement peut être compromis lorsque, au lieu de cela, la méthode substituée dans l’assembly externe est exécutée. Cette opération crée une faille de sécurité.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, empêchez la méthode d’être substituée en dehors de l’assembly en utilisant l’une des opérations suivantes :

- Créez le type déclarant `sealed` (`NotInheritable` en Visual Basic).

- Modifiez l’accessibilité du type déclarant à `internal` (`Friend` en Visual Basic).

- Supprimez tous les constructeurs publics du type déclarant.

- Implémentez la méthode sans utiliser le `virtual` modificateur.

- Implémentez explicitement la méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si, après un examen minutieux, aucun problème de sécurité qui peut être exploitable que si la méthode est substituée en dehors de l’assembly.

## <a name="example-1"></a>Exemple 1
 L’exemple suivant illustre un type, `BaseImplementation`, qui enfreint cette règle.

 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]

## <a name="example-2"></a>Exemple 2
 L’exemple suivant exploite l’implémentation de méthode virtuelle de l’exemple précédent.

 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]

## <a name="see-also"></a>Voir aussi

- [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)
- [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)