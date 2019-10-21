---
title: 'CA1819 : les propriétés ne doivent pas retourner des tableaux | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5c85efc3e601eb9e0d887043c50b30587e51321e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668377"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819 : Les propriétés ne doivent pas retourner des tableaux
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Category|Microsoft. performance|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une propriété publique ou protégée dans un type public retourne un tableau.

## <a name="rule-description"></a>Description de la règle
 Les tableaux retournés par les propriétés ne sont pas protégés en écriture, même si la propriété est en lecture seule. Pour protéger le tableau de toute falsification, la propriété doit retourner une copie du tableau. En général, les utilisateurs ne comprennent l'incidence négative en matière de performances de l'appel à une telle propriété. Plus précisément, ils peuvent utiliser la propriété en tant que propriété indexée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, définissez la propriété sur une méthode ou modifiez la propriété pour retourner une collection.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Les attributs peuvent contenir des propriétés qui retournent des tableaux, mais ne peuvent pas contenir de propriétés qui retournent des collections. Vous pouvez supprimer un avertissement déclenché pour une propriété d’un attribut dérivé de [System. Attribute] (<!-- TODO: review code entity reference <xref:assetId:///System.Attribute?qualifyHint=False&amp;autoUpgrade=True>  -->type. Sinon, ne supprimez pas un avertissement de cette règle.

## <a name="example-violation"></a>Exemple de violation

### <a name="description"></a>Description
 L’exemple suivant montre une propriété qui ne respecte pas cette règle.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/cs/FxCop.Performance.PropertyArrayViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/vb/FxCop.Performance.PropertyArrayViolation.vb#1)]

### <a name="comments"></a>Comments
 Pour corriger une violation de cette règle, définissez la propriété sur une méthode ou modifiez la propriété pour retourner une collection au lieu d’un tableau.

## <a name="change-the-property-to-a-method-example"></a>Remplacer la propriété par un exemple de méthode

### <a name="description"></a>Description
 L’exemple suivant résout la violation en remplaçant la propriété par une méthode.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/cs/FxCop.Performance.PropertyArrayFixedMethod.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/vb/FxCop.Performance.PropertyArrayFixedMethod.vb#1)]

## <a name="return-a-collection-example"></a>Retourner un exemple de collection

### <a name="description"></a>Description
 L’exemple suivant résout la violation en modifiant la propriété pour retourner un

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>.,

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/cs/FxCop.Performance.PropertyArrayFixedCollection.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/vb/FxCop.Performance.PropertyArrayFixedCollection.vb#1)]

## <a name="allowing-users-to-modify-a-property"></a>Autoriser les utilisateurs à modifier une propriété

### <a name="description"></a>Description
 Vous souhaiterez peut-être autoriser le consommateur de la classe à modifier une propriété. L’exemple suivant illustre une propriété en lecture/écriture qui ne respecte pas cette règle.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/cs/FxCop.Performance.PropertyModifyViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/vb/FxCop.Performance.PropertyModifyViolation.vb#1)]

### <a name="comments"></a>Comments
 L’exemple suivant résout la violation en modifiant la propriété pour retourner un <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/cs/FxCop.Performance.PropertyModifyFixed.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/vb/FxCop.Performance.PropertyModifyFixed.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1024 : Utilisez des propriétés quand c’est approprié](../code-quality/ca1024-use-properties-where-appropriate.md)
