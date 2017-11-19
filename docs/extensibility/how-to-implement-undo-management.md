---
title: "Comment : implémenter la gestion des annulations | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f61ee4c561e32f17afa1b53cbf3bd3bf982feeb4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-implement-undo-management"></a>Comment : implémenter la gestion de l’annulation
L’interface principale utilisée pour la gestion de l’annulation est <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, qui est implémentée par l’environnement. Pour prendre en charge la gestion de l’annulation, implémentez des unités d’annulation (autrement dit, <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, qui peut contenir plusieurs étapes individuelles.  
  
 La procédure d’implémentation de gestion de l’annulation dépend de si votre éditeur prend en charge plusieurs vues ou non. Les procédures pour chaque implémentation sont détaillées dans les sections suivantes.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Cas où un éditeur prend en charge une seule vue  
 Dans ce scénario, l’éditeur ne prend pas en charge plusieurs vues. Il y a qu’un seul éditeur et un document, et ils prennent en charge d’annulation. Utilisez la procédure suivante pour implémenter la gestion de l’annulation.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Pour prendre en charge la gestion de l’annulation pour un éditeur de vue unique  
  
1.  Appelez `QueryInterface` sur la `IServiceProvider` interface sur le frame de fenêtre pour `IOleUndoManager`, à partir de l’objet de vue de document pour accéder au gestionnaire d’annulation (`IID_IOLEUndoManager`).  
  
2.  Lorsqu’une vue est placée dans un frame de fenêtre, elle obtient un pointeur de site, qu’elle peut utiliser pour appeler `QueryInterface` pour `IServiceProvider`.  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Cas où un éditeur prend en charge plusieurs vues  
 Si vous avez une séparation de document et la vue, il est de gestionnaire d’annulation normalement un associée au document lui-même. Toutes les unités d’annulation sont placées dans le Gestionnaire d’une annulation associé à l’objet de données du document.  
  
 Au lieu de l’interrogation de l’affichage pour le Gestionnaire d’annulation, dont il en existe un pour chaque vue, les données du document de l’objet appelle <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> pour instancier le Gestionnaire d’annulation, en spécifiant un identificateur de classe de CLSID_OLEUndoManager. L’identificateur de classe est définie dans le fichier OCUNDOID.h.  
  
 Lorsque vous utilisez <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> pour créer votre propre instance de gestionnaire d’annulation, procédez comme suit pour connecter votre gestionnaire d’annulation dans l’environnement.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Pour connecter votre gestionnaire d’annulation dans l’environnement  
  
1.  Appelez `QueryInterface` sur l’objet retourné à partir de <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> pour `IID_IOleUndoManager`. Stocke le pointeur vers <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.  
  
2.  Appelez `QueryInterface` sur `IOleUndoManager` pour `IID_IOleCommandTarget`. Stocke le pointeur vers <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
3.  Relais votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> appelle stockées `IOleCommandTarget` interface pour les commandes StandardCommandSet97 suivantes :  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  Appelez `QueryInterface` sur `IOleUndoManager` pour `IID_IVsChangeTrackingUndoManager`. Stocke le pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.  
  
     Utiliser le pointeur pour <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> pour appeler le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>et le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> méthodes.  
  
5.  Appelez `QueryInterface` sur `IOleUndoManager` pour `IID_IVsLinkCapableUndoManager`.  
  
6.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> avec votre document, qui doit également implémenter le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> interface. Lors de la fermeture du document, appelez `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.  
  
7.  Lors de la fermeture du document, appelez `QueryInterface` sur votre gestionnaire d’annulation pour `IID_IVsLifetimeControlledObject`.  
  
8.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. Lorsque des modifications sont apportées au document, appelez <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> sur le gestionnaire avec un `OleUndoUnit` classe. Le <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> méthode conserve une référence à l’objet, vous la publiez généralement juste après le <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.  
  
 La `OleUndoManager` classe représente une instance de pile d’annulation unique. Par conséquent, il est un objet de gestionnaire d’annulation par entité de données suivie pour annuler ou rétablir.  
  
> [!NOTE]
>  Lors de l’objet de gestionnaire d’annulation est largement par l’éditeur de texte, il est un composant général qui ne dispose d’aucune prise en charge spécifique pour l’éditeur de texte. Si vous souhaitez prendre en charge plusieurs niveaux annuler ou rétablir, vous pouvez utiliser cet objet pour ce faire.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Comment : effacer la pile d’annulation](../extensibility/how-to-clear-the-undo-stack.md)