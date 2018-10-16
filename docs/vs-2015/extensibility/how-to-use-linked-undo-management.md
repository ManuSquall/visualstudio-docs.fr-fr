---
title: 'Comment : utiliser la gestion d’annulation liée | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ce5cb31e2ac3d7014dec30e71a1dc08b122a330
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229123"
---
# <a name="how-to-use-linked-undo-management"></a>Comment : utiliser la gestion d’annulation liée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Annulation liée permet à l’utilisateur d’annuler simultanément les mêmes modifications dans plusieurs fichiers. Par exemple, les modifications de texte simultanées dans plusieurs fichiers de programme, par exemple un fichier d’en-tête et un fichier Visual C++, est une transaction d’annulation liée. Fonctionnalité d’annulation liée est intégrée à l’implémentation de l’environnement du Gestionnaire d’annulation, et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> vous permet de manipuler cette fonctionnalité. Annulation liée est implémentée par une unité d’annulation parent capable de relier les piles d’annulation distinct pour être traité comme une seule unité d’annulation. La procédure d’utilisation d’annulation liée est détaillée dans la section suivante.  
  
### <a name="to-use-linked-undo"></a>Pour utiliser l’annulation liée  
  
1.  Appelez `QueryService` sur `SVsLinkedUndoManager` pour obtenir un pointeur vers `IVsLinkedUndoTransactionManager`.  
  
2.  Créer l’unité d’annulation liée parent initiale en appelant <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Cela définit le point de départ pour un ensemble de piles d’annulation à être regroupées dans les piles d’annulation liée. Dans la `OpenLinkedUndo` méthode, vous devrez également spécifier si vous souhaitez que l’annulation liée à être strict ou non strict. Opération d’annulation liée non strict signifie que certaines des documents avec les frères d’annulation liée peuvent fermer et toujours laisser l’autre liée Annuler frères sur leurs piles. Comportement d’annulation liée stricte Spécifie que toutes les piles d’annulation frères doivent être annulées ensemble ou pas du tout. Ajouter des piles d’annulations liées suivantes en appelant [IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135) (méthode).  
  
3.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> pour restaurer toutes les unités d’annulation liée en tant qu’une sauvegarde.  
  
    > [!NOTE]
    >  Pour implémenter la gestion d’annulation lié dans un éditeur, ajoutez la gestion d’annulation. Pour plus d’informations sur l’implémentation de la gestion d’annulation liée, consultez [Comment : implémenter Annuler gestion](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Guide pratique pour implémenter la gestion des opérations d’annulation](../extensibility/how-to-implement-undo-management.md)

