---
title: 'Ca1046 : ne pas surcharger l’opérateur égal à sur les types référence | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 118c29473db09d5ed0a4fa447e27e593a88f98b3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546755"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046 : Ne pas surcharger l'opérateur égal à sur les types référence
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type référence public ou imbriqué est surchargé par l’opérateur d’égalité.

## <a name="rule-description"></a>Description de la règle
 Pour les types référence, l'implémentation par défaut de l'opérateur d'égalité est presque toujours correcte. Par défaut, deux références sont égales uniquement si elles pointent sur le même objet.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez l’implémentation de l’opérateur d’égalité.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle lorsque le type de référence se comporte comme un type valeur intégré. S’il est judicieux d’effectuer une addition ou une soustraction sur des instances du type, il est probablement correct d’implémenter l’opérateur d’égalité et de supprimer la violation.

## <a name="example"></a>Exemple
 L’exemple suivant illustre le comportement par défaut lors de la comparaison de deux références.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefTypesNoEqualityOp/cs/FxCop.Design.RefTypesNoEqualityOp.cs#1)]

## <a name="example"></a>Exemple
 L’application suivante compare certaines références.

 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefTypesNoEqualityOp/cs/FxCop.Design.TestRefTypesNoEqualityOp.cs#1)]

 Cet exemple produit la sortie suivante.

 **a = New (2, 2) et b = New (2, 2) sont égaux ? Aucun** 
 **c et un n’est égal ? Oui** 
 **b et a sont = = ? Aucun** 
 **c et un ne sont = = ? Oui**
## <a name="related-rules"></a>Règles associées
 [CA1013 : Surchargez l'opérateur égal lors de la surcharge de l'opérateur d'addition et de soustraction](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Object.Equals%2A?displayProperty=fullName>[Opérateurs d’égalité](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
