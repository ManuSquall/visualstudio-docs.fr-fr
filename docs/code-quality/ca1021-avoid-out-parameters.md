---
title: 'CA1021 : Éviter les paramètres out'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf9475ad208a229057700fa2965984fbdcb17abf
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923106"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021 : Éviter les paramètres out

|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Catégorie|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Une méthode publique ou protégée dans un type public a un `out` paramètre.

## <a name="rule-description"></a>Description de la règle
Passer des types par référence ( `out` à `ref`l’aide de ou) requiert une expérience avec les pointeurs, en comprenant les différences entre les types valeur et les types référence, ainsi que la gestion des méthodes avec plusieurs valeurs de retour. En outre, la différence `out` entre `ref` les paramètres et n’est pas largement comprise.

Quand un type référence est passé par référence, la méthode envisage d’utiliser le paramètre pour retourner une instance différente de l’objet. Le passage d’un type référence par référence est également appelé utilisation d’un pointeur double, d’un pointeur vers un pointeur ou d’une double indirection. En utilisant la Convention d’appel par défaut, qui passe «par valeur», un paramètre qui prend un type référence reçoit déjà un pointeur vers l’objet. Le pointeur, pas l’objet vers lequel il pointe, est passé par valeur. Le passage par valeur signifie que la méthode ne peut pas modifier le pointeur pour qu’il pointe vers une nouvelle instance du type référence. Toutefois, il peut modifier le contenu de l’objet vers lequel il pointe. Pour la plupart des applications, cela suffit et génère le comportement souhaité.

Si une méthode doit retourner une instance différente, utilisez la valeur de retour de la méthode pour y parvenir. Consultez la <xref:System.String?displayProperty=fullName> classe pour une variété de méthodes qui opèrent sur des chaînes et retournent une nouvelle instance d’une chaîne. Quand ce modèle est utilisé, l’appelant doit décider si l’objet d’origine est conservé.

Bien que les valeurs de retour soient courantes et largement utilisées, l' `out` application `ref` correcte des paramètres et requiert des compétences en matière de conception et de codage intermédiaires. Les architectes de bibliothèque qui sont en train de concevoir pour un public général ne doivent `out` pas `ref` s’attendre à ce que les utilisateurs maîtrisent le travail avec les paramètres ou.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle qui est provoquée par un type valeur, utilisez la méthode pour retourner l’objet comme valeur de retour. Si la méthode doit retourner plusieurs valeurs, remaniez-la pour retourner une seule instance d’un objet qui contient les valeurs.

Pour corriger une violation de cette règle qui est provoquée par un type référence, assurez-vous que le comportement souhaité est de retourner une nouvelle instance de la référence. Si c’est le cas, la méthode doit utiliser sa valeur de retour pour effectuer cette opération.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle. Toutefois, cette conception peut entraîner des problèmes d’utilisation.

## <a name="example"></a>Exemples
La bibliothèque suivante montre deux implémentations d’une classe qui génère des réponses aux commentaires d’un utilisateur. La première implémentation (`BadRefAndOut`) force l’utilisateur de la bibliothèque à gérer trois valeurs de retour. La deuxième implémentation (`RedesignedRefAndOut`) simplifie l’expérience utilisateur en retournant une instance d’une classe de`ReplyData`conteneur () qui gère les données en tant qu’unité unique.

[!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]

## <a name="example"></a>Exemple
L’application suivante illustre l’expérience de l’utilisateur. L’appel à la bibliothèque repensée (`UseTheSimplifiedClass` méthode) est plus simple, et les informations retournées par la méthode sont facilement gérées. La sortie des deux méthodes est identique.

[!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]

## <a name="example"></a>Exemple
L’exemple de bibliothèque suivant illustre la `ref` manière dont les paramètres des types de référence sont utilisés et montre une meilleure façon d’implémenter cette fonctionnalité.

[!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]

## <a name="example"></a>Exemples
L’application suivante appelle chaque méthode de la bibliothèque pour illustrer le comportement.

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

## <a name="try-pattern-methods"></a>Méthodes de modèle try

### <a name="description"></a>Description
Les méthodes qui implémentent le modèle **try\<>** , telles <xref:System.Int32.TryParse%2A?displayProperty=fullName>que, ne déclenchent pas cette violation. L’exemple suivant illustre une structure (type valeur) qui implémente la <xref:System.Int32.TryParse%2A?displayProperty=fullName> méthode.

### <a name="code"></a>Code
[!code-csharp[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]

## <a name="related-rules"></a>Règles associées
[CA1045 Ne pas passer de types par référence](../code-quality/ca1045-do-not-pass-types-by-reference.md)