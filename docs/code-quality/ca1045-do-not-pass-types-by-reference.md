---
title: 'CA1045 : Ne pas passer de types par référence'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5174d00593b44d51b5628851039b1d0a37753c5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387496"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045 : Ne pas passer de types par référence

|||
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode publique ou protégée dans un type public a un `ref` paramètre qui accepte un type primitif, un type référence ou un type valeur qui ne fait pas partie des types intégrés.

## <a name="rule-description"></a>Description de la règle
 Passer des types par référence (à l’aide de `out` ou `ref`) nécessite une certaine expérience des pointeurs, de comprendre la différence entre les types valeur et types référence et la gestion des méthodes qui ont plusieurs valeurs de retour. En outre, la différence entre `out` et `ref` paramètres n’est pas généralement peu comprise.

 Lorsqu’un type référence est passé de « par référence », la méthode prévoit d’utiliser le paramètre pour retourner une autre instance de l’objet. (Passez un type référence par référence est également appelé à l’aide d’un pointeur double, pointeur vers un pointeur, ou une double indirection.) À l’aide de la valeur par défaut de convention d’appel, qui est de passer « par valeur », un paramètre qui accepte un type référence déjà reçoit un pointeur vers l’objet. Le pointeur, pas l’objet vers lequel il pointe, est passé par valeur. Le passage par valeur signifie que la méthode ne peut pas modifier le pointeur afin qu’il pointe vers une nouvelle instance de la référence de type, mais peut modifier le contenu de l’objet vers lequel il pointe. Pour la plupart des applications, cela est suffisant et débouche sur le comportement souhaité.

 Si une méthode doit retourner une instance différente, utilisez la valeur de retour de la méthode pour y parvenir. Consultez la <xref:System.String?displayProperty=fullName> classe pour un large éventail de méthodes qui opèrent sur des chaînes et retourner une nouvelle instance d’une chaîne. À l’aide de ce modèle, il incombe à l’appelant pour décider si l’objet d’origine est conservé.

 Bien que les valeurs de retour soient banales et très utilisées, l’application correcte de `out` et `ref` paramètres nécessite une conception intermédiaire et compétences de codage. Architectes de bibliothèque de conception destiné à une audience générale ne doit pas s’attendre aux utilisateurs de maîtrisent l’utilisation des `out` ou `ref` paramètres.

> [!NOTE]
> Lorsque vous travaillez avec des paramètres qui sont des structures de grande taille, les ressources supplémentaires qui sont requises pour copier ces structures peut entraîner un effet sur les performances lorsque vous passez par valeur. Dans ce cas, vous pouvez envisager d’utiliser `ref` ou `out` paramètres.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle est dû à un type valeur, que la méthode retourne l’objet comme sa valeur de retour. Si la méthode doit retourner plusieurs valeurs, reconcevoir pour retourner une instance unique d’un objet qui contient les valeurs.

 Pour corriger une violation de cette règle est dû à un type référence, assurez-vous que le comportement voulu consiste à retourner une nouvelle instance de la référence. Dans le cas, la méthode doit utiliser sa valeur de retour pour ce faire.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle ; Toutefois, cette conception peut entraîner des problèmes d’utilisation.

## <a name="example"></a>Exemple
 La bibliothèque suivante présente deux implémentations d’une classe qui génère des réponses aux commentaires de l’utilisateur. La première implémentation (`BadRefAndOut`) oblige l’utilisateur de la bibliothèque à gérer trois valeurs de retour. La deuxième implémentation (`RedesignedRefAndOut`) simplifie l’expérience utilisateur en retournant une instance d’une classe de conteneur (`ReplyData`) qui gère les données comme une seule unité.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]

## <a name="example"></a>Exemple
 L’application suivante illustre l’expérience de l’utilisateur. L’appel à la bibliothèque repensée (`UseTheSimplifiedClass` méthode) est plus simple, et les informations qui sont retournées par la méthode sont facilement gérées. La sortie des deux méthodes est identique.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]

## <a name="example"></a>Exemple
 La bibliothèque de l’exemple suivant illustre comment `ref` paramètres pour les types référence sont utilisés et une manière plus efficace d’implémenter cette fonctionnalité.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]

## <a name="example"></a>Exemple
 L’application suivante appelle chaque méthode dans la bibliothèque afin d’illustrer le comportement.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]

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

## <a name="related-rules"></a>Règles associées
 [CA1021 : Éviter les paramètres out](../code-quality/ca1021-avoid-out-parameters.md)