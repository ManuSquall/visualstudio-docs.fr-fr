---
title: 'CA2233 : Les opérations ne doivent pas déborder'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93d4fc872f14a63eeec446d8e6d1f9a2c7acf7ff
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919303"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233 : Les opérations ne doivent pas déborder
|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode exécute une opération arithmétique et ne valide pas au préalable les opérandes pour empêcher un débordement.

## <a name="rule-description"></a>Description de la règle
 Opérations arithmétiques ne doivent pas être effectuées sans valider au préalable les opérandes pour vous assurer que le résultat de l’opération n’est pas en dehors de la plage de valeurs possibles pour les types de données impliqués. Selon le contexte d’exécution et les types de données impliqués, dépassement de capacité arithmétique peut engendrer un <xref:System.OverflowException?displayProperty=fullName> ou les bits les plus significatifs du résultat est ignoré.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, validez les opérandes avant d’effectuer l’opération.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si les valeurs possibles des opérandes ne provoquent jamais l’opération arithmétique de dépassement de capacité.

## <a name="example-of-a-violation"></a>Exemple de Violation

### <a name="description"></a>Description
 Une méthode dans l’exemple suivant manipule un entier qui viole cette règle. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] requiert le **supprimer** l’option de dépassement doit être désactivée pour ce déclenchement.

### <a name="code"></a>Code
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]

### <a name="comments"></a>Commentaires
 Si la méthode dans cet exemple est passée <xref:System.Int32.MinValue?displayProperty=fullName>, l’opération va de dépassement de capacité négatif. Cela entraîne le bit le plus significatif du résultat est ignorée. Le code suivant montre comment cela se produit.

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 [VB]

```
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

### <a name="output"></a>Sortie

```
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Résoudre avec Validation de paramètre d’entrée

### <a name="description"></a>Description
 L’exemple suivant résout la violation précédente en validant la valeur d’entrée.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]

## <a name="fix-with-a-checked-block"></a>Résoudre avec un bloc Checked

### <a name="description"></a>Description
 L’exemple suivant résout la violation précédente en encapsulant l’opération dans un bloc checked. Si l’opération provoque un dépassement de capacité, une <xref:System.OverflowException?displayProperty=fullName> sera levée.

 Notez que les blocs checked ne sont pas pris en charge dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Activer Checked dépassements arithmétiques
 Si vous activez checked dépassements arithmétiques en c#, il est équivalent à chaque opération entier dans un bloc checked d’habillage.

 **Pour allumer checked dépassements arithmétiques en c#**

1.  Dans **l’Explorateur de solutions**, avec le bouton droit de votre projet et choisissez **propriétés**.

2.  Sélectionnez l’onglet **Build**, puis cliquez sur **Avancé**.

3.  Sélectionnez **vérifier les dépassements arithmétiques** et cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi
 <xref:System.OverflowException?displayProperty=fullName> [Opérateurs c#](/dotnet/csharp/language-reference/operators/index) [Checked et Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)