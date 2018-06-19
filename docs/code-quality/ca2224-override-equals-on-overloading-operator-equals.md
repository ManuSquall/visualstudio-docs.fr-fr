---
title: "CA2224 : Remplacez Equals au moment de surcharger l'opérateur égal"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8836644e109e37855aa79dc67b461591b273786
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921510"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224 : Remplacez Equals au moment de surcharger l'opérateur égal
|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type public implémente l’opérateur d’égalité, mais ne remplace pas <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 L’opérateur d’égalité est destinée à être un moyen pratique de point de vue syntaxique pour accéder aux fonctionnalités de la <xref:System.Object.Equals%2A> (méthode). Si vous implémentez l’opérateur d’égalité, sa logique doit être identique à celui de <xref:System.Object.Equals%2A>.

 Le compilateur c# émet un avertissement si votre code ne respecte pas cette règle.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, vous devez supprimer l’implémentation de l’opérateur d’égalité ou substituer <xref:System.Object.Equals%2A> et ont les deux méthodes retournent les mêmes valeurs. Si l’opérateur d’égalité n’introduit aucun comportement incohérent, vous pouvez corriger la violation en fournissant une implémentation de <xref:System.Object.Equals%2A> qui appelle le <xref:System.Object.Equals%2A> méthode dans la classe de base.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si l’opérateur d’égalité retourne la même valeur que l’implémentation héritée de <xref:System.Object.Equals%2A>. La section exemple inclut un type qui pourrait supprimer sans risque un avertissement de cette règle.

## <a name="examples-of-inconsistent-equality-definitions"></a>Exemples de définitions d’égalité incohérentes

### <a name="description"></a>Description
 L’exemple suivant montre un type avec des définitions d’égalité incohérentes. `BadPoint` Modifie la signification d’égalité en fournissant une implémentation personnalisée de l’opérateur d’égalité, mais ne remplace pas <xref:System.Object.Equals%2A> afin qu’il se comporte de façon identique.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

## <a name="example"></a>Exemple
 Le code suivant teste le comportement de `BadPoint`.

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]

 Cet exemple produit la sortie suivante.

 **a = ([0] 1,1) et b = ([1] 2,2) sont égaux ? Ne**
**un == b ? Ne**
**a1 et a sont égaux ? Oui**
**a1 == un ? Oui**
**b et b copie sont égaux ? Ne**
**b == bcopy ? Oui**
## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole cette règle techniquement, mais ne se comporte pas de façon incohérente.

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

## <a name="example"></a>Exemple
 Le code suivant teste le comportement de `GoodPoint`.

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]

 Cet exemple produit la sortie suivante.

 **a = (1,1) et b = (2,2) sont égaux ? Ne**
**un == b ? Ne**
**a1 et a sont égaux ? Oui**
**a1 == un ? Oui**
**b et b copie sont égaux ? Oui**
**b == bcopy ? Oui**
## <a name="class-example"></a>Exemple de classe

### <a name="description"></a>Description
 L’exemple suivant montre une classe (type référence) qui enfreint cette règle.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

## <a name="example"></a>Exemple
 L’exemple suivant résout la violation en substituant <xref:System.Object.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>Exemple de structure

### <a name="description"></a>Description
 L’exemple suivant montre une structure (type valeur) qui enfreint cette règle.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

## <a name="example"></a>Exemple
 L’exemple suivant résout la violation en substituant <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>Règles associées
 [CA1046 : Ne pas surcharger l’opérateur égal sur les types de référence](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225 : Les surcharges d’opérateur ont d’autres méthodes nommées](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226 : Les opérateurs doivent avoir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218 : Remplacez GetHashCode lors du remplacement de Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)