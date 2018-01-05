---
title: "CA1000 : Ne déclarez pas de membres statiques sur les types génériques | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 11bef403ffedee1a22ba615ee1744a7e93f8c1b0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000 : Ne pas déclarer de membres statiques sur les types génériques
|||  
|-|-|  
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|  
|CheckId|CA1000|  
|Category|Microsoft.Design|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type générique visible de l’extérieur contient un `static` (`Shared` en Visual Basic) membre.  
  
## <a name="rule-description"></a>Description de la règle  
 Lorsqu’un `static` membre d’un type générique est appelé, l’argument de type doit être spécifié pour le type. Lorsqu'un membre d'instance générique qui ne prend pas en charge l'inférence est appelé, l'argument de type doit être spécifié pour le membre. La syntaxe pour spécifier l’argument de type dans ces deux cas est différente et peut être facilement confondue, comme les appels suivants montrent :  
  
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
  
 En règle générale, les deux déclarations précédentes doivent être évitées afin que l’argument de type ne devra pas être spécifié lorsque le membre est appelé. Cela entraîne une syntaxe pour appeler des membres dans les génériques n’est pas différente de la syntaxe de non génériques. Pour plus d’informations, consultez [CA1004 : les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md).  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez le membre statique ou remplacez-le par un membre d’instance.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. Fourniture de génériques dans une syntaxe facile à comprendre et à utiliser réduit le temps nécessaire pour en savoir plus et augmente le taux d’adoption de nouvelles bibliothèques.  
  
## <a name="related-rules"></a>Règles associées  
 [CA1005 : Évitez trop de paramètres sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010 : Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1002 : N’exposez pas de listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003 : Utiliser les instances du gestionnaire d’événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007 : Utiliser des méthodes génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Génériques](/dotnet/csharp/programming-guide/generics/index)