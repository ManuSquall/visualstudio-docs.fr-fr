---
title: 'CA1819 : Les propriétés ne doivent pas retourner des tableaux'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9fd738b0c16ede4f71c001036546c335d8ca7186
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547036"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819 : Les propriétés ne doivent pas retourner des tableaux

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Catégorie|Microsoft. performance|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Une propriété retourne un tableau.

Par défaut, cette règle examine uniquement les propriétés et les types visibles de l’extérieur, mais elle peut [être configurée](#configurability).

## <a name="rule-description"></a>Description de la règle

Les tableaux retournés par les propriétés ne sont pas protégés en écriture, même si la propriété est en lecture seule. Pour protéger le tableau de toute falsification, la propriété doit retourner une copie du tableau. En règle générale, les utilisateurs ne comprennent pas les conséquences néfastes sur les performances de l’appel d’une telle propriété. Plus précisément, ils peuvent utiliser la propriété en tant que propriété indexée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, définissez la propriété sur une méthode ou modifiez la propriété pour retourner une collection.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Vous pouvez supprimer un avertissement déclenché pour une propriété d’un attribut dérivé de la <xref:System.Attribute> classe. Les attributs peuvent contenir des propriétés qui retournent des tableaux, mais ne peuvent pas contenir de propriétés qui retournent des collections.

Vous pouvez supprimer l’avertissement si la propriété fait partie d’une classe d' [objets transfert de données (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10)) .

Sinon, ne supprimez pas un avertissement de cette règle.

## <a name="configurability"></a>Configurabilité

Si vous exécutez cette règle à partir d' [analyseurs FxCop](install-fxcop-analyzers.md) (et non avec l’analyse héritée), vous pouvez configurer les parties de votre code base sur lesquelles exécuter cette règle, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet:

```ini
dotnet_code_quality.ca1819.api_surface = private, internal
```

Vous pouvez configurer cette option uniquement pour cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (performances). Pour plus d’informations, consultez [configurer les analyseurs FxCop](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Exemple de violation

L’exemple suivant montre une propriété qui enfreint cette règle:

[!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
[!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]

Pour corriger une violation de cette règle, définissez la propriété sur une méthode ou modifiez la propriété pour retourner une collection au lieu d’un tableau.

### <a name="change-the-property-to-a-method"></a>Remplacez la valeur de la propriété par une méthode

L’exemple suivant résout la violation en remplaçant la propriété par une méthode:

[!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
[!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]

### <a name="change-the-property-to-return-a-collection"></a>Modifier la propriété pour retourner une collection

L’exemple suivant résout la violation en modifiant la propriété pour retourner <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>un:

[!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
[!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]

## <a name="allow-users-to-modify-a-property"></a>Autoriser les utilisateurs à modifier une propriété

Vous souhaiterez peut-être autoriser le consommateur de la classe à modifier une propriété. L’exemple suivant illustre une propriété en lecture/écriture qui enfreint cette règle:

[!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
[!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]

L’exemple suivant résout la violation en modifiant la propriété pour retourner <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>un:

[!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
[!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]

## <a name="related-rules"></a>Règles associées

- [CA1024 Utiliser les propriétés lorsque cela est approprié](../code-quality/ca1024-use-properties-where-appropriate.md)