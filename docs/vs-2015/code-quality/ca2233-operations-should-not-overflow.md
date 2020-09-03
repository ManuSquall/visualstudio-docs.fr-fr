---
title: 'CA2233 : les opérations ne doivent pas déborder | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: eff09fb8f4423560c4681c94507d909f5864c69e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545234"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233 : Les opérations ne doivent pas déborder
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Une méthode effectue une opération arithmétique et ne valide pas les opérandes au préalable pour empêcher un dépassement de capacité.

## <a name="rule-description"></a>Description de la règle
 Les opérations arithmétiques ne doivent pas être effectuées sans valider au préalable les opérandes pour s’assurer que le résultat de l’opération n’est pas en dehors de la plage de valeurs possibles pour les types de données impliqués. En fonction du contexte d’exécution et des types de données impliqués, le dépassement de capacité arithmétique peut entraîner la suppression de l’un <xref:System.OverflowException?displayProperty=fullName> ou des bits les plus significatifs du résultat.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, validez les opérandes avant d’effectuer l’opération.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si les valeurs possibles des opérandes ne provoquent jamais le dépassement de capacité de l’opération arithmétique.

## <a name="example-of-a-violation"></a>Exemple de violation

### <a name="description"></a>Description
 Une méthode dans l’exemple suivant manipule un entier qui enfreint cette règle. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nécessite la désactivation de l’option **supprimer** le dépassement sur les entiers pour qu’elle soit déclenchée.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>Commentaires
 Si la méthode dans cet exemple est passée <xref:System.Int32.MinValue?displayProperty=fullName> , l’opération est dépassée. Le bit le plus significatif du résultat est alors ignoré. Le code suivant montre comment cela se produit.

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 VBScript

```
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

### <a name="output"></a>Output

```
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Correction de la validation des paramètres d’entrée

### <a name="description"></a>Description
 L’exemple suivant résout la violation précédente en validant la valeur de l’entrée.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>Corriger avec un bloc Checked

### <a name="description"></a>Description
 L’exemple suivant résout la violation précédente en encapsulant l’opération dans un bloc Checked. Si l’opération provoque un dépassement de capacité, une <xref:System.OverflowException?displayProperty=fullName> est levée.

 Notez que les blocs vérifiés ne sont pas pris en charge dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Activer le dépassement de capacité positif/négatif activé
 Si vous activez la case à cocher de dépassement de capacité positif ou de dépassement de capacité négatif en C#, cela revient à encapsuler chaque opération entière dans un bloc Checked.

 **Pour activer le dépassement de capacité positif ou négatif de la case à cocher en C #**

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur votre projet et choisissez **Propriétés**.

2. Sélectionnez l’onglet **Build**, puis cliquez sur **Avancé**.

3. Sélectionnez **vérifier les dépassements de capacité arithmétiques/négatifs** , puis cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi
 <xref:System.OverflowException?displayProperty=fullName>[Opérateurs C#](https://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43) [activés et désactivés](https://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e)
