---
title: "CA2225 : Les surcharges d'opérateur offrent d'autres méthodes nommées"
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8a1c7015421b686d47bfea4c3341ec76748f8ad
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873066"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225 : Les surcharges d'opérateur offrent d'autres méthodes nommées

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une surcharge d’opérateur a été détectée et la méthode de substitution nommée attendue est introuvable.

Par défaut, cette règle examine uniquement les types visibles de l’extérieur, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

Surcharge d’opérateur autorise l’utilisation de symboles pour représenter des calculs pour un type. Par exemple, un type qui surcharge le symbole plus (+) pour l’addition aurait en général, un membre de substitution nommé 'Add'. Le membre de substitution nommé donne accès à la même fonctionnalité que l’opérateur et est fourni pour les développeurs qui programment dans les langages qui ne prennent pas en charge les opérateurs surchargés.

Cette règle examine les opérateurs répertoriés dans le tableau suivant.

|C#|Visual Basic|C++|Autre nom|
|---------|------------------|-----------|--------------------|
|+ (binaire)|+|+ (binaire)|Ajouter|
|+=|+=|+=|Ajouter|
|&|and|&|BitwiseAnd|
|&=|Et =|&=|BitwiseAnd|
|&#124;|Ou|&#124;|BitwiseOr|
|&#124;=|Ou =|&#124;=|BitwiseOr|
|--|N/A|--|Décrémentation|
|/|/|/|Diviser|
|/=|/=|/=|Diviser|
|==|=|==|Equals|
|^|Xor|^|Xor|
|^=|Xor=|^=|Xor|
|>|>|>|Comparer|
|>=|>=|>=|Comparer|
|++|N/A|++|Incrémentation|
|<>|!=|Equals|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|Comparer|
|<=|<=|\<=|Comparer|
|&&|N/A|&&|LogicalAnd|
|&#124;&#124;|N/A|&#124;&#124;|LogicalOr|
|!|N/A|!|LogicalNot|
|%|Mod|%|Mod ou reste|
|%=|N/A|%=|Mod|
|* (binaire)|*|*|Multiplication|
|*=|N/A|*=|Multiplication|
|~|Ne convient pas|~|OnesComplement|
|>>|>>|>>|MAJ droite|
=|N/A|>>=|MAJ droite|
|-(binaire)|-(binaire)|-(binaire)|Soustraire|
|-=|N/A|-=|Soustraire|
|true|IsTrue|N/A|IsTrue (propriété)|
|-(unaire)|N/A|-|Negate|
|+ (unaire)|N/A|+|Signe plus|
|False|IsFalse|False|IsTrue (propriété)|

N/a == ne peut pas être surchargé dans la langue sélectionnée.

La règle vérifie également les opérateurs de cast implicites et explicites dans un type (`SomeType`) en recherchant les méthodes nommées `ToSomeType` et `FromSomeType`.

En C#, lorsqu’un opérateur binaire est surchargé, l’opérateur d’assignation correspondant, le cas échéant, est aussi implicitement surchargé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, implémentez la méthode alternative pour l’opérateur. Nommez-le à l’aide de l’autre nom recommandé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez pas un avertissement de cette règle si vous implémentez une bibliothèque partagée. Les applications peuvent ignorer un avertissement de cette règle.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```
dotnet_code_quality.ca2225.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (utilisation). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemple

L’exemple suivant définit une structure qui enfreint cette règle. Pour corriger l’exemple, ajoutez un public `Add(int x, int y)` méthode à la structure.

[!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]

## <a name="related-rules"></a>Règles associées

- [CA1046 : Ne pas surcharger l’opérateur égal sur les types référence](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2226 : Les opérateurs doivent contenir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)
- [CA2224 : Remplacez equals lors de la surcharge l’opérateur égal](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218 : Remplacez GetHashCode au moment de remplacer Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)