---
title: "CA1046 : Ne pas surcharger l’opérateur égal sur les types référence | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 87c9b1ca85eb7edaf1050da96356640b06b66e0c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046 : Ne pas surcharger l'opérateur égal à sur les types référence
|||  
|-|-|  
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|  
|CheckId|CA1046|  
|Category|Microsoft.Design|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type public ou imbriqué référence publique surcharge l’opérateur d’égalité.  
  
## <a name="rule-description"></a>Description de la règle  
 Pour les types référence, l’implémentation par défaut de l’opérateur d’égalité est presque toujours correcte. Par défaut, deux références sont égales uniquement si elles pointent sur le même objet.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez l’implémentation de l’opérateur d’égalité.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle quand le type de référence se comporte comme un type valeur intégré. S’il est significatif pour effectuer une addition ou soustraction sur des instances du type, il est probablement correct implémenter l’opérateur d’égalité et de supprimer la violation.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre le comportement par défaut lors de la comparaison de deux références.  
  
 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’application suivante compare des références.  
  
 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]  
  
 Cet exemple produit la sortie suivante.  
  
 **un = nouveau (2,2) et b = nouveau (2,2) sont égaux ? No**  
**c et a sont égaux ? Oui**  
**b et a sont == ? No**  
**c et a sont == ? Oui**   
## <a name="related-rules"></a>Règles associées  
 [CA1013 : Surchargez l’opérateur égal lors de la surcharge de l’opérateur d’addition et de soustraction](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Opérateurs d’égalité](/dotnet/standard/design-guidelines/equality-operators)