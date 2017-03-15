---
title: "CA2215 : Les m&#233;thodes Dispose doivent appeler la fonction Dispose de la classe de base | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2215"
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "Dispose methods should call base class dispose"
helpviewer_keywords: 
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "CA2215"
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2215 : Les m&#233;thodes Dispose doivent appeler la fonction Dispose de la classe de base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposeMethodsShouldCallBaseClassDispose|  
|CheckId|CA2215|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type qui implémente <xref:System.IDisposable?displayProperty=fullName> hérite d'un type qui implémente également <xref:System.IDisposable>.  La méthode <xref:System.IDisposable.Dispose%2A> du type héritant n'appelle pas la méthode <xref:System.IDisposable.Dispose%2A> du type parent.  
  
## Description de la règle  
 Si un type hérite d'un type pouvant être supprimé, il doit appeler la méthode <xref:System.IDisposable.Dispose%2A> du type de base issu de sa propre méthode <xref:System.IDisposable.Dispose%2A>.  L'appel de la méthode de type de base Dispose garantit que toutes ressources créées par le type de base sont diffusées.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, appelez `base`.<xref:System.IDisposable.Dispose%2A> dans votre méthode <xref:System.IDisposable.Dispose%2A>.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si l'appel à `base`.<xref:System.IDisposable.Dispose%2A> se produit à un niveau d'appel subordonné à celui que la règle contrôle.  
  
## Exemple  
 L'exemple suivant présente un type `TypeA` qui implémente <xref:System.IDisposable>.  
  
 [!CODE [FxCop.Usage.IDisposablePattern#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern#1)]  
  
## Exemple  
 L'exemple suivant présente un type `TypeB` qui hérite du type `TypeA` et appelle correctement sa méthode <xref:System.IDisposable.Dispose%2A>.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_1.vb)]  
  
## Voir aussi  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Modèle de suppression](../Topic/Dispose%20Pattern.md)