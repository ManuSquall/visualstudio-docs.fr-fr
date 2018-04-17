---
title: 'CA1012 : Les types abstraits ne doivent pas avoir de constructeurs | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b10d41b9671b3f25aea6722835d709b24ab9b12
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012 : Les types abstraits ne doivent pas avoir de constructeurs
|||  
|-|-|  
|TypeName|AbstractTypesShouldNotHaveConstructors|  
|CheckId|CA1012|  
|Category|Microsoft.Design|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type public est abstrait et possède un constructeur public.  
  
## <a name="rule-description"></a>Description de la règle  
 Les constructeurs des types abstraits peuvent être appelés uniquement par des types dérivés. Étant donné que les constructeurs publics créent des instances d'un type et que vous ne pouvez pas créer d'instance d'un type abstrait, un type abstrait doté d'un constructeur public est de conception incorrecte.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, rendez le constructeur protégé, ou bien ne pas déclarer le type comme abstract.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. Le type abstrait a un constructeur public.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant contient un type abstrait qui enfreint cette règle.  
  
 [!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
 [!code-csharp[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant résout la violation précédente en modifiant l’accessibilité du constructeur à partir de `public` à `protected`.  
  
 [!code-csharp[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]