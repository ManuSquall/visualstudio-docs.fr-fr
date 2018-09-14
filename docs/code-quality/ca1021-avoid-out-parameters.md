---
title: 'CA1021 : Éviter les paramètres out'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1082aaef3422923e0f74e8bd5eb242f3ae8e6023
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549493"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021 : Éviter les paramètres out

|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode publique ou protégée dans un type public a un `out` paramètre.

## <a name="rule-description"></a>Description de la règle
 Passer des types par référence (à l’aide de `out` ou `ref`) nécessite une certaine expérience des pointeurs, de comprendre la différence entre les types valeur et types référence et gestion de méthodes impliquant plusieurs valeurs de retour. En outre, la différence entre `out` et `ref` paramètres n’est pas généralement peu comprise.

 Lorsqu’un type référence est passé de « par référence », la méthode prévoit d’utiliser le paramètre pour retourner une autre instance de l’objet. Passage d’un type référence par référence est également appelé à l’aide d’un pointeur double, pointeur vers un pointeur, ou une double indirection. À l’aide de la valeur par défaut de convention d’appel, qui est de passer « par valeur », un paramètre qui accepte un type référence déjà reçoit un pointeur vers l’objet. Le pointeur, pas l’objet vers lequel il pointe, est passé par valeur. Passer par valeur signifie que la méthode ne peut pas modifier le pointeur afin qu’il pointe vers une nouvelle instance du type référence. Toutefois, il peut modifier le contenu de l’objet vers lequel il pointe. Pour la plupart des applications, cela est suffisant et débouche sur le comportement souhaité.

 Si une méthode doit retourner une instance différente, utilisez la valeur de retour de la méthode pour y parvenir. Consultez la <xref:System.String?displayProperty=fullName> classe pour un large éventail de méthodes qui opèrent sur des chaînes et retourner une nouvelle instance d’une chaîne. Lorsque ce modèle est utilisé, l’appelant doit décider si l’objet d’origine est conservé.

 Bien que les valeurs de retour soient banales et très utilisées, l’application correcte de `out` et `ref` paramètres nécessite une conception intermédiaire et compétences de codage. Architectes de bibliothèque de conception destiné à une audience générale ne doit pas s’attendre aux utilisateurs de maîtrisent l’utilisation des `out` ou `ref` paramètres.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle est dû à un type valeur, que la méthode retourne l’objet comme sa valeur de retour. Si la méthode doit retourner plusieurs valeurs, reconcevoir pour retourner une instance unique d’un objet qui contient les valeurs.

 Pour corriger une violation de cette règle est dû à un type référence, assurez-vous que le comportement souhaité doit retourner une nouvelle instance de la référence. Dans le cas, la méthode doit utiliser sa valeur de retour pour ce faire.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle. Toutefois, cette conception peut entraîner des problèmes d’utilisation.

## <a name="example"></a>Exemple
 La bibliothèque suivante présente deux implémentations d’une classe qui génère des réponses aux commentaires d’un utilisateur. La première implémentation (`BadRefAndOut`) oblige l’utilisateur de la bibliothèque à gérer trois valeurs de retour. La deuxième implémentation (`RedesignedRefAndOut`) simplifie l’expérience utilisateur en retournant une instance d’une classe de conteneur (`ReplyData`) qui gère les données comme une seule unité.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]

## <a name="example"></a>Exemple
 L’application suivante illustre l’expérience de l’utilisateur. L’appel à la bibliothèque repensée (`UseTheSimplifiedClass` méthode) est plus simple, et les informations retournées par la méthode sont facilement gérées. La sortie des deux méthodes est identique.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]

## <a name="example"></a>Exemple
 La bibliothèque de l’exemple suivant illustre comment `ref` paramètres pour les types référence sont utilisés et une manière plus efficace d’implémenter cette fonctionnalité.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]

## <a name="example"></a>Exemple
 L’application suivante appelle chaque méthode dans la bibliothèque afin d’illustrer le comportement.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]

Cet exemple génère la sortie suivante :

```txt
Changing pointer - passed by value:
12345
12345
Changing pointer - passed by reference:
12345
12345 ABCDE
Passing by return value:
12345 ABCDE
```

## <a name="try-pattern-methods"></a>Essayez les méthodes de modèle

### <a name="description"></a>Description
 Les méthodes qui implémentent le **essayez\<quelque chose >** modèle, tel que <xref:System.Int32.TryParse%2A?displayProperty=fullName>, ne déclenchent pas cette violation. L’exemple suivant montre une structure (type valeur) qui implémente le <xref:System.Int32.TryParse%2A?displayProperty=fullName> (méthode).

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]

## <a name="related-rules"></a>Règles associées
 [CA1045 : Ne pas passer de types par référence](../code-quality/ca1045-do-not-pass-types-by-reference.md)