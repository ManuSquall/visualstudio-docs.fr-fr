---
title: "CA1012&#160;: Les types abstraits ne doivent pas avoir de constructeurs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AbstractTypesShouldNotHaveConstructors"
  - "CA1012"
helpviewer_keywords: 
  - "CA1012"
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 25
---
# CA1012&#160;: Les types abstraits ne doivent pas avoir de constructeurs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AbstractTypesShouldNotHaveConstructors|  
|CheckId|CA1012|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type public est abstrait et présente un constructeur public.  
  
## Description de la règle  
 Les constructeurs des types abstraits peuvent être appelés uniquement par des types dérivés.  Étant donné que les constructeurs publics créent des instances d'un type et que vous ne pouvez pas créer d'instance d'un type abstrait, un type abstrait doté d'un constructeur public est de conception incorrecte.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, protégez le constructeur ou ne déclarez pas le type en tant qu'abstrait.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  Le type abstrait a un constructeur public.  
  
## Exemple  
 L'exemple suivant contient un type abstrait qui enfreint cette règle.  
  
 [!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
 [!code-cs[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]  
  
## Exemple  
 L'exemple suivant résout la violation précédente en modifiant l'accessibilité du constructeur de `public` en `protected`.  
  
 [!code-cs[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]