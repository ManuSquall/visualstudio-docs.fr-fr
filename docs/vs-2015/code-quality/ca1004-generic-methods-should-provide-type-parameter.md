---
title: 'CA1004 : Les méthodes génériques doivent fournir un paramètre de type | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1004
- GenericMethodsShouldProvideTypeParameter
helpviewer_keywords:
- GenericMethodsShouldProvideTypeParameter
- CA1004
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bb32ab837ce7431f90c6a7ccdc178aa62b8145cf
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589583"
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004 : Les méthodes génériques doivent fournir un paramètre de type
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1004 : les méthodes génériques doivent fournir un paramètre de type](https://docs.microsoft.com/visualstudio/code-quality/ca1004-generic-methods-should-provide-type-parameter).

|||
|-|-|
|TypeName|GenericMethodsShouldProvideTypeParameter|
|CheckId|CA1004|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 La signature de paramètre d’une méthode générique extérieurement visible ne contient pas de types qui correspondent à tous les paramètres de type de la méthode.

## <a name="rule-description"></a>Description de la règle
 L’inférence désigne la manière dont l’argument de type d’une méthode générique est déterminé par le type d’argument passé à la méthode, au lieu d’utiliser la spécification explicite de l’argument de type. Pour activer l’inférence, la signature de paramètre d’une méthode générique doit contenir un paramètre du même type que le paramètre de type de la méthode. Dans ce cas, il n’est pas nécessaire de spécifier l’argument de type. Lorsque vous utilisez l’inférence pour tous les paramètres de type, la syntaxe d’appel des méthodes d’instance génériques et non génériques est identique. Cela simplifie l’utilisation des méthodes génériques.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez la conception afin que la signature de paramètre contienne le même type pour chaque paramètre de type de la méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Fourniture de génériques dans une syntaxe facile à comprendre et à utiliser réduit le temps qui est nécessaire pour en savoir plus et augmente la vitesse d’adoption de nouvelles bibliothèques.

## <a name="example"></a>Exemple
 L’exemple suivant montre la syntaxe d’appel des deux méthodes génériques. L’argument de type pour `InferredTypeArgument` est déduit et l’argument de type pour `NotInferredTypeArgument` doit être spécifié explicitement.

 [!code-csharp[FxCop.Design.Inference#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.Inference/cs/FxCop.Design.Inference.cs#1)]
 [!code-vb[FxCop.Design.Inference#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.Inference/vb/FxCop.Design.Inference.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1005 : Évitez trop de paramètres sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010 : Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000 : Ne déclarez pas de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002 : N’exposez pas de listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1003 : Utiliser les instances du gestionnaire d’événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007 : Utiliser des méthodes génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)