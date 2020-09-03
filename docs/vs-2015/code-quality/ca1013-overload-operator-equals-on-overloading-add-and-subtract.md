---
title: 'Ca1013 : surchargez l’opérateur égal lors de la surcharge de l’opérateur Add et Subtract | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2304b78073b806dfc4aec9686f061d946b379ded
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545416"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013 : Surchargez l'opérateur égal lors de la surcharge de l'opérateur d'addition et de soustraction
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Un type public ou protégé implémente les opérateurs d'addition ou de soustraction sans implémenter l'opérateur d'égalité.

## <a name="rule-description"></a>Description de la règle
 Lorsque des instances d’un type peuvent être combinées à l’aide d’opérations telles que l’addition et la soustraction, vous devez presque toujours définir l’égalité pour retourner les `true` deux instances qui ont les mêmes valeurs constitutives.

 Vous ne pouvez pas utiliser l’opérateur d’égalité par défaut dans une implémentation surchargée de l’opérateur d’égalité. Cela entraîne un dépassement de capacité de la pile. Pour implémenter l’opérateur d’égalité, utilisez la méthode Object. Equals dans votre implémentation. Consultez l’exemple qui suit.

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
 Pour corriger une violation de cette règle, implémentez l’opérateur d’égalité afin qu’il soit mathématiquement cohérent avec les opérateurs d’addition et de soustraction.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle lorsque l’implémentation par défaut de l’opérateur d’égalité fournit le comportement correct pour le type.

## <a name="example"></a>Exemple
 L’exemple suivant définit un type ( `BadAddableType` ) qui enfreint cette règle. Ce type doit implémenter l’opérateur d’égalité pour que deux instances qui ont les mêmes valeurs de champ testent l' `true` égalité. Le type `GoodAddableType` affiche l’implémentation corrigée. Notez que ce type implémente également l’opérateur d’inégalité et les remplacements <xref:System.Object.Equals%2A> pour satisfaire d’autres règles. Une implémentation complète implémenterait également <xref:System.Object.GetHashCode%2A> .

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>Exemple
 L’exemple suivant teste l’égalité en utilisant des instances des types précédemment définis dans cette rubrique pour illustrer le comportement par défaut et correct pour l’opérateur d’égalité.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 Cet exemple produit la sortie suivante.

 **Type incorrect : {2,2} {2,2} sont égaux ? Aucun** 
 **type correct : {3,3} {3,3} sont égaux ? Oui**, 
 **type correct : {3,3} {3,3} = = ?   Oui**, 
 **type incorrect : {2,2} {9,9} sont-ils égaux ? Aucun** 
 **type correct : {3,3} {9,9} est = = ?   Non**
## <a name="see-also"></a>Voir aussi
 [Opérateurs d’égalité](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
