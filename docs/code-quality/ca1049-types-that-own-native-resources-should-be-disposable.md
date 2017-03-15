---
title: "CA1049&#160;: Les types qui poss&#232;dent des ressources natives doivent &#234;tre supprimables | Microsoft Docs"
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
  - "CA1049"
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
helpviewer_keywords: 
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
  - "CA1049"
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1049&#160;: Les types qui poss&#232;dent des ressources natives doivent &#234;tre supprimables
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|  
|CheckId|CA1049|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type référence un champ <xref:System.IntPtr?displayProperty=fullName>, <xref:System.UIntPtr?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>, mais n'implémente aucun <xref:System.IDisposable?displayProperty=fullName>.  
  
## Description de la règle  
 Cette règle suppose que les champs <xref:System.IntPtr>, <xref:System.UIntPtr> et <xref:System.Runtime.InteropServices.HandleRef> stockent des pointeurs vers des ressources non managées.  Les types qui allouent des ressources non managées doivent implémenter <xref:System.IDisposable> pour permettre aux appelants de libérer ces ressources à la demande et de raccourcir les durées de vie des objets qui les détiennent.  
  
 Le modèle de design recommandé pour nettoyer des ressources non managées consiste à fournir à la fois des moyens implicites et explicites de libérer ces ressources, respectivement à l'aide des méthodes <xref:System.Object.Finalize%2A?displayProperty=fullName> et <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>.  Le garbage collector appelle la méthode <xref:System.Object.Finalize%2A> d'un objet à un moment indéterminé, après que l'objet a été déterminé comme désormais inaccessible.  Après l'appel à <xref:System.Object.Finalize%2A>, une opération garbage collection supplémentaire est nécessaire pour libérer l'objet.  La méthode <xref:System.IDisposable.Dispose%2A> permet à l'appelant de libérer explicitement des ressources, et ce à la demande, avant le moment de leur libération si elles étaient laissées dans le garbage collector.  Après avoir nettoyé les ressources non managées, <xref:System.IDisposable.Dispose%2A> doit appeler la méthode <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> pour permettre au garbage collector de déterminer que <xref:System.Object.Finalize%2A> ne doit plus être appelée ; ce procédé élimine une opération garbage collection supplémentaire et raccourcit la durée de vie de l'objet.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, implémentez <xref:System.IDisposable>.  
  
## Quand supprimer les avertissements  
 ll est possible de supprimer sans risque un avertissement de cette règle dès lors que le type ne référence aucune ressource non managée.  Sinon, ne supprimez aucun avertissement de cette règle, parce que l'échec de l'implémentation de <xref:System.IDisposable> peut engendrer l'indisponibilité ou la sous\-utilisation de ressources non managées.  
  
## Exemple  
 L'exemple suivant présente un type qui implémente <xref:System.IDisposable> pour nettoyer une ressource non managée.  
  
 [!code-cs[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]  
  
## Règles connexes  
 [CA2115 : Appelez GC.KeepAlive lorsque vous utilisez des ressources natives](../Topic/CA2115:%20Call%20GC.KeepAlive%20when%20using%20native%20resources.md)  
  
 [CA1816 : Appeler GC.SuppressFinalize correctement](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA2216 : Les types pouvant être supprimés doivent déclarer un finaliseur](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA1001 : Les types qui possèdent des champs supprimables doivent être supprimables](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)  
  
## Voir aussi  
 [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md)   
 [Modèle de suppression](../Topic/Dispose%20Pattern.md)