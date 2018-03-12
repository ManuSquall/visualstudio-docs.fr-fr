---
title: "CA2231 : Surchargez l’opérateur equals en remplaçant ValueType.Equals | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9ee207eb3e5c4babb5bcb9f7d88f9afd3908a3c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231 : Surchargez l'opérateur égal (equals) en remplaçant ValueType.Equals
|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|  
|CheckId|CA2231|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type valeur se substitue <xref:System.Object.Equals%2A?displayProperty=fullName> mais n’implémente ne pas l’opérateur d’égalité.  
  
## <a name="rule-description"></a>Description de la règle  
 Dans la plupart des langages de programmation il n’existe aucune implémentation par défaut de l’opérateur d’égalité (==) pour les types valeur. Si votre langage de programmation prend en charge les surcharges d’opérateur, vous devez envisager d’implémenter l’opérateur d’égalité. Son comportement doit être identique à celui de <xref:System.Object.Equals%2A>.  
  
 Vous ne pouvez pas utiliser l’opérateur d’égalité par défaut dans une implémentation surchargée de l’opérateur d’égalité. Cela provoque un dépassement de capacité de pile. Pour implémenter l’opérateur d’égalité, utilisez la méthode Object.Equals dans votre implémentation. Exemple :  
  
```vb  
If (Object.ReferenceEquals(left, Nothing)) Then  
    Return Object.ReferenceEquals(right, Nothing)  
Else  
    Return left.Equals(right)  
End If  
```  
  
```csharp  
if (Object.ReferenceEquals(left, null))   
    return Object.ReferenceEquals(right, null);  
return left.Equals(right);  
```  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, implémentez l’opérateur d’égalité.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle ; Toutefois, nous vous recommandons de fournir l’opérateur d’égalité si possible.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit un type qui viole cette règle.  
  
 [!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../code-quality/codesnippet/CSharp/ca2231-overload-operator-equals-on-overriding-valuetype-equals_1.cs)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1046 : Ne pas surcharger l’opérateur égal sur les types de référence](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225 : Les surcharges d’opérateur ont d’autres méthodes nommées](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226 : Les opérateurs doivent avoir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224 : Remplacez Equals lors de la surcharge de l’opérateur égal](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218 : Remplacez GetHashCode lors du remplacement de Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Object.Equals%2A?displayProperty=fullName>