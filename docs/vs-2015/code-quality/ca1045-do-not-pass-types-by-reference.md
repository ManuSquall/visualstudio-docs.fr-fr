---
title: 'CA1045 : ne pas passer de types par référence | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dad2f90a51a4247a4c111ef51e85a28ba1a118ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548471"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045 : Ne pas passer de types par référence
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode publique ou protégée dans un type public a un `ref` paramètre qui accepte un type primitif, un type référence ou un type valeur qui ne fait pas partie des types intégrés.

## <a name="rule-description"></a>Description de la règle
 Passer des types par référence (à l’aide `out` de ou `ref` ) requiert une expérience avec les pointeurs, en comprenant les différences entre les types valeur et les types référence, ainsi que la gestion des méthodes qui ont plusieurs valeurs de retour. En outre, la différence entre les `out` `ref` paramètres et n’est pas largement comprise.

 Quand un type référence est passé par référence, la méthode envisage d’utiliser le paramètre pour retourner une instance différente de l’objet. (Le passage d’un type référence par référence est également appelé utilisation d’un pointeur double, d’un pointeur vers un pointeur ou d’une double indirection.) À l’aide de la Convention d’appel par défaut, qui passe « par valeur », un paramètre qui prend un type référence reçoit déjà un pointeur vers l’objet. Le pointeur, pas l’objet vers lequel il pointe, est passé par valeur. Le passage par valeur signifie que la méthode ne peut pas modifier le pointeur pour qu’il pointe vers une nouvelle instance du type référence, mais puisse modifier le contenu de l’objet vers lequel il pointe. Pour la plupart des applications, cela suffit et génère le comportement souhaité.

 Si une méthode doit retourner une instance différente, utilisez la valeur de retour de la méthode pour y parvenir. Consultez la <xref:System.String?displayProperty=fullName> classe pour une variété de méthodes qui opèrent sur des chaînes et retournent une nouvelle instance d’une chaîne. En utilisant ce modèle, il est laissé à l’appelant de décider si l’objet d’origine est conservé.

 Bien que les valeurs de retour soient courantes et largement utilisées, l’application correcte des `out` paramètres et requiert des compétences en matière de `ref` conception et de codage intermédiaires. Les architectes de bibliothèque qui sont en train de concevoir pour un public général ne doivent pas s’attendre à ce que les utilisateurs maîtrisent le travail avec les `out` `ref` paramètres ou.

> [!NOTE]
> Lorsque vous utilisez des paramètres qui sont de grandes structures, les ressources supplémentaires requises pour copier ces structures peuvent entraîner un effet sur les performances lorsque vous transmettez par valeur. Dans ce cas, vous pouvez envisager d’utiliser des `ref` `out` paramètres ou.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle qui est provoquée par un type valeur, utilisez la méthode pour retourner l’objet comme valeur de retour. Si la méthode doit retourner plusieurs valeurs, remaniez-la pour retourner une seule instance d’un objet qui contient les valeurs.

 Pour corriger une violation de cette règle qui est provoquée par un type référence, assurez-vous que le comportement que vous souhaitez est de retourner une nouvelle instance de la référence. Si c’est le cas, la méthode doit utiliser sa valeur de retour pour effectuer cette opération.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle ; Toutefois, cette conception peut entraîner des problèmes d’utilisation.

## <a name="example"></a>Exemple
 La bibliothèque suivante montre deux implémentations d’une classe qui génère des réponses aux commentaires de l’utilisateur. La première implémentation ( `BadRefAndOut` ) force l’utilisateur de la bibliothèque à gérer trois valeurs de retour. La deuxième implémentation ( `RedesignedRefAndOut` ) simplifie l’expérience utilisateur en retournant une instance d’une classe de conteneur ( `ReplyData` ) qui gère les données en tant qu’unité unique.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Exemple
 L’application suivante illustre l’expérience de l’utilisateur. L’appel à la bibliothèque repensée ( `UseTheSimplifiedClass` méthode) est plus simple, et les informations retournées par la méthode sont facilement gérées. La sortie des deux méthodes est identique.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Exemple
 L’exemple de bibliothèque suivant illustre l' `ref` utilisation des paramètres pour les types de référence et montre une meilleure façon d’implémenter cette fonctionnalité.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Exemple
 L’application suivante appelle chaque méthode de la bibliothèque pour illustrer le comportement.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 Cet exemple produit la sortie suivante.

 **Changement du pointeur-passé par valeur :** 
 **12345** 
 **12345** 
 **Modification du pointeur-passé par référence :** 
 **12345** 
 **12345 abcde** 
 **Passage par valeur de retour :** 
 **12345 abcde**
## <a name="related-rules"></a>Règles associées
 [CA1021 : Éviter les paramètres out](../code-quality/ca1021-avoid-out-parameters.md)
