---
title: "Comment : utiliser la gestion de l&#39;op&#233;ration d&#39;annulation li&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - gestion d'annulation liée"
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Comment : utiliser la gestion de l&#39;op&#233;ration d&#39;annulation li&#233;e
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La annulation liée permet à l'utilisateur d'annuler simultanément les mêmes modifications dans plusieurs fichiers.  Par exemple, le texte change simultanément sur plusieurs fichiers programme, tels qu'un fichier d'en\-tête et un fichier Visual C\+\+, est une transaction liée d'annulation.  La fonction liée d'annulation est générée dans l'implémentation de l'environnement du gestionnaire d'annulation, et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> vous permet de manipuler cette fonction.  La annulation liée est implémentée par une unité undo parent qui peut lier des piles d'annulations distinctes ensemble soit traitée comme une seule unité undo.  La procédure d'utilisation de l'annulation liée est détaillée dans la section suivante.  
  
### Pour utiliser l'annulation liée  
  
1.  Appelez `QueryService` sur `SVsLinkedUndoManager` pour obtenir un pointeur vers `IVsLinkedUndoTransactionManager`.  
  
2.  créez l'unité undo liée par parent initial par <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>appelant.  Cela définit le point de départ pour un ensemble de piles à annuler à regrouper dans la pile d'annulations liées.  Dans la méthode d' `OpenLinkedUndo` vous devez également spécifier si vous souhaitez que la annulation liée à être strict ou non\-strict.  le comportement lié Non\-strict d'annulation signifie que certains documents avec les frères liés d'annulation peuvent fermer et encore laisser les autres frères liés de annulation de leurs piles.  Une opération d'annulation liée stricte spécifie que toutes les piles de frères d'annulation liée doivent être annulées ensemble ou pas à tout.  Ajoutez les piles d'annulations liées suivantes en appelant la méthode d' [IOleUndoManager : : ajoutez](http://msdn.microsoft.com/library/windows/desktop/ms680135) .  
  
3.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> pour restaurer toutes les unités undo liées comme une.  
  
    > [!NOTE]
    >  Pour implémenter la gestion liée d'annulation dans un éditeur, ajoutez la gestion d'annulation.  Pour plus d'informations sur l'implémentation de la gestion liée d'annulation, consultez [Comment : Implémentez la gestion d'annulation](../extensibility/how-to-implement-undo-management.md).  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Comment : implémenter la gestion de l'annulation](../extensibility/how-to-implement-undo-management.md)