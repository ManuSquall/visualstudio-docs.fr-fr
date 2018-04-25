---
title: "CA1013 : Surchargez l'opérateur égal lors de la surcharge de l'opérateur d'addition et de soustraction"
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7fd43cc3077c037b70eaa8107563bd8f40b6a096
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013 : Surchargez l'opérateur égal lors de la surcharge de l'opérateur d'addition et de soustraction
|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé implémente les opérateurs d'addition ou de soustraction sans implémenter l'opérateur d'égalité.

## <a name="rule-description"></a>Description de la règle
 Lorsque les instances d’un type peuvent être combinées à l’aide des opérations telles que l’addition et la soustraction, vous devez presque toujours définir l’égalité retourne `true` pour les deux instances qui ont les mêmes valeurs constituantes.

 Vous ne pouvez pas utiliser l’opérateur d’égalité par défaut dans une implémentation surchargée de l’opérateur d’égalité. Cela provoque un dépassement de capacité de pile. Pour implémenter l’opérateur d’égalité, utilisez la méthode Object.Equals dans votre implémentation. Lisez l'exemple suivant.

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, implémentez l’opérateur d’égalité afin qu’il soit mathématiquement cohérent avec les opérateurs d’addition et soustraction.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle lorsque l’implémentation par défaut de l’opérateur d’égalité fournit le comportement correct pour le type.

## <a name="example"></a>Exemple
 L’exemple suivant définit un type (`BadAddableType`) qui enfreint cette règle. Ce type doit implémenter l’opérateur d’égalité pour rendre les deux instances qui ont les mêmes valeurs de champ à tester `true` d’égalité. Le type `GoodAddableType` affiche l’implémentation corrigée. Notez que ce type implémente l’opérateur d’inégalité également et remplace <xref:System.Object.Equals%2A> pour satisfaire d’autres règles. Une implémentation complète implémenterait également <xref:System.Object.GetHashCode%2A>.

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]

## <a name="example"></a>Exemple
 L’exemple suivant teste l’égalité à l’aide d’instances des types qui ont été définis précédemment dans cette rubrique pour illustrer la valeur par défaut et le comportement correct pour l’opérateur d’égalité.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]

 Cet exemple produit la sortie suivante.

 **Type incorrect : {2,2} {2,2} sont égaux ? Ne**
**bon type : {3,3} {3,3} sont égaux ? Oui**
**bon type : {3,3} {3,3} sont == ?   Oui**
**type incorrect : {2,2} {9,9} sont égaux ? Ne**
**bon type : {3,3} {9,9} sont == ?   Aucun**
## <a name="see-also"></a>Voir aussi
 [Opérateurs d’égalité](/dotnet/standard/design-guidelines/equality-operators)