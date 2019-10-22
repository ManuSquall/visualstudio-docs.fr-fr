---
title: 'CA1815 : remplacez Equals et l’opérateur égal à dans les types valeur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bb9574eb6e9f907d4b1fcc74f50fca0e7db85253
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668403"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815 : Remplacez Equals et l'opérateur égal à dans les types valeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Category|Microsoft. performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type valeur public ne remplace pas <xref:System.Object.Equals%2A?displayProperty=fullName>, ou n’implémente pas l’opérateur d’égalité (= =). Cette règle ne vérifie pas les énumérations.

## <a name="rule-description"></a>Description de la règle
 Pour les types valeur, l’implémentation héritée de <xref:System.Object.Equals%2A> utilise la bibliothèque de réflexion et compare le contenu de tous les champs. Le processus de réflexion sollicite fortement les ressources informatiques et la comparaison de chaque champ à la recherche d'une égalité peut s'avérer inutile. Si vous vous attendez à ce que les utilisateurs soient en mesure de comparer ou de trier des instances, ou de les utiliser en tant que clés de table de hachage, votre type valeur doit implémenter <xref:System.Object.Equals%2A>. Si votre langage de programmation prend en charge la surcharge des opérateurs, vous devez également fournir une implémentation des opérateurs d’égalité et d’inégalité.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, fournissez une implémentation de <xref:System.Object.Equals%2A>. Si vous le pouvez, implémentez l’opérateur d’égalité.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si les instances du type valeur ne seront pas comparées les unes aux autres.

## <a name="example-of-a-violation"></a>Exemple de violation

### <a name="description"></a>Description
 L’exemple suivant illustre une structure (type valeur) qui enfreint cette règle.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsViolation/cs/FxCop.Performance.OverrideEqualsViolation.cs#1)]

## <a name="example-of-how-to-fix"></a>Exemple de résolution

### <a name="description"></a>Description
 L’exemple suivant résout la violation précédente en remplaçant <xref:System.ValueType.Equals%2A?displayProperty=fullName> et en implémentant les opérateurs d’égalité (= =, ! =).

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsFixed/cs/FxCop.Performance.OverrideEqualsFixed.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA2224 : Remplacez Equals lors de la surcharge de l’opérateur égal](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226 : Les opérateurs doivent avoir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Object.Equals%2A?displayProperty=fullName>
