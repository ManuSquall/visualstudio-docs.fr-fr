---
title: 'CA1005 : éviter les paramètres excessifs sur les types génériques | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 56c69badf76a05351b37a7c8a41a9cacf54f9974
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539722"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005 : Éviter les paramètres excessifs sur les types génériques
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause :
 Un type générique visible de l’extérieur a plus de deux paramètres de type.

## <a name="rule-description"></a>Description de la règle
 Plus un type générique contient de paramètres de type, plus il est difficile de déterminer et de mémoriser la représentation de chaque paramètre de type. Elle est généralement évidente avec un paramètre de type, comme dans `List<T>` , et dans certains cas, avec deux paramètres de type, comme dans `Dictionary<TKey, TValue>` . S’il existe plus de deux paramètres de type, la difficulté devient trop importante pour la plupart des utilisateurs (par exemple, `TooManyTypeParameters<T, K, V>` en C# ou `TooManyTypeParameters(Of T, K, V)` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez la conception de sorte qu’elle n’utilise pas plus de deux paramètres de type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle, sauf si la conception requiert absolument plus de deux paramètres de type. La fourniture de génériques dans une syntaxe facile à comprendre et à utiliser réduit le temps nécessaire à l’apprentissage et à l’augmentation du taux d’adoption de nouvelles bibliothèques.

## <a name="related-rules"></a>Règles associées
 [CA1010 : Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000 : Ne pas déclarer de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002 : Ne pas exposer de listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003 : Utiliser les instances du gestionnaire d'événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007 : Utiliser des classes génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Voir aussi
 [Génériques](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
