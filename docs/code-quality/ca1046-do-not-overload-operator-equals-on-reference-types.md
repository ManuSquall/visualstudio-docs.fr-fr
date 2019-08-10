---
title: "CA1046 : Ne pas surcharger l'opérateur égal à sur les types référence"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d765bfda87fe184256304b86f145f4f02adb7db6
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922627"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046 : Ne pas surcharger l'opérateur égal à sur les types référence

|||
|-|-|
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Catégorie|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Un type référence public ou imbriqué est surchargé par l’opérateur d’égalité.

## <a name="rule-description"></a>Description de la règle
Pour les types référence, l'implémentation par défaut de l'opérateur d'égalité est presque toujours correcte. Par défaut, deux références sont égales uniquement si elles pointent sur le même objet.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, supprimez l’implémentation de l’opérateur d’égalité.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle lorsque le type de référence se comporte comme un type valeur intégré. S’il est judicieux d’effectuer une addition ou une soustraction sur des instances du type, il est probablement correct d’implémenter l’opérateur d’égalité et de supprimer la violation.

## <a name="example"></a>Exemples
L’exemple suivant illustre le comportement par défaut lors de la comparaison de deux références.

[!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]

## <a name="example"></a>Exemple

L’application suivante compare certaines références.

[!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]

Cet exemple génère la sortie suivante :

```txt
a = new (2,2) and b = new (2,2) are equal? No
c and a are equal? Yes
b and a are == ? No
c and a are == ? Yes
```

## <a name="related-rules"></a>Règles associées

[CA1013 Surchargez l’opérateur égal lors de la surcharge de l’ajout et de la soustraction](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Opérateurs d’égalité](/dotnet/standard/design-guidelines/equality-operators)