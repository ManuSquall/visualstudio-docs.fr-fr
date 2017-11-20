---
title: "CA1010 : Les Collections doivent implémenter une interface générique | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f0cefdb203011a24769b5b180a442d22a90d0b5c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010 : Les collections doivent implémenter une interface générique
|||  
|-|-|  
|TypeName|CollectionsShouldImplementGenericInterface|  
|CheckId|CA1010|  
|Catégorie|Microsoft.Design|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type visible de l’extérieur implémente la <xref:System.Collections.IEnumerable?displayProperty=fullName> interface mais n’implémente pas le <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interface et l’assembly conteneur cible [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]. Cette règle ignore les types qui implémentent <xref:System.Collections.IDictionary?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Description de la règle  
 Pour étendre la facilité d'utilisation d'une collection, implémentez l'une des interfaces de collection génériques. La collection peut ensuite être utilisée pour remplir des types de collections génériques tels que les éléments suivants :  
  
-   <xref:System.Collections.Generic.List%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, implémentez l’une des interfaces de collection génériques suivantes :  
  
-   <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.IList%601?displayProperty=fullName>  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle ; Toutefois, la collection aura une utilisation plus limitée.  
  
## <a name="example-violation"></a>Exemple de Violation  
  
### <a name="description"></a>Description  
 L’exemple suivant montre une classe qui dérive de la non générique (type référence) `CollectionBase` (classe), ce qui enfreint cette règle.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]  
  
### <a name="comments"></a>Commentaires  
 Pour corriger une violation de cette violation, vous devez implémenter les interfaces génériques ou modifier la classe de base en un type qui implémente déjà les interfaces génériques et non génériques, telles que la `Collection<T>` classe.  
  
## <a name="fix-by-base-class-change"></a>Résoudre par modification de la classe de Base  
  
### <a name="description"></a>Description  
 L’exemple suivant résout la violation en modifiant la classe de base de la collection non générique `CollectionBase` générique `Collection<T>` (`Collection(Of T)` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) classe.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]  
  
### <a name="comments"></a>Commentaires  
 Modification de la classe de base d’une classe déjà finale d’est considérée comme une modification avec rupture pour les utilisateurs existants.  
  
## <a name="fix-by-interface-implementation"></a>Résoudre par implémentation d’Interface  
  
### <a name="description"></a>Description  
 L’exemple suivant résout la violation en implémentant ces interfaces génériques : `IEnumerable<T>`, `ICollection<T>`, et `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)`, et `IList(Of T)` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1005 : Évitez trop de paramètres sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1000 : Ne déclarez pas de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002 : N’exposez pas de listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003 : Utiliser les instances du gestionnaire d’événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007 : Utiliser des méthodes génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Génériques](/dotnet/csharp/programming-guide/generics/index)