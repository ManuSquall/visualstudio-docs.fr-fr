---
title: 'CA1000 : ne pas déclarer de membres statiques sur des types génériques | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 66bca5b8b039de59509cecf4ecfae6bd6b4f0162
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548328"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000 : Ne pas déclarer de membres statiques sur les types génériques
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|
|CheckId|CA1000|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type générique visible de l’extérieur contient `static` un `Shared` membre (dans Visual Basic).

## <a name="rule-description"></a>Description de la règle
 Lorsqu’un `static` membre d’un type générique est appelé, l’argument de type doit être spécifié pour le type. Lorsqu'un membre d'instance générique qui ne prend pas en charge l'inférence est appelé, l'argument de type doit être spécifié pour le membre. La syntaxe permettant de spécifier l’argument de type dans ces deux cas est différente et facilement confondue, comme le montrent les appels suivants :

```vb
' Shared method in a generic type.
GenericType(Of Integer).SharedMethod()

' Generic instance method that does not support inference.
someObject.GenericMethod(Of Integer)()
```

```csharp
// Static method in a generic type.
GenericType<int>.StaticMethod();

// Generic instance method that does not support inference.
someObject.GenericMethod<int>();
```

 En règle générale, les deux déclarations précédentes doivent être évitées afin qu’il ne soit pas nécessaire de spécifier l’argument de type lorsque le membre est appelé. Cela aboutit à une syntaxe pour appeler des membres dans des génériques qui n’est pas différent de la syntaxe pour les non génériques. Pour plus d’informations, consultez [CA1004 : les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md).

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez le membre statique ou remplacez-le par un membre d’instance.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. La fourniture de génériques dans une syntaxe facile à comprendre et à utiliser réduit le temps nécessaire à l’apprentissage et à l’augmentation du taux d’adoption de nouvelles bibliothèques.

## <a name="related-rules"></a>Règles associées
 [CA1005 : Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010 : Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1002 : Ne pas exposer de listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003 : Utiliser les instances du gestionnaire d'événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007 : Utiliser des classes génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Voir aussi
 [Génériques](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
