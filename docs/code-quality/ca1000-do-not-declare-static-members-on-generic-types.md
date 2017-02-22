---
title: "CA1000&#160;: Ne pas d&#233;clarer de membres statiques sur les types g&#233;n&#233;riques | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1000"
  - "DoNotDeclareStaticMembersOnGenericTypes"
helpviewer_keywords: 
  - "CA1000"
  - "DoNotDeclareStaticMembersOnGenericTypes"
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1000&#160;: Ne pas d&#233;clarer de membres statiques sur les types g&#233;n&#233;riques
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|  
|CheckId|CA1000|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type générique visible de l'extérieur contient un membre `static` \(`Shared` en Visual Basic\).  
  
## Description de la règle  
 Lorsqu'un membre `static` d'un type générique est appelé, l'argument de type doit être spécifié pour le type.  Lorsqu'un membre d'instance générique qui ne prend pas en charge l'inférence est appelé, l'argument de type doit être spécifié pour le membre.  La syntaxe permettant de spécifier l'argument de type dans ces deux cas est différente et peut être facilement confondue, comme l'illustrent les appels suivants :  
  
```vb  
' Shared method in a generic type.  
GenericType(Of Integer).SharedMethod()  
  
' Generic instance method that does not support inference.  
someObject.GenericMethod(Of Integer)()  
```  
  
```c#  
// Static method in a generic type.  
GenericType<int>.StaticMethod();  
  
// Generic instance method that does not support inference.  
someObject.GenericMethod<int>();  
```  
  
 En général, les deux déclarations précédentes doivent être évitées afin que l'argument de type ne soit pas spécifié lors de l'appel au membre.  On obtient une syntaxe d'appel aux membres pour les génériques qui est identique à celle pour les non\-génériques.  Pour plus d’informations, consultez [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md).  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez le membre statique ou remplacez\-le par un membre d'instance.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  La fourniture de génériques dans une syntaxe facile à comprendre et à utiliser réduit le délai d'apprentissage nécessaire et augmente le taux d'adoption de nouvelles bibliothèques.  
  
## Règles connexes  
 [CA1005 : Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010 : Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1002 : Ne pas exposer de listes génériques](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003 : Utiliser les instances du gestionnaire d'événements génériques](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007 : Utiliser des classes génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Voir aussi  
 [Génériques](/dotnet/csharp/programming-guide/generics/index)