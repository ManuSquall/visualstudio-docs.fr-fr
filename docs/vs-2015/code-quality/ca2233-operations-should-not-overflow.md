---
title: 'CA2233 : Les opérations ne doivent pas déborder | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5f6690f6577d936757ae3bbe8b725b4434b6bee1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836656"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233 : Les opérations ne doivent pas déborder
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode exécute une opération arithmétique et ne valide pas au préalable les opérandes pour empêcher un débordement.

## <a name="rule-description"></a>Description de la règle
 Opérations arithmétiques ne doivent pas être effectuées sans valider au préalable les opérandes pour vous assurer que le résultat de l’opération n’est pas en dehors de la plage de valeurs possibles pour les types de données impliqués. Selon le contexte d’exécution et les types de données impliquées, dépassement de capacité arithmétique peut engendrer un <xref:System.OverflowException?displayProperty=fullName> ou ignoré les bits les plus significatifs du résultat.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, validez les opérandes avant d’effectuer l’opération.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si les valeurs possibles des opérandes ne provoquent jamais de dépassement de capacité de l’opération arithmétique.

## <a name="example-of-a-violation"></a>Exemple de Violation

### <a name="description"></a>Description
 Une méthode dans l’exemple suivant manipule un entier qui enfreint cette règle. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nécessite le **supprimer** l’option de dépassement doit être désactivée pour cette option pour déclencher.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>Commentaires
 Si la méthode dans cet exemple est passée <xref:System.Int32.MinValue?displayProperty=fullName>, l’opération provoquait le dépassement de capacité négatif. Par conséquent, le bit le plus significatif du résultat sont ignorés. Le code suivant montre comment cela se produit.

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
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>Résoudre avec un bloc Checked

### <a name="description"></a>Description
 L’exemple suivant résout la violation précédente en encapsulant l’opération dans un bloc checked. Si l’opération provoque un dépassement de capacité, une <xref:System.OverflowException?displayProperty=fullName> sera levée.

 Notez que les blocs vérifiés ne sont pas pris en charge dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Activer Checked arithmétiques dépassement de capacité positifs et négatifs
 Si vous activez checked arithmétiques dépassement de capacité positifs et négatifs en c#, il est équivalent à chaque opération entière d’habillage dans un bloc checked.

 **Pour allumer checked arithmétiques dépassement de capacité positifs et négatifs en c#**

1.  Dans **l’Explorateur de solutions**, cliquez sur votre projet et choisissez **propriétés**.

2.  Sélectionnez l’onglet **Build**, puis cliquez sur **Avancé**.

3.  Sélectionnez **vérifier les dépassements arithmétiques** et cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi
 <xref:System.OverflowException?displayProperty=fullName> [Opérateurs c#](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43) [Checked et Unchecked](http://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e)



