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
dev_langs:
- CSharp
ms.openlocfilehash: b4db3074d334fe32f95c4d1b8446921c4e4d47ba
ms.sourcegitcommit: 16175e0cea6af528e9ec76f0b94690faaf1bed30
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71481770"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225 : Les surcharges d'opérateur offrent d'autres méthodes nommées

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Catégorie|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une surcharge d’opérateur a été détectée et la méthode alternative nommée attendue est introuvable.

Par défaut, cette règle recherche uniquement les types visibles de l’extérieur, mais elle peut [être configurée](#configurability).

## <a name="rule-description"></a>Description de la règle

La surcharge d’opérateur autorise l’utilisation de symboles pour représenter les calculs d’un type. Par exemple, un type qui surcharge le symbole plus `+` pour l’addition aura généralement un autre membre nommé `Add`. Le membre de substitution nommé fournit l’accès aux mêmes fonctionnalités que l’opérateur. Il est fourni aux développeurs qui programment dans des langages qui ne prennent pas en charge les opérateurs surchargés.

Cette règle examine les éléments suivants :

- Les opérateurs de cast implicite et explicite dans un type en vérifiant les méthodes nommées `To<typename>` et `From<typename>`.

- Les opérateurs listés dans le tableau suivant :

|C#|Visual Basic|C++|Nom de la méthode de remplacement|
|-|-|-|-|
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
|^=|XOR =|^=|Xor|
|>|>|>|CompareTo ou compare|
|>=|>=|>=|CompareTo ou compare|
|++|N/A|++|Incrémentation|
|!=|<>|!=|Equals|
|<<|<<|<<|Maj|
|<<=|<<=|<<=|Maj|
|<|<|<|CompareTo ou compare|
|<=|<=|\<=|CompareTo ou compare|
|&&|N/A|&&|LogicalAnd|
|&#124;&#124;|N/A|&#124;&#124;|Logique|
|!|N/A|!|LogicalNot|
|%|Mod|%|Modulo ou modulo|
|%=|N/A|%=|Mod|
|* (binaire)|*|*|Multiplication|
|*=|N/A|*=|Multiplication|
|~|Ne convient pas|~|OnesComplement|
|>>|>>|>>|Maj droite|
=|N/A|>>=|Maj droite|
|-(binaire)|-(binaire)|-(binaire)|Soustraire|
|-=|N/A|-=|Soustraire|
|true|IsTrue|N/A|IsTrue (propriété)|
|-(unaire)|N/A|-|Negate|
|+ (unaire)|N/A|+|Protect|
|false|IsFalse|False|IsTrue (propriété)|

\* N/A signifie que l’opérateur ne peut pas être surchargé dans la langue sélectionnée.

> [!NOTE]
> Dans C#, lorsqu’un opérateur binaire est surchargé, l’opérateur d’assignation correspondant, le cas échéant, est également implicitement surchargé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, implémentez l’autre méthode pour l’opérateur. Nommez-le à l’aide du nom de remplacement recommandé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez pas un avertissement de cette règle si vous implémentez une bibliothèque partagée. Les applications peuvent ignorer un avertissement de cette règle.

## <a name="configurability"></a>Configurabilité

Si vous exécutez cette règle à partir d' [analyseurs FxCop](install-fxcop-analyzers.md) (et non avec l’analyse héritée), vous pouvez configurer les parties de votre code base sur lesquelles exécuter cette règle, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet :

```ini
dotnet_code_quality.ca2225.api_surface = private, internal
```

Vous pouvez configurer cette option uniquement pour cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (utilisation). Pour plus d’informations, consultez [configurer les analyseurs FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemple

L’exemple suivant définit une structure qui enfreint cette règle. Pour corriger l’exemple, ajoutez une méthode `Add(int x, int y)` publique à la structure.

[!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]

## <a name="related-rules"></a>Règles associées

- [CA1046 Ne pas surcharger l’opérateur égal à sur les types référence](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2226 Les opérateurs doivent avoir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)
- [CA2224 Remplacer Equals lors de la surcharge de l’opérateur égal](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218 Substituez GetHashCode lors du remplacement d’égal](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)