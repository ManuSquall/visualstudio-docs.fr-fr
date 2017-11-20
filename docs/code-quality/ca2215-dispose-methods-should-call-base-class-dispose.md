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
ms.openlocfilehash: 0659b9ec82353e3c658f1ba89f07fad197dd8670
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
 [Modèle de suppression](/dotnet/standard/design-guidelines/dispose-pattern)