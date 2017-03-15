---
title: "Comment : mettre &#224; jour la barre d&#39;&#233;tat | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - mettre à jour la barre d'état"
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Comment : mettre &#224; jour la barre d&#39;&#233;tat
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**barre d'état** est une barre de contrôles située dans la partie inférieure de plusieurs fenêtres d'application qui contient une ou plusieurs lignes de texte ou indicateurs d'état.  
  
### pour mettre à jour la barre d'état  
  
1.  Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> sur chaque objet de vue individuelle \(DocView\) que votre éditeur le fournit, tel qu'un mode formulaire et un mode Code.  
  
2.  Lorsque l'IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, mettez à jour les informations dans **barre d'état** en appelant les méthodes d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.  
  
    > [!NOTE]
    >  L'IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> uniquement lorsque votre fenêtre de document est initialement activée.  Dans le reste du temps que la fenêtre de document actif, vous devez mettre à jour les informations de **barre d'état** lorsque l'état de votre éditeur change.  
  
## Programmation fiable  
 **barre d'état** contient quatre champs séparés :  
  
-   Texte d'état  
  
-   Progress Bar  
  
-   icône animée  
  
-   les informations d'éditeur  
  
 Pour plus d'informations, consultez [Barres d'état](/visual-cpp/mfc/status-bars).  
  
 L'IDE appelle automatiquement la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> de votre implémentation d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> lorsque votre fenêtre de document est activée.  
  
 L'implémenteur d'un VSPackage est responsable de la mise à jour le texte d'état dans la barre d'état.  L'IDE réinitialise cette chaîne à " prêt " si le champ de texte d'état est défini pour purger le texte \(""\) à la durée d'inactivité.  
  
## Voir aussi  
 [Barres d'état](/visual-cpp/mfc/status-bars)