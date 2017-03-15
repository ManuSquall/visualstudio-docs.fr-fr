---
title: "Proc&#233;dure&#160;: programmation de la r&#233;gion de barre de progression de la barre d’&#233;tat | Microsoft Docs"
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
  - "Barre d’état, région de barre de progression"
  - "barre de progression, barre d’état"
  - "barre d’état, programmer"
ms.assetid: 4b54616a-8c20-436d-b764-f2380e5760f2
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# Proc&#233;dure&#160;: programmation de la r&#233;gion de barre de progression de la barre d’&#233;tat
La zone de barre de progression de la barre d'état de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] affiche la progression incrémentielle des opérations rapides, par exemple, l'enregistrement d'un fichier sur le disque.  
  
### Pour utiliser la progression défendez la zone de la barre d'état de Visual Studio  
  
1.  Obtenez une instance de l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> , qui sont disponibles via le service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> .  
  
2.  Initialisez la barre de progression à démarrer des valeurs en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> .  
  
3.  mettez à jour la barre de progression comme votre opération continue à l'aide de la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> à définir de nouvelles valeurs.  
  
## Exemple  
 cet exemple montre comment initialiser et mettre à jour la barre de progression.  
  
 [!code-cs[VSSDKProgressStatusBar#1](../misc/codesnippet/CSharp/how-to-program-the-progress-bar-region-of-the-status-bar_1.cs)]
 [!code-vb[VSSDKProgressStatusBar#1](../misc/codesnippet/VisualBasic/how-to-program-the-progress-bar-region-of-the-status-bar_1.vb)]  
  
 Dans l'exemple, le code :  
  
-   obtient une instance de l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> du service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> .  
  
-   Initialise la barre de progression aux valeurs de début données en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> .  
  
-   Simule une opération en itérant au sein d'une boucle d' `for` et en mettant à jour les valeurs de barre de progression à l'aide de la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> .  
  
-   Efface la barre de progression à l'aide de la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Clear%2A> .  
  
## Voir aussi  
 [Extension de la barre d'état](../extensibility/extending-the-status-bar.md)   
 [Comment : lire et écrire dans la zone de commentaires de la barre d’état](../misc/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar.md)   
 [Comment : utiliser la région d’animation de la barre d’état](../misc/how-to-use-the-animation-region-of-the-status-bar.md)   
 [Procédure : programmation de la zone du concepteur de la barre d’état](../Topic/How%20to:%20Program%20the%20Designer%20Region%20of%20the%20Status%20Bar.md)