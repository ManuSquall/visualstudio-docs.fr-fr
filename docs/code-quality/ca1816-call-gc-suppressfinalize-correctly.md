---
title: "CA1816&#160;: Appeler GC.SuppressFinalize correctement | Microsoft Docs"
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
  - "CA1816"
  - "DisposeMethodsShouldCallSuppressFinalize"
helpviewer_keywords: 
  - "CA1816"
  - "DisposeMethodsShouldCallSuppressFinalize"
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1816&#160;: Appeler GC.SuppressFinalize correctement
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallGCSuppressFinalizeCorrectly|  
|CheckId|CA1816|  
|Catégorie|Microsoft.  Utilisation|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
  
-   Une méthode qui est une implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> n'appelle pas <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   Une méthode qui n'est pas une implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> appelle <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   Une méthode appelle <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> et passe une valeur différente de this \(Me en Visual Basic\).  
  
## Description de la règle  
 La méthode <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> permet aux utilisateurs de libérer des ressources n'importe quand avant que l'objet devienne disponible pour l'opération garbage collection.  Si la méthode <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> est appelée, elle libère les ressources de l'objet.  Cela rend la finalisation inutile.  <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> doit appeler <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> ainsi le garbage collector n'appelle pas le finaliseur de l'objet.  
  
 Pour éviter que les types dérivés avec finaliseurs ne doivent réimplémenter [System.IDisposable](assetId:///System.IDisposable?qualifyHint=True&autoUpgrade=False) et l'appeler, des types unsealed sans finaliseur doivent toujours appeler <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle :  
  
 Si la méthode est une implémentation de <xref:System.IDisposable.Dispose%2A>, ajoutez un appel à <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 Si la méthode n'est pas une implémentation de <xref:System.IDisposable.Dispose%2A>, supprimez l'appel à <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> ou déplacez\-le vers l'implémentation <xref:System.IDisposable.Dispose%2A> du type.  
  
 Modifiez tous les appels en<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> pour passer ceci \(Moi en Visual Basic\).  
  
## Quand supprimer les avertissements  
 Supprimez uniquement un avertissement de cette règle si vous utilisez délibérément <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> pour contrôler la durée de vie des autres objets.  Ne supprimez pas un avertissement de cette règle si une implémentation de <xref:System.IDisposable.Dispose%2A> n'appelle pas <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  Dans cette situation, ne pas parvenir à supprimer une finalisation fait baisser les performances et n'apporte aucun avantage.  
  
## Exemple  
 L'exemple suivant montre une méthode qui appelle <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> de manière incorrecte.  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
 [!code-cs[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]  
  
## Exemple  
 L'exemple suivant montre une méthode qui appelle <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> de manière correcte.  
  
 [!CODE [FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1)]  
  
## Règles connexes  
 [CA2215 : Les méthodes Dispose doivent appeler la fonction Dispose de la classe de base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA2216 : Les types pouvant être supprimés doivent déclarer un finaliseur](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
## Voir aussi  
 [Modèle de suppression](../Topic/Dispose%20Pattern.md)