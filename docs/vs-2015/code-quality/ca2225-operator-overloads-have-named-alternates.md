---
title: 'CA2225 : les surcharges d’opérateur ont des alternatives nommées | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2dc43e92b92b6f963900057a76dfe88e38a3638f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545221"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225 : Les surcharges d'opérateur offrent d'autres méthodes nommées
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Une surcharge d'opérateur a été détectée, et la méthode de substitution nommée attendue n'a pas été trouvée.

## <a name="rule-description"></a>Description de la règle
 La surcharge d’opérateur autorise l’utilisation de symboles pour représenter les calculs d’un type. Par exemple, un type qui surcharge le symbole plus (+) en plus de l’ajout aurait généralement un autre membre nommé’Add'. Le membre de substitution nommé fournit l’accès aux mêmes fonctionnalités que l’opérateur et est fourni aux développeurs qui programment dans des langages qui ne prennent pas en charge les opérateurs surchargés.

 Cette règle examine les opérateurs listés dans le tableau suivant.

|C#|Visual Basic|C++|Autre nom|
|---------|------------------|-----------|--------------------|
|+ (binaire)|+|+ (binaire)|Ajouter|
|+=|+=|+=|Ajouter|
|&|and|&|BitwiseAnd|
|&=|Et =|&=|BitwiseAnd|
|&#124;|ou|&#124;|BitwiseOr|
|&#124;=|Ou =|&#124;=|BitwiseOr|
|--|N/A|--|Décrémentation|
|/|/|/|Diviser|
|/=|/=|/=|Diviser|
|==|=|==|Equals|
|^|Xor|^|Xor|
|^=|XOR =|^=|Xor|
|>|>|>|Comparer|
|>=|>=|>=|Comparer|
|++|N/A|++|Incrément|
|<>|!=|Equals|
|<<|<<|<<|Maj|
|<<=|<<=|<<=|Maj|
|<|<|<|Comparer|
|<=|<=|\<=|Comparer|
|&&|N/A|&&|LogicalAnd|
|&#124;&#124;|N/A|&#124;&#124;|Logique|
|!|N/A|!|LogicalNot|
|%|Mod|%|Modulo ou modulo|
|%=|N/A|%=|Mod|
|* (binaire)|*|*|Multiplier|
|*=|N/A|*=|Multiplier|
|~|Not|~|OnesComplement|
|>>|>>|>>|Maj droite|
=|N/A|>>=|Maj droite|
|-(binaire)|-(binaire)|-(binaire)|Soustraire|
|-=|N/A|-=|Soustraire|
|true|IsTrue|N/A|IsTrue (propriété)|
| - (unaire)   |N/A|-|Negate|
|+ (unaire)|N/A|+|Plus|
|false|IsFalse|Faux|IsTrue (propriété)|

 N/A = = ne peut pas être surchargé dans la langue sélectionnée.

 La règle vérifie également les opérateurs de cast implicite et explicite dans un type ( `SomeType` ) en vérifiant les méthodes nommées `ToSomeType` et `FromSomeType` .

 En C#, lorsqu’un opérateur binaire est surchargé, l’opérateur d’assignation correspondant, le cas échéant, est également implicitement surchargé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, implémentez l’autre méthode pour l’opérateur. Nommez-le à l’aide du nom de remplacement recommandé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle si vous implémentez une bibliothèque partagée. Les applications peuvent ignorer un avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant définit une structure qui enfreint cette règle. Pour corriger l’exemple, ajoutez une `Add(int x, int y)` méthode publique à la structure.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorOverloadsHaveNamedAlternates/cs/FxCop.Usage.OperatorOverloadsHaveNamedAlternates.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA1046 : Ne pas surcharger l'opérateur égal à sur les types référence](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226 : Les opérateurs doivent contenir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224 : Remplacez Equals au moment de surcharger l'opérateur égal](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218 : Remplacez GetHashCode au moment de remplacer Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
