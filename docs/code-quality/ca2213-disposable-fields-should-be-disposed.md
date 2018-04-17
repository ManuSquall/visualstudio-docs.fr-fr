---
title: 'CA2213 : Les champs supprimables doivent être supprimés | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 89f861db9c6e22492a8720a5890020cce26a4f43
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213 : Les champs pouvant être supprimés doivent l'être
|||  
|-|-|  
|TypeName|DisposableFieldsShouldBeDisposed|  
|CheckId|CA2213|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type qui implémente <xref:System.IDisposable?displayProperty=fullName> déclare des champs qui sont des types qui implémentent également <xref:System.IDisposable>. Le <xref:System.IDisposable.Dispose%2A> méthode du champ n’est pas appelée par le <xref:System.IDisposable.Dispose%2A> méthode du type déclarant.  
  
## <a name="rule-description"></a>Description de la règle  
 Un type est chargé de suppression de toutes ses ressources non managées ; Cela est accompli en implémentant <xref:System.IDisposable>. Cette règle vérifie si un type supprimable `T` déclare un champ `F` qui est une instance d’un type supprimable `FT`. Pour chaque champ `F`, la règle essaie de localiser un appel à `FT.Dispose`. La règle recherche les méthodes appelées par `T.Dispose`et un niveau inférieur (les méthodes appelées par les méthodes appelées par `FT.Dispose`).  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, appelez <xref:System.IDisposable.Dispose%2A> sur les champs qui sont des types qui implémentent <xref:System.IDisposable> si vous êtes chargé d’allouer et libérer les ressources non managées détenues par le champ.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle si vous n’êtes pas responsable pour libérer la ressource détenue par le champ, ou si l’appel à <xref:System.IDisposable.Dispose%2A> se produit à un niveau d’appel inférieur à la règle de contrôle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type `TypeA` qui implémente <xref:System.IDisposable> (`FT` dans l’examen précédent).  
  
 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type `TypeB` qui enfreint cette règle en déclarant un champ `aFieldOfADisposableType` (`F` dans la discussion précédente) comme un type (`TypeA`) sans appeler <xref:System.IDisposable.Dispose%2A> sur le champ. `TypeB` correspond à `T` dans la discussion précédente.  
  
 [!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)