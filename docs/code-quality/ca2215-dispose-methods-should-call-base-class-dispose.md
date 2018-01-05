---
title: "CA2215 : Les méthodes Dispose doivent appeler dispose de la classe de base | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 791de4f70113df3759e920591ec94da5108eec9a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215 : Les méthodes Dispose doivent appeler la fonction Dispose de la classe de base
|||  
|-|-|  
|TypeName|DisposeMethodsShouldCallBaseClassDispose|  
|CheckId|CA2215|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type qui implémente <xref:System.IDisposable?displayProperty=fullName> hérite d’un type qui implémente également <xref:System.IDisposable>. Le <xref:System.IDisposable.Dispose%2A> méthode du type héritant n’appelle pas la <xref:System.IDisposable.Dispose%2A> méthode du type parent.  
  
## <a name="rule-description"></a>Description de la règle  
 Si un type hérite d’un type pouvant être supprimé, il doit appeler la <xref:System.IDisposable.Dispose%2A> méthode du type de base à partir de son propre <xref:System.IDisposable.Dispose%2A> (méthode). Appel de la méthode de type de base Dispose garantit que toutes les ressources créées par le type de base sont libérées.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, appelez `base`.<xref:System.IDisposable.Dispose%2A> dans votre <xref:System.IDisposable.Dispose%2A> (méthode).  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle si l’appel à `base`.<xref:System.IDisposable.Dispose%2A> se produit à un niveau d’appel inférieur à la règle de contrôle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type `TypeA` qui implémente <xref:System.IDisposable>.  
  
 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type `TypeB` qui hérite du type `TypeA` et appelle son <xref:System.IDisposable.Dispose%2A> (méthode).  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)