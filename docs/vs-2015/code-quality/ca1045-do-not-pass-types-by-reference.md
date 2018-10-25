---
title: 'CA1045 : Ne pas passer de types par référence | Microsoft Docs'
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
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1aa9077a0d27c105cd7008d550a4315ce8daf91a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836565"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045 : Ne pas passer de types par référence
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
>  Lorsque vous travaillez avec des paramètres qui sont des structures de grande taille, les ressources supplémentaires qui sont requises pour copier ces structures peut entraîner un effet sur les performances lorsque vous passez par valeur. Dans ce cas, vous pouvez envisager d’utiliser `ref` ou `out` paramètres.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle est dû à un type valeur, que la méthode retourne l’objet comme sa valeur de retour. Si la méthode doit retourner plusieurs valeurs, reconcevoir pour retourner une instance unique d’un objet qui contient les valeurs.

 Pour corriger une violation de cette règle est dû à un type référence, assurez-vous que le comportement voulu consiste à retourner une nouvelle instance de la référence. Dans le cas, la méthode doit utiliser sa valeur de retour pour ce faire.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle ; Toutefois, cette conception peut entraîner des problèmes d’utilisation.

## <a name="example"></a>Exemple
 La bibliothèque suivante présente deux implémentations d’une classe qui génère des réponses aux commentaires de l’utilisateur. La première implémentation (`BadRefAndOut`) oblige l’utilisateur de la bibliothèque à gérer trois valeurs de retour. La deuxième implémentation (`RedesignedRefAndOut`) simplifie l’expérience utilisateur en retournant une instance d’une classe de conteneur (`ReplyData`) qui gère les données comme une seule unité.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Exemple
 L’application suivante illustre l’expérience de l’utilisateur. L’appel à la bibliothèque repensée (`UseTheSimplifiedClass` méthode) est plus simple, et les informations qui sont retournées par la méthode sont facilement gérées. La sortie des deux méthodes est identique.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Exemple
 La bibliothèque de l’exemple suivant illustre comment `ref` paramètres pour les types référence sont utilisés et une manière plus efficace d’implémenter cette fonctionnalité.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Exemple
 L’application suivante appelle chaque méthode dans la bibliothèque afin d’illustrer le comportement.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 Cet exemple produit la sortie suivante.

 **Changing pointeur - passé par valeur :**
**12345**
**12345**
**Changing pointeur - passé par référence :** 
 ** 12345**
**ABCDE 12345**
**passage par valeur de retour :**
**ABCDE 12345**
## <a name="related-rules"></a>Règles associées
 [CA1021 : Évitez les paramètres out](../code-quality/ca1021-avoid-out-parameters.md)



