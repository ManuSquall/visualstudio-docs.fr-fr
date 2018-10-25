---
title: 'CA1815 : Remplacez equals et l’opérateur égal à sur les types valeur | Microsoft Docs'
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
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3868e5e1e78fd5640e9a2b55b133a9c6e0b47816
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912602"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815 : Remplacez Equals et l'opérateur égal à dans les types valeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Category|Microsoft.Performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type valeur public ne se substitue pas <xref:System.Object.Equals%2A?displayProperty=fullName>, ou n’implémente pas l’opérateur d’égalité (==). Cette règle ne vérifie pas les énumérations.

## <a name="rule-description"></a>Description de la règle
 Pour les types valeur, l’implémentation héritée de <xref:System.Object.Equals%2A> utilise la bibliothèque Reflection et compare le contenu de tous les champs. Le processus de réflexion sollicite fortement les ressources informatiques et la comparaison de chaque champ à la recherche d'une égalité peut s'avérer inutile. Si vous prévoyez que les utilisateurs à comparer ou trier des instances, ou les utilisez en tant que clés de table de hachage, votre type valeur doit implémenter <xref:System.Object.Equals%2A>. Si votre langage de programmation prend en charge la surcharge des opérateurs, vous devez également fournir une implémentation des opérateurs d’égalité et d’inégalité.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, fournir une implémentation de <xref:System.Object.Equals%2A>. Si vous pouvez implémenter l’opérateur d’égalité.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si les instances du type valeur ne seront pas comparer à l’autre sans.

## <a name="example-of-a-violation"></a>Exemple de Violation

### <a name="description"></a>Description
 L’exemple suivant montre une structure (type valeur) qui enfreint cette règle.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsViolation/cs/FxCop.Performance.OverrideEqualsViolation.cs#1)]

## <a name="example-of-how-to-fix"></a>Exemple de correctif

### <a name="description"></a>Description
 L’exemple suivant résout la violation précédente en substituant <xref:System.ValueType.Equals%2A?displayProperty=fullName> et en implémentant les opérateurs d’égalité (==, ! =).

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsFixed/cs/FxCop.Performance.OverrideEqualsFixed.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA2224 : Remplacez Equals lors de la surcharge de l’opérateur égal](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226 : Les opérateurs doivent avoir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Object.Equals%2A?displayProperty=fullName>



