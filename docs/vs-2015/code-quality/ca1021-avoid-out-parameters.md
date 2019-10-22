---
title: 'CA1021 : Évitez les paramètres out | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ea5d943212122672b84376b9b3ddf5e72bb0e81f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661998"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021 : Éviter les paramètres out
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode publique ou protégée dans un type public a un paramètre `out`.

## <a name="rule-description"></a>Description de la règle
 Passer des types par référence (à l’aide de `out` ou `ref`) requiert une expérience avec les pointeurs, en comprenant la différence entre les types valeur et les types référence, et la gestion des méthodes avec plusieurs valeurs de retour. En outre, la différence entre les paramètres `out` et `ref` n’est pas largement comprise.

 Quand un type référence est passé par référence, la méthode envisage d’utiliser le paramètre pour retourner une instance différente de l’objet. Le passage d’un type référence par référence est également appelé utilisation d’un pointeur double, d’un pointeur vers un pointeur ou d’une double indirection. En utilisant la Convention d’appel par défaut, qui passe « par valeur », un paramètre qui prend un type référence reçoit déjà un pointeur vers l’objet. Le pointeur, pas l’objet vers lequel il pointe, est passé par valeur. Le passage par valeur signifie que la méthode ne peut pas modifier le pointeur pour qu’il pointe vers une nouvelle instance du type référence. Toutefois, il peut modifier le contenu de l’objet vers lequel il pointe. Pour la plupart des applications, cela suffit et génère le comportement souhaité.

 Si une méthode doit retourner une instance différente, utilisez la valeur de retour de la méthode pour y parvenir. Consultez la classe <xref:System.String?displayProperty=fullName> pour une variété de méthodes qui opèrent sur des chaînes et retournent une nouvelle instance d’une chaîne. Quand ce modèle est utilisé, l’appelant doit décider si l’objet d’origine est conservé.

 Bien que les valeurs de retour soient banales et largement utilisées, l’application correcte des paramètres `out` et `ref` nécessite des compétences en matière de conception et de codage intermédiaires. Les architectes de bibliothèque qui se contentent de concevoir pour un public général ne doivent pas s’attendre à ce que les utilisateurs maîtrisent le travail avec les paramètres `out` ou `ref`.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle qui est provoquée par un type valeur, utilisez la méthode pour retourner l’objet comme valeur de retour. Si la méthode doit retourner plusieurs valeurs, remaniez-la pour retourner une seule instance d’un objet qui contient les valeurs.

 Pour corriger une violation de cette règle qui est provoquée par un type référence, assurez-vous que le comportement souhaité est de retourner une nouvelle instance de la référence. Si c’est le cas, la méthode doit utiliser sa valeur de retour pour effectuer cette opération.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle. Toutefois, cette conception peut entraîner des problèmes d’utilisation.

## <a name="example"></a>Exemple
 La bibliothèque suivante montre deux implémentations d’une classe qui génère des réponses aux commentaires d’un utilisateur. La première implémentation (`BadRefAndOut`) force l’utilisateur de la bibliothèque à gérer trois valeurs de retour. La deuxième implémentation (`RedesignedRefAndOut`) simplifie l’expérience utilisateur en retournant une instance d’une classe de conteneur (`ReplyData`) qui gère les données en tant qu’unité unique.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Exemple
 L’application suivante illustre l’expérience de l’utilisateur. L’appel à la bibliothèque repensée (méthode `UseTheSimplifiedClass`) est plus simple, et les informations retournées par la méthode sont facilement gérées. La sortie des deux méthodes est identique.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Exemple
 L’exemple de bibliothèque suivant illustre la façon dont les paramètres `ref` pour les types référence sont utilisés et montre une meilleure façon d’implémenter cette fonctionnalité.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Exemple
 L’application suivante appelle chaque méthode de la bibliothèque pour illustrer le comportement.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 Cet exemple produit la sortie suivante.

 **Changement du pointeur-passé par valeur :** 
**12345** 
**12345** 
**modification du pointeur-passé par référence :** 
**12345** 
**12345 ABCD** 1**passant par la valeur de retour : **3**12345 abcde**
## <a name="try-pattern-methods"></a>Méthodes de modèle try

### <a name="description"></a>Description
 Les méthodes qui implémentent le modèle **Try \<Something >** , telles que <xref:System.Int32.TryParse%2A?displayProperty=fullName>, ne déclenchent pas cette violation. L’exemple suivant illustre une structure (type valeur) qui implémente la méthode <xref:System.Int32.TryParse%2A?displayProperty=fullName>.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.TryPattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TryPattern/cs/FxCop.Design.TryPattern.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA1045 : Ne pas passer de types par référence](../code-quality/ca1045-do-not-pass-types-by-reference.md)
