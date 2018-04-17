---
title: 'CA1815 : Remplacez equals et l’opérateur égal à sur les types valeur | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c4f5667977ed25da03d5d651e28c5ae3c3f4a3e0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815 : Remplacez Equals et l'opérateur égal à dans les types valeur
|||  
|-|-|  
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|  
|CheckId|CA1815|  
|Category|Microsoft.Performance|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type valeur public ne se substitue pas <xref:System.Object.Equals%2A?displayProperty=fullName>, ou n’implémente pas l’opérateur d’égalité (==). Cette règle ne vérifie pas les énumérations.  
  
## <a name="rule-description"></a>Description de la règle  
 Pour les types valeur, l’implémentation héritée de <xref:System.Object.Equals%2A> utilise la bibliothèque Reflection et compare le contenu de tous les champs. Le processus de réflexion sollicite fortement les ressources informatiques et la comparaison de chaque champ à la recherche d'une égalité peut s'avérer inutile. Si vous prévoyez que les utilisateurs à comparer ou trier des instances, ou les utilisez en tant que clés de table de hachage, votre type valeur doit implémenter <xref:System.Object.Equals%2A>. Si votre langage de programmation prend en charge la surcharge des opérateurs, vous devez également fournir une implémentation des opérateurs d’égalité et d’inégalité.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, fournissez une implémentation de <xref:System.Object.Equals%2A>. Si vous pouvez implémenter l’opérateur d’égalité.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle si les instances du type valeur ne seront pas comparées à l’autre sans.  
  
## <a name="example-of-a-violation"></a>Exemple de Violation  
  
### <a name="description"></a>Description  
 L’exemple suivant montre une structure (type valeur) qui enfreint cette règle.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]  
  
## <a name="example-of-how-to-fix"></a>Exemple de correctif  
  
### <a name="description"></a>Description  
 L’exemple suivant résout la violation précédente en substituant <xref:System.ValueType.Equals%2A?displayProperty=fullName> et en implémentant les opérateurs d’égalité (==, ! =).  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA2224 : Remplacez Equals lors de la surcharge de l’opérateur égal](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
 [CA2226 : Les opérateurs doivent avoir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Object.Equals%2A?displayProperty=fullName>