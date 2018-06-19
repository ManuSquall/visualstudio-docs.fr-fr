---
title: 'CA1819 : Les propriétés ne doivent pas retourner des tableaux'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2aca450bba47b73c8fa2e5e8e1246e864a1293c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917729"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819 : Les propriétés ne doivent pas retourner des tableaux
|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Category|Microsoft.Performance|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une propriété publique ou protégée dans un type public retourne un tableau.

## <a name="rule-description"></a>Description de la règle
 Les tableaux retournés par les propriétés ne sont pas protégés en écriture, même si la propriété est en lecture seule. Pour protéger le tableau de toute falsification, la propriété doit retourner une copie du tableau. En général, les utilisateurs ne comprennent l'incidence négative en matière de performances de l'appel à une telle propriété. Plus précisément, ils peuvent utiliser la propriété comme une propriété indexée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, rendez la propriété à une méthode, ou bien modifier la propriété pour retourner une collection.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Les attributs peuvent contenir des propriétés qui retournent des tableaux, mais ne peut pas contenir des propriétés qui retournent des collections. Vous pouvez supprimer un avertissement est déclenché pour une propriété d’un attribut qui est dérivé de la <xref:System.Attribute> classe. Sinon, ne supprimez aucun avertissement de cette règle.

## <a name="example-violation"></a>Exemple de Violation

### <a name="description"></a>Description
 L’exemple suivant illustre une propriété qui enfreint cette règle.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]

### <a name="comments"></a>Commentaires
 Pour corriger une violation de cette règle, rendez la propriété à une méthode, ou bien modifier la propriété pour retourner une collection au lieu d’un tableau.

## <a name="change-the-property-to-a-method-example"></a>Modifiez la propriété à un exemple de méthode

### <a name="description"></a>Description
 L’exemple suivant résout la violation en modifiant la propriété à une méthode.

### <a name="code"></a>Code
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]

## <a name="return-a-collection-example"></a>Retourner un exemple de Collection

### <a name="description"></a>Description
 L’exemple suivant résout la violation en modifiant la propriété à retourner un

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]

## <a name="allowing-users-to-modify-a-property"></a>Ce qui permet aux utilisateurs de modifier une propriété

### <a name="description"></a>Description
 Vous pouvez souhaiter permettre au consommateur de la classe modifier une propriété. L’exemple suivant montre une propriété en lecture/écriture qui enfreint cette règle.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]

### <a name="comments"></a>Commentaires
 L’exemple suivant résout la violation en modifiant la propriété à retourner un <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>.

### <a name="code"></a>Code
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]

## <a name="related-rules"></a>Règles associées
 [CA1024 : Utilisez des propriétés quand c’est approprié](../code-quality/ca1024-use-properties-where-appropriate.md)