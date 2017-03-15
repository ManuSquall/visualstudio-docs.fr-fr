---
title: "Comment&#160;: lire et &#233;crire dans la zone de commentaires de la barre d’&#233;tat | Microsoft Docs"
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
  - "zone de commentaires, barre d’état"
  - "Barre d’état, zone de commentaires"
  - "Barre d’état, vue d’ensemble"
ms.assetid: e639561c-e1e7-4660-b2a2-8bca80f34a29
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Comment&#160;: lire et &#233;crire dans la zone de commentaires de la barre d’&#233;tat
La zone de commentaire de barre d'état de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] texte.  Vous pouvez définir et récupérer du texte, texte d'affichage statique, puis mettez en surbrillance le texte affiché.  
  
### Pour utiliser la zone de commentaire de la barre d'état de Visual Studio  
  
1.  Obtenez une instance de l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> , qui sont disponibles via le service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> .  
  
2.  Déterminez si la barre d'état est figé en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.IsFrozen%2A> d'instance d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> .  
  
3.  Définissez le texte de la zone de commentaire en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.SetText%2A> et en passant une chaîne de texte.  
  
4.  Lisez le texte de la zone de commentaire en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.GetText%2A> .  
  
## Exemple  
 Cet exemple montre comment écrire du texte à et lire le texte de la zone de commentaire.  
  
 [!code-cs[VSSDKFeedbackStatusBar#1](../misc/codesnippet/CSharp/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar_1.cs)]
 [!code-vb[VSSDKFeedbackStatusBar#1](../misc/codesnippet/VisualBasic/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar_1.vb)]  
  
 Dans l'exemple ci\-dessus, le code fait les choses suivantes :  
  
-   obtient une instance de l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> du service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> .  
  
-   Vérifie si la barre d'état est figé en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.IsFrozen%2A> .  
  
-   inhibe d'autres mises à jour à la barre d'état en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.FreezeOutput%2A> .  
  
-   lit le texte de la barre d'état en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.GetText%2A> et l'affiche dans un message.  
  
-   Permet de mettre à jour la barre d'état en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.FreezeOutput%2A> et en passant 0 dans le paramètre.  
  
-   Efface le contenu de la barre d'état en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Clear%2A> .  
  
## Voir aussi  
 [Extension de la barre d'état](../extensibility/extending-the-status-bar.md)   
 [Procédure : programmation de la région de barre de progression de la barre d’état](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [Comment : utiliser la région d’animation de la barre d’état](../misc/how-to-use-the-animation-region-of-the-status-bar.md)   
 [Procédure : programmation de la zone du concepteur de la barre d’état](../Topic/How%20to:%20Program%20the%20Designer%20Region%20of%20the%20Status%20Bar.md)