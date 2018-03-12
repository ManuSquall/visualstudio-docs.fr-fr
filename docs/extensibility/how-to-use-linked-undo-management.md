---
title: "Comment : utiliser la gestion de l’opération d’annulation liée | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7a025cdfc14eb39dad7ea2bc72a69f1f260fb583
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-linked-undo-management"></a>Comment : utiliser la gestion de l’opération d’annulation liée
Opération d’annulation liée permet à l’utilisateur à annuler simultanément les mêmes modifications dans plusieurs fichiers. Par exemple, les modifications de texte simultanées dans plusieurs fichiers de programme, par exemple un fichier d’en-tête et un fichier Visual C++, est une transaction d’annulation liée. Capacité de l’opération d’annulation liée est intégrée à la mise en œuvre de l’environnement du Gestionnaire d’annulation, et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> vous permet de manipuler cette fonctionnalité. Opération d’annulation liée est implémentée par une unité undo parent que vous pouvez lier les piles d’annulation pour être traité comme une seule unité d’annulation. La procédure d’utilisation d’annulation liée est détaillée dans la section suivante.  
  
### <a name="to-use-linked-undo"></a>Pour utiliser l’opération d’annulation liée  
  
1.  Appelez `QueryService` sur `SVsLinkedUndoManager` pour obtenir un pointeur vers `IVsLinkedUndoTransactionManager`.  
  
2.  Créer l’unité d’annulation liée initiale parent en appelant <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Cela définit le point de départ pour un ensemble de piles d’annulation d’être regroupés en les piles d’annulation liée. Dans la `OpenLinkedUndo` méthode, vous devez également spécifier si vous souhaitez que l’opération d’annulation liée stricte ou non strict. Opération d’annulation liée non strict signifie que certains documents avec frères d’annulation liée peuvent fermer et toujours laisser l’autre liée Annuler frères sur leurs piles. Comportement d’annulation liée stricte Spécifie que toutes les piles d’annulation frères doivent être annulées ensemble ou pas du tout. Ajoutez ensuite lié annule piles en appelant [IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135) (méthode).  
  
3.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> pour restaurer toutes les unités d’annulation liée en tant qu’une sauvegarde.  
  
    > [!NOTE]
    >  Pour implémenter la gestion de l’opération d’annulation liée dans un éditeur, ajouter la gestion de l’annulation. Pour plus d’informations sur l’implémentation de la gestion de l’opération d’annulation liée, consultez [Comment : gestion d’annuler implémenter](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Comment : implémenter la gestion de l’annulation](../extensibility/how-to-implement-undo-management.md)