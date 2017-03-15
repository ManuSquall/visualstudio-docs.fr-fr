---
title: "Comment&#160;: utiliser la r&#233;gion d’animation de la barre d’&#233;tat | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "barre d’état, programmer"
  - "barre d’état, région d’animation"
  - "région d’animation, barre d’état"
ms.assetid: ec6fb915-7bc8-4a90-8156-70c1a243caff
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# Comment&#160;: utiliser la r&#233;gion d’animation de la barre d’&#233;tat
La région d'animation de la barre d'état de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] affiche une animation en boucle qui indique une longue opération ou une opération de longueur indéterminée \(par exemple, la création de plusieurs projets dans une solution\).  
  
### pour utiliser la région d'animation de la barre d'état de Visual Studio  
  
1.  Obtenez une instance de l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> , qui sont disponibles via le service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> .  
  
2.  Démarrez l'animation en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Animation%2A> de barre d'état.  Passez 1 comme valeur du premier paramètre, et une référence à une icône animée comme valeur du deuxième paramètre.  
  
3.  Arrêtez l'animation en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Animation%2A> de barre d'état.  Passez 0 comme valeur du premier paramètre, et une référence à l'icône animée comme valeur du deuxième paramètre.  
  
## Exemple  
 Cet exemple montre comment effectuer une animation intégrée dans une région d'animation.  
  
 [!code-cs[VSSDKAnimationStatusBar#1](../misc/codesnippet/CSharp/how-to-use-the-animation-region-of-the-status-bar_1.cs)]
 [!code-vb[VSSDKAnimationStatusBar#1](../misc/codesnippet/VisualBasic/how-to-use-the-animation-region-of-the-status-bar_1.vb)]  
  
## Voir aussi  
 [Extension de la barre d'état](../extensibility/extending-the-status-bar.md)   
 [Comment : lire et écrire dans la zone de commentaires de la barre d’état](../misc/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar.md)   
 [Procédure : programmation de la région de barre de progression de la barre d’état](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [Procédure : programmation de la zone du concepteur de la barre d’état](../Topic/How%20to:%20Program%20the%20Designer%20Region%20of%20the%20Status%20Bar.md)