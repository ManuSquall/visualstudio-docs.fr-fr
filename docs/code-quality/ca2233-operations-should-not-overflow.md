---
title: 'CA2233 : Les opérations ne doivent pas déborder'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7c07dde4c3b992db30c9fc72a0dfa01f0f13b31e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806600"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233 : Les opérations ne doivent pas déborder

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une méthode exécute une opération arithmétique et ne valide pas au préalable les opérandes pour empêcher un débordement.

## <a name="rule-description"></a>Description de la règle

Ne pas effectuer des opérations arithmétiques sans valider au préalable les opérandes pour vous assurer que le résultat de l’opération n’est pas en dehors de la plage de valeurs possibles pour les types de données impliqués. Selon le contexte d’exécution et les types de données impliquées, dépassement de capacité arithmétique peut engendrer un <xref:System.OverflowException?displayProperty=fullName> ou ignoré les bits les plus significatifs du résultat.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, validez les opérandes avant d’effectuer l’opération.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle si les valeurs possibles des opérandes ne provoquent jamais de dépassement de capacité de l’opération arithmétique.

## <a name="example-of-a-violation"></a>Exemple de violation

Une méthode dans l’exemple suivant manipule un entier qui enfreint cette règle. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nécessite le **supprimer** l’option de dépassement doit être désactivée pour cette option pour déclencher.

[!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
[!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]

Si la méthode dans cet exemple est passée <xref:System.Int32.MinValue?displayProperty=fullName>, l’opération provoquait le dépassement de capacité négatif. Par conséquent, le bit le plus significatif du résultat sont ignorés. Le code suivant montre comment cela se produit.

```csharp
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

```vb
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

Sortie :

```text
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Résoudre avec Validation de paramètre d’entrée

L’exemple suivant résout la violation précédente en validant la valeur d’entrée.

[!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
[!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]

## <a name="fix-with-a-checked-block"></a>Résoudre avec un bloc Checked

L’exemple suivant résout la violation précédente en encapsulant l’opération dans un bloc checked. Si l’opération provoque un dépassement de capacité, une <xref:System.OverflowException?displayProperty=fullName> sera levée.

Blocs vérifiés ne sont pas pris en charge dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].

[!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Activer Checked arithmétiques dépassement de capacité positifs et négatifs

Si vous activez checked arithmétiques dépassement de capacité positifs et négatifs en c#, il est équivalent à chaque opération entière d’habillage dans un bloc checked.

Pour activer checked arithmétiques dépassement de capacité positifs et négatifs en c# :

1. Dans **l’Explorateur de solutions**, cliquez sur votre projet et choisissez **propriétés**.

2. Sélectionnez l’onglet **Build**, puis cliquez sur **Avancé**.

3. Sélectionnez **vérifier les dépassements arithmétiques** et cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

- <xref:System.OverflowException?displayProperty=fullName>
- [Opérateurs C#](/dotnet/csharp/language-reference/operators/index)
- [Checked et unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)